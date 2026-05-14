---
layout: post
title: "AIDRA: putting AI ship-detection on a satellite-sized computer"
featured: true
---

## TL;DR

Earth-observation satellites take more pictures than they can send home. Most of those pictures are empty ocean. **AIDRA** is a SatCen project asking one question: *can we run a useful AI ship-detector on the kind of tiny computer that fits on a satellite, instead of waiting to downlink the data and process it on the ground?* What follows is my own small feasibility study around that same question.

The honest short answer, based on what I measured:

- **Yes, but it shrinks.** A standard YOLOv8 + CFAR vessel detector quantised to INT8 drops from **49.6 MB to 25.1 MB**, runs **~35% faster**, and keeps detection confidence virtually identical (53.6% vs 53.9%).
- **The payoff is huge if you can afford the squeeze.** On-board processing turns a Sentinel-1-style scene from a **27.9 GB downlink** into a few hundred contact reports — a **~1,900× compression ratio**, and the end-to-end "sensor → operator" latency drops by **5.3×**.
- **The hard part isn't the model. It's the paper trail.** EU procurement (and the AI Act) wants every detection to be reproducible, hash-traceable, and explainable. That's the part I spent most of my time on.

Everything below is live and auditable in a public Grafana at [aidra.uliber.com](https://aidra.uliber.com), and the code is on [GitHub](https://github.com/RadW2020/aidra-feasibility-study).

[![Vessel detections, Strait of Gibraltar]({{ site.baseurl }}/images/aidra/map-detections.png "Every green dot is an AI-detected vessel, weeks of Sentinel-1 SAR over the Strait of Gibraltar")]({{ site.baseurl }}/images/aidra/map-detections.png)

*Every green dot is a vessel AIDRA flagged on a Sentinel-1 SAR scene. Strait of Gibraltar, several weeks of acquisitions. This is what the question "can the satellite see ships?" looks like when you say yes.*

[![Vessel detection detail]({{ site.baseurl }}/images/aidra/detection.png "A single vessel detection, as seen by the YOLOv8 model on SAR imagery")]({{ site.baseurl }}/images/aidra/detection.png)

*A single vessel detection, as seen by the YOLOv8 model on SAR imagery. The 'detection' is a set of coordinates and a confidence score tied to a specific SAR chip.*

---

## Why this project exists

In early 2026 the **EU Satellite Centre (SatCen)** in Madrid published a tender — **SATCEN/2026/OP/0003** — asking for a feasibility study on running AI directly on-board Earth-observation satellites. The use case they care about is **maritime surveillance**: spotting vessels in SAR (radar) imagery without having to wait for the satellite to dump the full scene to a ground station.

I'm not bidding for that tender. But the question was genuinely interesting, and along the way I discovered something I had no idea about: **Sentinel satellite imagery is open and free** — anyone can pull it from the [Copernicus Data Space portal](https://dataspace.copernicus.eu/) with a free account. Decades of EU-funded radar imagery of the entire planet, a few clicks away. That alone was worth the rabbit hole.

> *Is on-board AI a real engineering option in 2026, or still science-fiction with a marketing budget?*

**AIDRA** — *AI-enabled On-Board Data Processing Assessment* — is the actual SatCen project. The tender is asking external teams to study whether this is viable. What follows is my own personal take on it: a small feasibility study against the same evaluation grid, with measured numbers and a paper trail anyone can re-run.

## The premise: a "fake satellite" you can actually rent

The single biggest constraint of an on-board AI is **compute**: you have a few watts, a few CPU cores, and a couple of gigabytes of RAM. You cannot ssh into a GPU rack at 700 km altitude.

I needed a way to simulate that without launching anything. The trick:

- The whole AIDRA pipeline runs on a single **Oracle Cloud ARM Free Tier** VM (4 OCPU, 24 GB RAM, Frankfurt region — EU sovereignty matters here).
- That box plays the role of "ground reference."
- On top of it I define five **constraint profiles** — `ground`, `sat-mid`, `sat-low`, `sat-strict`, `sat-extreme` — that throttle the same model down to spacecraft-class budgets (down to **0.25 OCPU / 512 MB RAM** in the most aggressive one).
- The same Sentinel-1 scene runs through all five. You can see exactly where the pipeline *starts to break*.

That last sentence is the whole point of the study. Not "does it work in the lab," but "at what point does it stop working, and how gracefully?"

![AIDRA Grafana home: pipeline runs, vessels detected, models registered]({{ site.baseurl }}/images/aidra/home.png "AIDRA Grafana home dashboard")

*A few numbers from a recent run: 24 pipeline executions, 6,571 vessels detected across all profiles, 3 model variants registered, last run 4 hours ago. The home dashboard is the index — every other panel drills into one piece of the story.*

---

## What I actually measured

Three results stand out. None of them are surprising in isolation. The interesting thing is they're all measured on the **same hardware**, with the **same model family**, end-to-end, and you can replay every single number from the public dashboards.

### 1. Compression: smaller, faster, basically the same accuracy

Quantising the YOLOv8 detector from FP32 to dynamic INT8 — a one-line PyTorch change — gives a clean trade-off:

| Variant | Model size | Total inference (50 scenes) | Avg confidence | Peak RAM |
|---|---|---|---|---|
| fp32 (baseline) | 49.6 MB | 52.7 min | 53.9% | 3.50 GB |
| **dynamic_int8** | **25.1 MB** | **33.9 min** | **53.6%** | 4.35 GB |

Half the disk. ~35% less wall-clock time. **0.3 percentage points** of confidence lost — well within noise. Peak RAM actually goes *up* a bit (PyTorch's dynamic INT8 keeps some FP32 staging buffers), which is the kind of detail you only see once you measure on the real target.

![Compression benchmark dashboard]({{ site.baseurl }}/images/aidra/compression-bench.png "Compression benchmark: fp32 baseline vs dynamic INT8")

### 2. The on-board processing payoff

This is the chart that justifies the whole project. The question is: *what happens to the end-to-end latency if the satellite processes the scene on-board and only downlinks the contact list, vs the traditional "dump the raw scene, process on the ground" workflow?*

| Downlink | Without OBDP | With OBDP | Speed-up |
|---|---|---|---|
| S-band (0.5 Mbps) | 0 useful images/day | 31 | — |
| X-band (50 Mbps) | 2 | 3,166 | 1,583× |
| Ka-band (300 Mbps) | 13 | 18,996 | 1,461× |
| Laser (1.8 Gbps) | 40 | 56,988 | 1,425× |

On a typical X-band link, a satellite that processes scenes on-board can deliver **~1,500× more useful daily output** than one that just acts as a camera. Or, looked at the other way: **27.9 GB** of raw imagery becomes a few kilobytes of geo-tagged contact reports — a **~1,900× data compression ratio**.

![Downlink and OBDP value]({{ site.baseurl }}/images/aidra/obdp-value.png "Why on-board processing matters: 27.9 GB → contact reports")

The end-to-end "vessel passes overhead → operator sees the contact" latency drops by **5.3×** on the orbits I modelled, mostly because you don't have to wait for the next ground-station pass to dump a 9 GB raw scene.

![Orbital latency: 5.30x speedup]({{ site.baseurl }}/images/aidra/orbital-latency.png "Orbital latency: 5.30x speedup with on-board processing")

### 3. Honest limits

What didn't work, or only barely worked:

- **`sat-extreme` (0.25 OCPU, 512 MB)** is below the floor. The model loads, but the runtime thrashes on swap and the per-scene latency goes from minutes to *hours*. That's the failure mode worth reporting — not a number to brag about.
- **Cluster anomaly flags fire more often at the swath edge** than I'd like. The current preprocessing chain (orbit correction → σ⁰ calibration → speckle filter → terrain correction → edge swath filter) cleans most of it, but a non-trivial fraction of "detections" near the image border are still SAR artefacts, not boats. I keep them, tag them `cluster_anomaly`, and exclude them from the headline metrics.
- **Confidence around 54%** is fine for a feasibility study using off-the-shelf weights, but it's not a production number. A real deployment would fine-tune on a balanced xView3-SAR + HRSID + OpenSARShip mix and probably land at 75–85%.

I'm noting these because the *point* of a feasibility study is not to oversell.

---

## The second half: the bits the evaluator actually cares about

If you've made it this far and you don't work in EU procurement, you can stop here. The summary above is the story.

For everyone else: in this kind of tender, **the technology is rarely the differentiator** — the differentiator is whether your methodology is auditable. Three things turned out to matter much more than the model:

### Traceability as a first-class citizen

Every artefact that touches the pipeline gets a SHA-256:

- the raw Sentinel-1 product hash,
- the model weights hash,
- the input-parameters hash (the serialised `Settings`),
- the output GeoJSON hash,
- the git commit SHA at run time.

These five hashes are written to an `execution_log` table in PostgreSQL **before** the run starts (state = `pending`), then updated when the run finishes. Crashed runs don't disappear — they stay in the log as `failed`, fully reproducible. The whole thing is one of the boring backbone tests in the repo, and it's what lets me say "here's the evidence bundle" instead of "trust me."

### AI Act compliance, baked in

The EU AI Act (Reg. 2024/1689) requires, among other things, that high-risk AI systems carry a model card with their purpose, training data, known biases, and limitations. AIDRA enforces this at the orchestration layer: **a model without a `MODEL_CARD.md` cannot be registered**, and therefore cannot run in the pipeline. It's a one-line check that turns "we should write documentation" into "the system refuses to start without it."

### Geospatial integration that a GEOINT analyst would recognise

Detections are persisted with native PostGIS geometry (EPSG:4326), with the SAR thumbnail of each contact attached, filterable by profile / model / on-land flag, and exportable in the kind of OGC-friendly format that ground-segment systems already speak. Nothing exotic. Just the bare minimum to fit into existing workflows rather than asking analysts to learn a new tool.

## The pieces, briefly

For the curious — the actual stack:

- **Language:** Python 3.11 end-to-end. FastAPI for the API, PyTorch for the model, rasterio + GDAL for SAR I/O.
- **Detector:** YOLOv8 (textural features) + a classical CFAR detector (point reflectors), ensembled. SAR-specific because optical sensors are useless at night and under clouds.
- **Datasets:** xView3-SAR, HRSID, OpenSARShip. All open, all license-compatible.
- **Database:** PostgreSQL 16 + PostGIS 3.4.
- **Observability:** Prometheus + Grafana + Loki, with `run_id` propagated end-to-end through logs and metric labels. The dashboards in this post are read straight from production.
- **Hosting:** OCI Free Tier ARM (Frankfurt). One small VM, no GPU, EU-only data residency.

## What this study is *not*

It's not a satellite. It's not a product. It's not a benchmark of state-of-the-art vessel detection (the SOTA mAP figures live in academic papers, not on a Free Tier VM). It does not promise to solve maritime surveillance.

It's a deliberately small, honest exercise in answering: *given the real-world constraints of on-board hardware, EU data sovereignty, and AI Act compliance, what does a working ship-detection pipeline actually look like, and where does it crack?*

---

*Code on [GitHub](https://github.com/RadW2020/aidra-feasibility-study). Dashboards and the full evidence bundle live at the [AIDRA Grafana](https://aidra.uliber.com). Inspired by SatCen tender SATCEN/2026/OP/0003; not affiliated with SatCen or the European Union.*
