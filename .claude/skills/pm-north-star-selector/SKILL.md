---
name: pm-north-star-selector
description: Pick a single North Star metric for a product. Weighs candidates across behavioral (MAU, sessions), value-delivered (messages sent, orders completed), and financial (ARR, revenue), forcing the comparison most teams skip — explainability, adoption + retention coverage, lead/lag, gameability. Use when a PM is defining a North Star, debating between MAU/DAU vs. value/revenue, or revisiting an existing one. Pushes back on jumping to a sophisticated composite or to revenue too early. Different from pm-metrics-critic, which reviews whole dashboards; this skill picks the one number.
---

# PM North Star selector

Helps a PM pick *one* North Star metric. Most teams over-rotate in one of two directions: (a) defaulting to MAU/DAU without checking whether activity actually tracks the strategic bet, or (b) reaching for a sophisticated metric (value delivered, revenue, custom composite) that nobody in the org can explain. The skill forces the comparison and lands on a single defensible number.

## When to use

Use this when:
- The team is defining a North Star for the first time
- The team has a North Star and someone has proposed replacing it
- The user is debating "should we use MAU or revenue / value / something more sophisticated?"
- A leadership review keeps asking "why this metric?" and the answer doesn't hold

Don't use this when:
- The user wants a *full* metrics dashboard reviewed — use [`pm-metrics-critic`](../pm-metrics-critic/SKILL.md)
- The user is debating *input metrics* under an already-locked North Star — that's a metric-tree exercise, see `decision-making/metrics.md` § growth equation
- The strategy itself is unclear — fix that first using [`pm-framework-selector`](../pm-framework-selector/SKILL.md). A North Star without a strategy is just a number.

## The core tension

A North Star has two jobs that pull in opposite directions:

1. **Capture strategic product health** — has to move when the product is genuinely working
2. **Align the org** — has to be a single number every team can explain, defend, and act on

Teams that only optimize (1) end up with "weighted engaged-user value" that nobody outside the metrics team can explain. Teams that only optimize (2) end up with DAU and ship changes that move DAU without moving the business.

The right North Star is the *simplest metric that still captures the strategic bet.* Not the most sophisticated one that captures it best.

## How to apply

1. **Name the strategic bet in one sentence.** What has to be true for this product to succeed? "Users who try it once will come back weekly and bring others." "Buyers who list once will keep listing." "Free users will convert to paid within 14 days." If the user can't state this, stop and surface the gap — every other step depends on it. Reference `decision-making/metrics.md` § "Match metrics to strategy assumptions."

2. **List 3–5 candidate North Stars across categories.** Be concrete — not "engagement" but "weekly active users who sent at least one message."

   | Category | Examples |
   |---|---|
   | Behavioral / active users | DAU, WAU, MAU |
   | Value-delivered (product output) | Messages sent, photos shared, rides completed, queries answered, reports generated |
   | Quality-adjusted active users | MAU with ≥ N actions, L28 retained users |
   | Financial | Revenue, ARR, GMV, paid conversion rate |
   | Composite | "Engaged users" by multiple actions, custom score |

