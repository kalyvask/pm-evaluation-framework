---
name: pm-metrics-critic
description: Critique a metrics dashboard, success-criteria section, or proposed North Star metric against the repo's metrics guide. Use when the user shares a dashboard, a list of KPIs, a success-criteria slide, or asks "are these the right metrics?" Surfaces the three most common metric failures: aggregate metrics that hide segment-level failure, vanity metrics decoupled from strategy assumptions, and standalone metrics with no falsifiable counter. Returns a metric-by-metric verdict and a recommended replacement set.
---

# PM metrics critic

Reviews a set of metrics — a dashboard, a success-criteria section, a North Star proposal — against `decision-making/metrics.md`. The core test: does each metric, if it moved, tell us something *strategic*, or does it just tell us the product is being used? Most metric sets fail this test and the skill's job is to say so concretely.

## When to use

Use this when:
- The user shares a dashboard or KPI list and asks "are these the right metrics?"
- The user is locking success criteria for a launch or a quarterly OKR
- The user is proposing or revisiting a North Star metric
- A metric "moved" and the team is debating whether the underlying assumption was actually validated

Don't use this when:
- The user wants a full PRD critique — use `pm-prd-drafter`
- The user wants to build a metric *tree* from scratch (mapping inputs → outputs → outcomes) — that's a longer exercise; reference `decision-making/metrics.md` § metric trees and walk it manually
- The user is debugging a specific dashboard query or instrumentation bug — that's an engineering task

## How to apply

1. **Pull the strategy assumptions.** Reference `decision-making/metrics.md` § "Match metrics to strategy assumptions." For the work in question, list the load-bearing strategic assumptions. If the user can't articulate them, surface that gap before evaluating any metric — you can't grade metrics without strategy.

2. **For each proposed metric, ask: what assumption would this falsify?** If a metric can't falsify any assumption — if it can only confirm "the product is being used" — it's a vanity metric. Mark it as such.

3. **Run the segment-level decomposition.** Aggregate metrics hide segment failures. If the strategy assumption is segment-specific ("top creators will adopt"), the metric must be segment-specific. Top-line DAU does not validate a top-creator assumption.

4. **Run the standalone-vs-counterweight check.** From `decision-making/metrics.md` § counter-metrics: every primary metric should have a counter-metric that catches the obvious gaming path. Engagement up + retention down is a different story than engagement up + retention flat. Flag any metric that ships without a counter.

5. **Run the leading-vs-lagging check.** A success criterion of "ARR by Q4" tells you nothing in weeks 1–8. Identify the leading indicator that would predict the lagging metric *early enough to act on it*.

6. **Recommend a replacement set.** Not "track more metrics." A focused list of 3–5 metrics that each map to a strategic assumption, with a counter-metric for each.

## Output structure

```
## TL;DR
[One-paragraph honest take. Are these metrics measuring the strategy or the activity?]

## Strategic assumptions in play
1. [Assumption 1 — load-bearing for this work]
2. [Assumption 2]
3. ...

## Metric-by-metric
| Metric | What it would falsify | Verdict |
|---|---|---|
| [Metric A] | [Assumption / nothing — vanity] | 🟢 strategic / 🟡 weak / 🔴 vanity |
| [Metric B] | ... | ... |

## Failure modes flagged
- **Aggregate masking segment failure:** [Which metric, what segment is hidden]
- **No counter-metric:** [Which metric, what the obvious gaming path looks like]
- **Lagging-only:** [Which metric, what leading indicator should sit alongside it]
- **Decoupled from strategy:** [Which metric, what assumption it claims to validate but doesn't]

## Recommended replacement set
1. **[Primary metric]** — falsifies *[assumption]*. Segment: [specific]. Threshold: [specific]. Counter-metric: [specific].
2. **[Primary metric 2]** — ...
3. ...

## What an exec will press on
[The 1-2 metrics questions the team will be asked that they're not yet ready for.]
```

## What good looks like

- Every recommended metric is named with a *segment* and a *threshold*. "Adoption" is not a metric. "Adoption among top-decile creators reaching 25% in 60 days" is.
- Each metric has a counter-metric. No exceptions.
- The North Star metric (if one is proposed) is a single metric the entire org could agree to optimize, not a basket of five things.
- Vanity metrics are called out explicitly. "DAU is a vanity metric for this strategy because the assumption is about *which* users adopt, not *how many*" — that level of specificity.
- Leading indicators are named. The team should not have to wait until Q4 to know if Q4 is on track.

## Anti-patterns

- Approving a dashboard because it has "good metrics on it" without checking what they would falsify.
- Recommending more metrics. Metric proliferation is itself a failure mode — most dashboards need fewer, sharper metrics, not more.
- Accepting "engagement" as a metric. Engagement is a category. Engagement-with-what, by-whom, doing-what, is the metric.
- Letting a North Star metric ship without naming the strategic bet it represents. If the team can't say "if North Star moves, it means [specific strategic claim] is true," the North Star isn't load-bearing.
- Ignoring the counter-metric requirement because the team "would never game it." Gaming is rarely intentional; it's structural. The counter-metric exists to catch the structural drift.
