---
layout: post
title: "15 PromQL concepts every SRE should know"
featured: true
---

PromQL is one of those languages that looks deceptively simple for the first five minutes and then quietly ruins your afternoon. You write `rate(http_requests_total[5m])` and it works. You try `rate(http_requests_total[5m]) / rate(http_requests_total[5m])` and you get `NaN`. Why? Because vector matching. What's vector matching? Exactly.

This is the second post in the series. If you haven't read the first one, it covers [15 alerting terms every SRE should know]({% post_url 2026-04-16-15-alerting-terms-every-sre-should-know %}).

Fifteen PromQL concepts, explained with the confusions that trip people up in real dashboards.

---

## Block 1 — The data model

### 1. Time series

**What it is:** a sequence of timestamped numeric samples, identified uniquely by a metric name + label combination.

**Analogy:** a single line on a graph. The x-axis is time, the y-axis is the value. That one line is one time series.

**Example in Grafana:** `http_requests_total{service="checkout", status="200"}` is one series. `http_requests_total{service="checkout", status="500"}` is a *different* series. A query can return many series at once.

**Don't confuse with:** the metric *name*. The name (`http_requests_total`) groups many series. The series is the name plus a specific label combination.

---

### 2. Instant vector vs range vector

**What it is:** two different "shapes" of data in PromQL.
- **Instant vector:** one value per series, at a single point in time. `http_requests_total` on its own.
- **Range vector:** a window of values per series, over a duration. `http_requests_total[5m]` returns every sample from the last 5 minutes per series.

**Analogy:** instant vector is a photograph (one moment). Range vector is a short video clip (many moments).

**Example in Grafana:** you cannot graph a range vector directly — Grafana will refuse. You need to *reduce* it with a function (`rate`, `avg_over_time`, etc.) that turns it back into an instant vector.

**Don't confuse with:** each other. 90% of "this query doesn't work" is "I used one where the other was required".

---

### 3. Counter vs gauge

**What it is:** two fundamental metric types.
- **Counter:** a value that only goes up (or resets to zero on restart). `http_requests_total`, `errors_total`.
- **Gauge:** a value that can go up or down. `memory_usage_bytes`, `queue_size`, `temperature_celsius`.

**Analogy:** counter is your car's odometer — only grows (and resets when the engine is rebuilt). Gauge is the speedometer — fluctuates freely.

**Example in Grafana:** you almost never graph a counter directly (the line just goes up forever). You graph `rate(counter[5m])` — its per-second growth rate. Gauges you graph directly.

**Don't confuse with:** histograms and summaries — those are more complex types built on top of counters and gauges.

---

## Block 2 — The functions you'll use every day

### 4. `rate()`

**What it is:** calculates the per-second average rate of increase of a counter over a range window, after automatically handling counter resets.

**Analogy:** looking at your odometer and saying "you drove 300 km in the last 5 hours, so your average speed was 60 km/h". `rate` does that for you.

**Example in Grafana:** `rate(http_requests_total[5m])` returns requests-per-second over a 5-minute rolling window. This is the correct way to turn a counter into a "throughput" graph.

**Don't confuse with:** `increase()` which returns the *total* growth over the window (not per-second). And don't confuse with `irate()` (next).

---

### 5. `rate()` vs `irate()`

**What it is:** both compute rates of counters, but:
- `rate()`: averages across the whole window — smooth, good for alerts and long views.
- `irate()`: uses only the *last two* data points in the window — jittery, good for short-term spikes.

**Analogy:** `rate` is your average speed over the whole trip. `irate` is what the speedometer says *right now*.

**Example in Grafana:** for a 24-hour dashboard, always use `rate` — `irate` will look like a seismograph. For zoom-in debugging of a 2-minute spike, `irate` tells you more.

**Don't confuse with:** the idea that `irate` is "more accurate". It's more *reactive*, which is a different thing. In alerts, reactivity causes flapping.

---

### 6. `sum()` and `by` / `without`

**What it is:** aggregation operators that collapse multiple series into fewer (or one), optionally preserving certain labels.

**Analogy:** an Excel pivot table. You have rows by product + region + month. `sum by (region)` collapses product and month but keeps region.

**Example in Grafana:**
- `sum(rate(http_requests_total[5m]))` → one single series: total QPS across everything.
- `sum by (service) (rate(http_requests_total[5m]))` → one series per service.
- `sum without (pod) (...)` → keeps everything *except* `pod`. Useful when pod names are noise.

**Don't confuse with:** omitting `by`/`without` entirely. Then all labels are dropped and you get one unified series — usually not what you want.

---

### 7. `histogram_quantile()`

**What it is:** calculates a percentile (p50, p95, p99…) from a Prometheus histogram metric.

**Analogy:** class test results. The p95 is the score below which 95% of students scored. In metrics: the latency below which 95% of requests completed.

**Example in Grafana:** `histogram_quantile(0.95, sum by (le) (rate(http_request_duration_seconds_bucket[5m])))`. The `le` ("less than or equal") label is what Prometheus uses to define histogram buckets — you **must** preserve it in the aggregation.

**Don't confuse with:** summaries. Summaries pre-compute percentiles on the client, can't be aggregated across instances, and are generally being phased out in favour of histograms.

---

## Block 3 — Arithmetic, matching, the stuff that breaks silently

### 8. Vector matching

**What it is:** the rules PromQL uses to pair up series from the left and right side of a binary operation (`+`, `-`, `*`, `/`). By default: only series with *identical labels* on both sides match. Anything else is dropped silently.

**Analogy:** two decks of labelled cards. You can only add two cards if every label matches exactly. Cards without a partner are thrown away.

