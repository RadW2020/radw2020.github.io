---
layout: post
title: "15 alerting terms every SRE should know"
featured: true
---

Every time I read a Grafana Alerting discussion I bump into words that sound obvious until someone asks me to define them. *Flapping*, *silence*, *inhibition*, *cardinality explosion*. You nod, you use them, and then one day a junior asks "wait, what's the difference between a silence and a mute timing?" and you realise you're not sure.

This post is the glossary I wish I had when I started. Fifteen terms, real Grafana examples, and the small confusions that bite you in practice.

It's the first of a three-part series:

1. **Alerting terms** ← you are here
2. PromQL concepts every SRE should know
3. Observability patterns every SRE should know

---

## At a glance

| #  | Term                     | In one line                                                            | Category            |
|----|--------------------------|------------------------------------------------------------------------|---------------------|
| 1  | [Alert rule](#1-alert-rule)                         | The boolean condition that defines *when* an alert fires.              | Life cycle          |
| 2  | [Firing](#2-firing)                                 | The alert's condition has been true long enough to count.              | Life cycle          |
| 3  | [Pending](#3-pending)                               | Condition is true, but the `for:` buffer hasn't elapsed yet.           | Life cycle          |
| 4  | [Silence](#4-silence)                               | Time-bounded mute of notifications — the alert still evaluates.        | Noise control       |
| 5  | [Inhibition](#5-inhibition)                         | If alert A fires, suppress alert B automatically.                      | Noise control       |
| 6  | [Grouping](#6-grouping)                             | Collapse many related instances into a single notification.            | Noise control       |
| 7  | [Flapping](#7-flapping)                             | Alert oscillating fast between firing and resolved.                    | Pathologies         |
| 8  | [Alert fatigue](#8-alert-fatigue)                   | On-call desensitised by too many low-value notifications.              | Pathologies         |
| 9  | [Cardinality explosion](#9-cardinality-explosion)   | Too many label combinations wrecking storage and queries.              | Pathologies         |
| 10 | [Contact point](#10-contact-point)                  | The destination a notification is sent to (Slack, email, webhook…).    | Routing             |
| 11 | [Notification policy](#11-notification-policy)      | The tree that routes each alert to the right contact point.            | Routing             |
| 12 | [SLI / SLO](#12-sli--slo)                           | What you measure vs the internal target you commit to.                 | Telemetry           |
| 13 | [RED method](#13-red-method)                        | Rate, Errors, Duration — the three metrics per request-driven service. | Telemetry           |
| 14 | [Label](#14-label)                                  | Key-value pair that dimensions a metric into a unique series.          | Prometheus basics   |
| 15 | [Fingerprint](#15-fingerprint)                      | Hash of labels that uniquely identifies an alert instance.             | Prometheus basics   |

---

## Block 1 — The life cycle of an alert

### 1. Alert rule

**What it is:** the definition of an alert. A boolean condition evaluated on a schedule: *"if this query returns a value above X for Y minutes, fire"*.

**Analogy:** a smoke detector. The rule is "if particles in the air > threshold → beep". The rule itself isn't firing — it's the policy that decides when to fire.

**Example in Grafana:** a rule that runs `avg_over_time(http_request_duration_seconds[5m]) > 0.5` every 30 seconds against Prometheus.

**Don't confuse with:** the alert *instance*. One rule can produce many instances — one per label combination (one per service, one per region, etc.).

---

### 2. Firing

**What it is:** the state of an alert instance whose condition is currently true and has been true long enough to "count".

**Analogy:** the smoke detector is actually beeping.

**Example in Grafana:** you see a red badge in the Alerting UI. Notifications have been sent to the configured contact points.

**Don't confuse with:** *pending*. Pending means "the condition just became true, but we're waiting to make sure it sticks". Firing means "it stuck".

---

### 3. Pending

**What it is:** a transitional state. The condition is true **right now**, but the `for:` duration hasn't elapsed yet, so no notification is sent.

**Analogy:** you smell something burning but you're not sure yet — you wait 30 seconds before yelling "fire!".

**Example in Grafana:** a rule with `for: 2m` that just became true stays in *Pending* for 2 minutes. If the condition stays true the whole time, it promotes to *Firing*. If it drops, pending is cancelled silently — no one is notified.

**Don't confuse with:** firing. Pending is the anti-flapping buffer. It exists precisely so you don't page someone for a 10-second blip.

---

## Block 2 — Controlling the noise

### 4. Silence

**What it is:** a time-bounded rule that suppresses **notifications** for alerts matching a set of labels. The alert still evaluates and still shows as firing in the UI — but nobody gets paged.

**Analogy:** the "Do Not Disturb" mode on your phone. Calls still come in; the phone just doesn't ring.

**Example in Grafana:** before a planned deploy to staging, you create a silence with matcher `env=staging` from now until 30 minutes later. Alerts during the deploy fire in the UI but no Slack messages go out. It expires on its own.

**Don't confuse with:** disabling the rule. Disabling stops evaluation entirely and has no auto-expiry — you'll forget to re-enable it.

---

### 5. Inhibition

**What it is:** a rule that says "if alert A is firing, suppress alert B". Used to avoid cascades of notifications for a single root cause.

**Analogy:** when the main power goes out at home, you don't want the UPS beeper, the fridge beeper, and the alarm panel beeper all screaming at once. The power-outage alert *inhibits* the downstream ones.

**Example in Grafana:** if `DatabaseDown` is firing, inhibit `HighAPIErrorRate` and `CheckoutFailing` for the same service — they're symptoms, not the cause.

**Don't confuse with:** silence. Silence is a manual, time-bounded mute. Inhibition is an automatic, condition-based relationship between alerts.

---

### 6. Grouping

**What it is:** collapsing multiple related alert instances into a single notification instead of sending one per instance.

**Analogy:** a news app that says "12 new messages from Slack" instead of 12 separate notifications.

**Example in Grafana:** if 20 pods from the same deployment go unhealthy at once, grouping by `deployment` sends you one Slack message listing all 20, not 20 separate messages.

**Don't confuse with:** inhibition. Grouping merges notifications of the *same* alert across instances. Inhibition suppresses *different* alerts based on dependency.

---

## Block 3 — Pathologies

### 7. Flapping

**What it is:** an alert that rapidly oscillates between firing and resolved in a short time window, generating many notifications for what is effectively a single fuzzy event.

**Analogy:** a light switch with bad contact. The light flickers on-off-on-off instead of settling.

**Example in Grafana:** a latency alert with threshold 500ms when your normal latency is 480ms. Any natural variation crosses the threshold. During a deploy you might see 6 firing/resolved cycles in 20 minutes.

**Don't confuse with:** a legitimate persistent alert. A database that's been down for 20 minutes is firing continuously — that's not flapping, that's just a real incident.

**How to mitigate:** raise the threshold, lengthen `for:`, use `keep_firing_for`, or build a detector that creates auto-silences when it spots the pattern.

---

### 8. Alert fatigue

**What it is:** the human effect where an on-caller receives so many low-value notifications that they start ignoring all of them — including the real ones.

**Analogy:** the boy who cried wolf. If your alerts lie often, people stop believing them.

**Example in Grafana:** a team getting 40 Slack pings a day from `StagingPodRestarted`. Nobody reads them anymore. The day production has a real incident, the first page is ignored for 10 minutes.

**Don't confuse with:** a noisy day. Fatigue is a *chronic* condition caused by systemic over-alerting, not a one-off busy shift.

**How to mitigate:** audit every alert quarterly with a ruthless question — *"did this actionably change someone's behaviour last time it fired?"*. If not, delete it or lower its severity.

---

### 9. Cardinality explosion

**What it is:** when the combination of labels on a metric produces far too many unique time series, making storage and queries slow or impossible.

**Analogy:** organising a library by author is fine. Organising it by author + exact minute the book was checked out + customer's email creates billions of categories and nobody can find anything.

**Example in Grafana:** adding `user_id` as a label to an HTTP metric. If you have 1M users, you just created up to 1M time series per endpoint per status code. Prometheus OOMs, queries time out, bills explode.

**Don't confuse with:** having lots of metrics. The problem isn't the number of metric *names* — it's the number of label *combinations* per metric.

**How to mitigate:** never use high-cardinality values (user IDs, request IDs, timestamps) as labels. Use exemplars or logs for that.

---

## Block 4 — Routes and notifications

### 10. Contact point

**What it is:** a destination for notifications. Slack channel, email address, PagerDuty service, webhook URL.

**Analogy:** the "To:" field of an email. It says *where* the message goes, not *what* it says or *when* it's sent.

**Example in Grafana:** you configure a contact point called `oncall-slack` pointing to the `#alerts-prod` channel, and another one called `webhook-flap-sentinel` pointing to your custom service.

**Don't confuse with:** notification policy. The contact point is the *destination*. The policy is the *decision* of which alerts reach which destination.

---

### 11. Notification policy

**What it is:** the tree of rules that decides, for each firing alert, which contact point receives it — based on its labels.

**Analogy:** the sorting hat at Hogwarts. Each alert walks up, the hat reads its labels, and assigns it to a house (contact point).

**Example in Grafana:** root policy sends everything to `oncall-slack`. Child policy matches `severity=critical` and routes to PagerDuty. Another child matches `team=payments` and routes to the payments Slack channel.

**Don't confuse with:** the alert rule. The rule decides *when* to fire. The policy decides *where* the firing alert goes.

---

## Block 5 — Telemetry vocabulary worth knowing

### 12. SLI / SLO

**What it is:** two intertwined concepts.
- **SLI (Service Level Indicator):** a *measurement* of how well a service is doing. E.g. "percentage of requests that complete under 300ms".
- **SLO (Service Level Objective):** a *target* for that indicator. E.g. "99.9% of requests under 300ms over 30 days".

**Analogy:** a student's grade on a test is the SLI. "You must score at least 80%" is the SLO.

**Example in Grafana:** you define an SLI as `rate(http_requests_success[5m]) / rate(http_requests_total[5m])` and set an SLO at 99.9%. Your alerts fire not when things are "bad right now" but when you're burning the error budget too fast to meet the SLO.

**Don't confuse with:** SLA. The SLA is the contractual/legal promise to customers (often looser than the SLO). The SLO is the internal engineering target.

---

### 13. RED method

**What it is:** a framework for deciding *what to measure* about a request-driven service. Three metrics: **R**ate (requests/sec), **E**rrors (error rate), **D**uration (latency).

**Analogy:** when a doctor checks a patient, they measure pulse, blood pressure, and temperature. You don't need 50 vital signs — three well-chosen ones tell you most of what's wrong.

**Example in Grafana:** for every HTTP service you build a dashboard with three panels: requests per second, error percentage, p95 latency. If all three look healthy, the service is probably fine.

**Don't confuse with:** USE (Utilization, Saturation, Errors) — USE is for *resources* (CPU, disk, memory), RED is for *services*.

---

## Block 6 — Prometheus essentials that show up everywhere

### 14. Label

**What it is:** a key-value pair attached to a metric that dimensions it. The same metric name plus a different label value is a different *time series*.

**Analogy:** a filing cabinet. `http_requests_total` is the drawer. `{method="GET", status="200"}` is the specific folder inside.

**Example in Grafana:** `http_requests_total{service="checkout", method="POST", status="500"}` — four labels, one series. Change any value and it's a different series.

**Don't confuse with:** the metric name itself. The name is the noun; labels are the adjectives.

---

### 15. Fingerprint

**What it is:** a hash uniquely identifying an alert instance based on its labels. Same labels → same fingerprint. Different labels → different fingerprint.

**Analogy:** a human fingerprint. Two different people can share a name ("John Smith") but never a fingerprint.

**Example in Grafana:** when building a webhook receiver, the fingerprint is how you know that two incoming events refer to the *same* alert instance (so you can count state transitions for flap detection, for example).

**Don't confuse with:** the alert name. Many instances of the same rule share the name `HighLatency` but each has its own fingerprint because their labels differ (`service=checkout` vs `service=cart`).

---

## What's next

Now that the vocabulary is out of the way, the follow-ups get more concrete:

- **Next post:** *"15 PromQL concepts every SRE should know"* — because you can't talk about alerts without talking about the query language that powers them.
- **After that:** *"15 observability patterns every SRE should know"* — error budgets, exemplars, golden signals, and friends.

If I missed a term you argue about every week, tell me and I'll add it to the list before the next instalment.