3. **Score each candidate on the five dimensions below.** Use 🟢 / 🟡 / 🔴, not numeric scores — the point is to surface tradeoffs, not produce false precision.

   - **Explainability.** Can a non-PM in the company explain it in one sentence? Engineering, sales, support, the CEO. If half would say "uhh," that's 🔴.
   - **Adoption + retention coverage.** Does it capture *both* new users showing up *and* existing users coming back? MAU does — it's a rolling 30-day window that mechanically combines both. "Total signups" only captures adoption. "Day-30 retention of a single cohort" only captures retention. Revenue captures neither unless monetization is tight.
   - **Leading vs. lagging.** Does it move when the product is working, or only quarters later? Revenue is almost always lagging — by the time it moves, the bet has already been made. Behavioral metrics are usually leading.
   - **Gameability.** Can the team hit the number without serving users better? DAU can be gamed by spam notifications. MAU with N actions is harder. Revenue is hardest to game directly (which is also why it's so lagging).
   - **Strategic match.** If the metric moved 20% up, would you actually believe the strategic bet is working? If the answer is "kind of, depends," the metric isn't sharp enough.

4. **Check the MAU dismissal honestly.** MAU often gets reflexively dismissed as "vanity." For many products it is — but for many others it's the right answer. MAU mechanically combines new-user acquisition and existing-user retention into one universally explainable number. If the strategic bet is "more people using the product more often," MAU is not vanity, it's correct. The default dismissal is itself a failure mode. MAU is the right call when: (a) the product is consumer or SaaS where breadth matters, (b) revenue is far enough downstream that it lags by quarters, (c) the org needs one number and a composite would fracture alignment.

5. **Check the revenue trap.** Revenue / ARR is tempting because it "sounds strategic." It's almost always:
   - Lagging — moves quarters after the product change
   - Multi-attributed — pricing, sales, marketing all move it, so the product can't claim or disclaim it cleanly
   - Hard to use as a daily/weekly decision tool

   Pick revenue as the North Star when: the product is already monetizing meaningfully, user-value-to-revenue conversion is tight (e.g., transactional marketplaces where GMV = product success), or the org is past PMF and explicitly optimizing the business. Don't use it pre-PMF, or when revenue is currently being driven by sales motions rather than the product.

6. **Check the composite trap.** "North Star = 0.4 × MAU + 0.3 × retention + 0.3 × NPS" reads as sophisticated. It is *worse* than a single metric: nobody can move it intuitively, and you can't tell which component is broken when it drops. If the team needs to track multiple things — and they do — that's what inputs and guardrails are for. The North Star itself stays one number. See `decision-making/metrics.md` § "North Star metric."

7. **Pick one. Add inputs and guardrails.** The output is one metric (with precise segment + definition) plus 3–5 input metrics that drive it and 2–3 guardrail metrics that catch the gaming. A North Star without inputs and guardrails is incomplete — see `decision-making/metrics.md` § "North Star metric."

## Output structure

```
## Strategic bet (one sentence)
[What has to be true for the product to succeed. Restated from the user.]

## Candidate North Stars
| Metric | Explainability | Adoption + retention | Leading | Hard to game | Strategic match |
|---|---|---|---|---|---|
| [Metric A] | 🟢/🟡/🔴 | ... | ... | ... | ... |
| [Metric B] | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... |

## Recommendation
**[Metric name with precise definition: segment + threshold + window.]**

Why this one: [Two sentences. Cite the strategic bet.]
Why not [runner-up]: [One sentence on what it loses on.]
Known gap: [What this metric won't catch, and how the guardrails cover it.]

## Inputs (what drives the North Star)
1. [Input metric 1 — what it measures, how it ladders up]
2. [Input metric 2]
3. ...

## Guardrails (what must not go down while pushing North Star up)
1. [Guardrail 1 — and the gaming path it catches]
2. [Guardrail 2]

## Pre-committed targets
- Today: [value]
- Success at 6 months: [value]
- Failure threshold (forces a strategy rethink): [value]
```

## What good looks like

- The North Star is a single metric, named with a precise segment and window. "Monthly active users" is OK. "MAU among signed-in users on web + mobile who completed at least one core action in the 30-day window" is better.
- The recommendation explicitly names what it's giving up versus the runner-up. If the pick is MAU over revenue, the writeup says "revenue would catch monetization issues we won't see in MAU — that's a known gap, covered by guardrail X."
- The strategic bet is restated and the metric is tied to it. If the bet is "retention beats acquisition in this category," the North Star can't be top-of-funnel signups.
- Inputs and guardrails are named, not just the North Star. A North Star without these is a poster, not a tool.
- MAU is treated honestly — neither parroted nor reflexively dismissed. The skill picks it when it's right, walks past it when it isn't, and says which.

## Anti-patterns

- **Reaching for the sophisticated composite.** "Engagement score = 0.4 × A + 0.3 × B + 0.3 × C" is almost always worse than any of A, B, or C alone. The North Star is the rallying number, not the analytically optimal number.
- **Defaulting to revenue because it "sounds strategic."** Revenue is right for mature monetizing products and transactional marketplaces. It's wrong for most early or growth-stage products — too lagging, too multi-attributed, not a daily decision tool.
- **Dismissing MAU/DAU as "vanity" without checking.** For many consumer and SaaS products with breadth-driven strategies, MAU captures both adoption and retention in one number and is the right call. The reflexive dismissal is itself the failure mode.
- **Picking a North Star with no segment.** "MAU" is incomplete. "MAU on the iOS app" or "MAU among teams with ≥ 10 seats" is a metric. The segment is where the strategy lives.
- **Skipping inputs and guardrails.** A North Star without inputs (you can't move it directly) and guardrails (you'll game it) is incomplete. Don't sign off without both.
- **Treating the North Star as locked.** When the strategic bet changes, the North Star should change. If a metric has been the North Star for three years and the strategy has shifted twice, it's probably wrong now.

## Chain with pm-red-team

Once you've picked a North Star, run it through [`pm-red-team`](../pm-red-team/SKILL.md) before locking. The red team argues the opposite — that the runner-up was the right pick, or that the metric will be gamed in a way you didn't anticipate. The North Star is high-leverage; an adversarial second pass before lock-in is cheap.