**Example in Grafana:** `rate(errors[5m]) / rate(requests[5m])` works if both metrics have the same labels. If `errors` has an extra `error_type` label that `requests` doesn't, the match fails and you get empty results — no error, no warning.

**How to mitigate:** use `on(...)` to restrict matching to specific labels, or `ignoring(...)` to exclude some, or `group_left` / `group_right` for many-to-one joins.

**Don't confuse with:** aggregation. Matching is about combining *two* queries. Aggregation is about collapsing *one*.

---

### 9. `on()` / `ignoring()` / `group_left`

**What it is:** modifiers that customise vector matching.
- `on(label1, label2)` — match only on the listed labels, ignore the rest.
- `ignoring(label1)` — match on everything *except* the listed labels.
- `group_left` / `group_right` — allow a many-to-one match (with extra labels carried from the "many" side).

**Analogy:** spreadsheet JOINs. `on` is an inner join on specific columns. `group_left` is a LEFT JOIN where you want extra columns from the joined table.

**Example in Grafana:** joining request metrics with a build info metric to add a `version` label: `rate(http_requests_total[5m]) * on(instance) group_left(version) build_info`.

**Don't confuse with:** SQL joins. They're conceptually similar but the syntax is alien until you've written five of them.

---

### 10. `offset` and `@` modifier

**What it is:** time-shifting tools.
- `offset 1h` — query the metric as it was 1 hour ago.
- `@ <timestamp>` — query at a fixed absolute timestamp.

**Analogy:** your phone's photo "memories" — "this day 1 year ago". You look at the same metric, but displaced in time.

**Example in Grafana:** compare current traffic with last week's at the same time: `rate(http_requests_total[5m]) / rate(http_requests_total[5m] offset 1w)`. If the ratio drops to 0.5, you've lost half your traffic versus the same moment last week.

**Don't confuse with:** using a custom dashboard time range — `offset` lets you combine *current* and *past* values in the *same* query.

---

## Block 4 — Time-based aggregations

### 11. `_over_time` family

**What it is:** a set of functions (`avg_over_time`, `max_over_time`, `min_over_time`, `sum_over_time`, `stddev_over_time`, `quantile_over_time`…) that aggregate a *single* series across a time window.

**Analogy:** taking a week's worth of daily temperatures and reducing them to "the hottest day" or "the average week temperature".

**Example in Grafana:** `max_over_time(cpu_usage[1h])` returns, per series, the peak CPU usage seen in the last hour. Very useful for capacity alerts: "alert if max CPU in the last hour > 90%".

**Don't confuse with:** regular aggregation (`sum`, `avg`). Regular aggregation collapses across *series*. `_over_time` collapses across *time*.

---

### 12. `absent()` and `absent_over_time()`

**What it is:** functions that return a non-empty vector only when the queried series is *absent*.
- `absent(up{job="api"})` → returns 1 if no series match.
- `absent_over_time(up{job="api"}[10m])` → returns 1 if no series were seen for the whole window.

**Analogy:** a dead man's switch. The switch triggers when it *stops* receiving a signal.

**Example in Grafana:** critical for detecting when a service stops scraping entirely. If `up` just disappears, normal alerts can't fire (there's no data to compare). `absent` is how you alert on "we stopped hearing from it".

**Don't confuse with:** `== 0`. That requires the series to *exist* and be zero. `absent` fires when the series doesn't exist at all.

---

## Block 5 — Performance and organisation

### 13. Recording rules

**What it is:** pre-computed PromQL queries that Prometheus evaluates on a schedule and stores as new metrics. You query the pre-computed metric instead of re-running the expensive query every time.

**Analogy:** meal prep on Sunday. You cook once, eat all week. The query runs once per evaluation interval, every dashboard loads instantly.

**Example in Grafana:** turn a heavy `histogram_quantile(0.95, sum by (le, service) (rate(...)))` into a recording rule that emits `service:http_request_duration_p95:rate5m`. Dashboards use the short version — fast and cheap.

**Don't confuse with:** alert rules. Alert rules evaluate a condition and may fire. Recording rules evaluate a query and store the result. Both live in the same rule file.

---

### 14. Subqueries

**What it is:** a syntax that lets you turn an instant vector expression into a range vector on the fly: `<expression>[5m:30s]`. It evaluates the expression every 30 seconds for the last 5 minutes.

**Analogy:** asking a calculator to solve the same equation every 30 seconds for 5 minutes and showing you all the answers as a sequence.

**Example in Grafana:** `max_over_time(rate(http_requests_total[1m])[10m:])` — the maximum per-minute request rate over the last 10 minutes. The subquery is the only way to apply `_over_time` functions to things that are themselves already computed.

**Don't confuse with:** regular range vectors. Subqueries are expensive — Prometheus recomputes the inner expression at every step. Use a recording rule if you find yourself relying on them a lot.

---

### 15. `up`

**What it is:** a special metric Prometheus generates automatically for every target it scrapes. `1` if the scrape succeeded, `0` if it failed.

**Analogy:** the "signal bars" icon on your phone. It's not the thing being measured — it's the measurement of whether the measurement itself is working.

**Example in Grafana:** the simplest and most important alert you'll ever write: `up == 0 for 5m`. If `up` disappears entirely, see `absent()` — the combination of the two covers both "scrape failing" and "target vanished".

**Don't confuse with:** application-level health. `up == 1` means "Prometheus managed to reach the /metrics endpoint". The app itself may still be returning 500s to users.

---

## What's next

Next post closes the series: *"15 observability patterns every SRE should know"* — the concepts that turn metrics and alerts into actual decisions. SLOs, error budgets, golden signals, exemplars, and the patterns that separate a dashboard from a diagnostic tool.

If one of the PromQL expressions in this post burned you personally in the last month, tell me — those are the best additions for a future "part 2".
