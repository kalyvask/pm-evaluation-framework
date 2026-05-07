# Metrics

What to measure, what not to measure, and how to know when your metrics are lying to you.

---

## Match metrics to strategy assumptions

The single biggest metrics mistake: tracking what's *easy to measure* instead of what *would falsify your strategy*.

Before locking a dashboard, list the load-bearing assumptions of the strategy. For each one, ask: *what metric, if it moved, would tell me this assumption is broken?*

That's the metric to track.

Examples:

| Strategic assumption | The metric that would falsify it |
|---|---|
| "Top-tier creators will adopt and drive smaller-creator imitation" | Adoption rate among the top-tier segment, specifically. Not aggregate adoption. |
| "Enterprise customers will switch from a competitor to us" | Switching events from named competitors. Not new sign-ups. |
| "Free-tier users will convert to paid at X%" | Free-to-paid conversion *at the planned conversion event*. Not aggregate revenue. |
| "Users will pay 2× more for the premium tier" | Conversion rate at the premium price point. Not ARPU. |

Aggregate metrics hide segment-level failures. Strategy-aligned metrics reveal them.

---

## North Star metric

A single metric that captures core user value delivered, that the entire org agrees on.

Properties of a good North Star:

- **Reflects user value, not internal effort.** "Reports created and shared" beats "API calls served."
- **Leading, not lagging.** Moves before revenue does.
- **Hard to game without serving users better.** If a team can hit the number by spamming, it's the wrong number.
- **Shared.** Same metric on every dashboard. If two teams optimize for different North Stars, you don't have one.

The North Star is not enough on its own. You also need:

- **Inputs** — the 3–5 metrics that drive the North Star
- **Guardrails** — metrics that should *not* go down (e.g. quality, cost-per-action, retention) while you push the North Star up

Without guardrails, teams optimize the North Star at the expense of things they don't measure. Quality erodes, costs balloon, the support queue overflows — and the North Star looks great.

---

## The growth equation

Growth = Reach × Conversion × Activation × Retention

Map the full funnel. Find the worst-performing stage. **That's where to invest.**

A common failure: spending on top-of-funnel acquisition when the leak is actually at activation. Doubling acquisition with broken activation gets you twice the wasted users.

A useful first-pass diagnosis: take a typical cohort of 1000 new sign-ups. How many reach *aha* in the first session? How many come back the next week? How many are still around after 30 days? That cascade tells you the leak.

---

## Funnels: AARRR (Pirate Metrics)

- **Acquisition** — how do users find you?
- **Activation** — first *aha* moment
- **Retention** — do they come back?
- **Referral** — do they tell others?
- **Revenue** — do they pay?

See `frameworks/04-post-pmf-growth.md` for the full treatment.

---

## HEART (for feature-level UX measurement)

- **Happiness** — how do users feel?
- **Engagement** — depth of usage
- **Adoption** — new users reaching key features
- **Retention** — repeat usage
- **Task success** — completion rate

Pick 2–3 dimensions per feature, not all five. Trying to track everything dilutes attention.

---

## Cohort retention

For each cohort of new users (by week, month, or campaign), plot retention over time.

- **Healthy product:** retention curve flattens to a stable base
- **Unhealthy product:** retention curve collapses to zero

Two specific reads to do every week:

- **Newest cohorts vs. older cohorts.** If new is worse, either the product is degrading or the user mix is degrading (often a sign of paid acquisition pulling in lower-quality users).
- **By acquisition source.** Organic almost always retains better than paid. If paid retention is so weak that LTV doesn't cover CAC, you're buying losses.

---

## Activation rate / time to value

Two paired metrics for first-experience health:

- **Activation rate** — % of new users who reach *aha* in their first session (or first N days)
- **Time to value** — median time from sign-up to *aha*

Define *aha* concretely. "Sent first message," "received first answer," "imported first dataset." Vague definitions ("engaged," "active," "saw value") produce vague metrics.

Bad activation kills good acquisition. Fix activation before scaling acquisition.

---

## Sean Ellis test

Survey current users: *"How would you feel if you could no longer use this product?"*

- Very disappointed
- Somewhat disappointed
- Not disappointed
- N/A

The "very disappointed" % is a directional PMF signal. ~40% is a commonly cited (though imperfect) threshold. Slice the response by segment — PMF often exists for a narrower segment than you assumed.

Most useful follow-up: *"What would you use as a replacement?"* The answers reveal the actual competitive set.

---

## LTV / CAC

The unit economics check.

- **LTV** — total revenue from a user over their lifetime, minus variable cost to serve
- **CAC** — fully-loaded cost to acquire (sales, marketing, onboarding, free-tier costs)

Rule of thumb: LTV ≥ 3 × CAC. CAC payback under 12–18 months in most software categories.

Common failure: optimizing CAC by channel without checking that cheap-CAC channels produce comparable LTV. They almost never do.

---

## Bundle effects in metrics

In multi-product companies, no feature stands alone. A new product's success is partially measured by what it does for *the bundle* — does it deepen the primary-account relationship, increase the share of wallet, lower churn on the primary product?

Conversely, a feature with strong standalone metrics can hurt bundle value if it attracts users who only want that one feature, never expand, and never become primary-account holders.

When measuring a new feature in a multi-product company, always include:

- Standalone metric (adoption, engagement, retention of the feature)
- Bundle metric (impact on primary-product retention, on share of wallet, on cross-product usage)

A feature with strong standalone numbers and negative bundle numbers is often a *worse* outcome than a feature with weaker standalone and positive bundle numbers.

---

## Working backwards from success metrics

Before launch, write down:

1. What's the metric this product/feature is supposed to move?
2. What's the value of that metric *today*?
3. What value would constitute success in 3, 6, 12 months?
4. What value would force us to kill it?

This forces explicit pre-commitment, which is the antidote to retroactive rationalization.

---

## Reading experiment results

A/B test results lie more often than people realize. Three failure modes show up repeatedly:

### 1. The aggregate is masking a segment-level disaster

A test ships, the headline metric moves +1.2%, the team declares a win. Six months later, retention among the strategically important segment is down. The aggregate hid it.

Default move: **before declaring a winner, slice by the strategically necessary segment.** If the test won in aggregate but lost (or didn't move) in the segment your strategy depends on, you don't have a winner. You have a tradeoff that needs a decision, not a deploy.

### 2. The result is real but the effect is too small to matter

A test runs, the variant beats control by +0.4% on a metric, the change is statistically significant, the team ships. Six months of similar +0.4% wins later, the product has 12 changes none of which matter individually and that collectively don't move the strategy.

Default move: **decide the minimum detectable effect that would justify shipping *before* you start the test.** "Stat sig" is necessary, not sufficient. A 0.4% lift on a non-strategic metric is noise dressed up as signal.

### 3. The novelty effect or the cohort effect

The variant looks great in week one, fades by week four. The team shipped in week two. Or: the test ran during an unusual cohort window (post-launch, holiday season, a marketing push) and won't replicate in steady state.

Default move: **run experiments long enough to see beyond the novelty window** (usually 2–4 weeks for habit-forming products), and validate that the cohort during the test reflects steady-state acquisition, not a temporary surge.

### Stress-tests for any experiment result

Before locking a launch decision on test data:

- **Did the test isolate the change you care about?** Or are there confounded variations (timing, marketing, other releases)?
- **Did the variant win on the strategic metric, or only on a proxy that's easier to move?**
- **Did the win replicate in the strategic segment, or only in aggregate?**
- **Is the lift large enough to matter on the strategy timeline, or is it a precision-engineered 0.4%?**
- **Was the test long enough to clear the novelty window?**
- **Are guardrail metrics (quality, support load, retention, costs) holding?**

Tests that pass these stress-tests are usable as launch decisions. Tests that don't are interesting; they're not yet decisional.

### Cohort comparisons in observational data

Experiments are the gold standard. When you can't run one — and many B2B and infrequent-event products genuinely can't — cohort comparisons are the next best, but they're easy to get wrong.

Three traps:

- **Self-selection.** Users who adopted feature X are systematically different from users who didn't. Comparing their retention is comparing two non-equivalent populations, not measuring the feature's effect.
- **Time confounds.** Cohorts from different months experienced different product versions, marketing motions, and macro conditions. A "cohorts are getting better" trend may just be "the market got better."
- **Survivorship.** Only the cohorts who stuck around show up in the analysis. The ones who churned are invisible, which makes the survivors look better than the average user.

Default move: when reading observational cohort data, name which of the three traps you're vulnerable to and how you've controlled for it. If you haven't, the data is directional, not decisional.

---

## When the metrics are lying

Three common failure modes:

### 1. Optimizing the wrong variable

Beautiful research, clean execution, wrong metric. Usually because the team picked the metric that was easy to move (e.g. *aggregate* engagement) when the strategically meaningful metric was harder to access (e.g. engagement *among the strategic segment*).

Fix: re-derive metrics from strategy. If the strategy depends on a specific segment, the metric must isolate that segment.

### 2. Goodhart's Law

"When a measure becomes a target, it ceases to be a good measure." Teams optimize the metric at the expense of the underlying goal. Examples: gaming an NPS prompt to surface only when the user just had a successful experience; counting *messages sent* and inflating by sending notifications; counting *active users* by changing the activity threshold.

Fix: pair every primary metric with guardrail metrics that catch the gaming. If active users is your North Star, monitor active users *who came back the next week* as a guardrail.

### 3. Strong NPS / engagement, weak business

A product can have unusually high NPS, strong engagement, and a great qualitative story — and still fail to find a sustainable business model. NPS measures love, not viability. Engagement measures usage, not willingness to pay.

If you only measure user love, you optimize for a product users love that doesn't make money. Pair user-love metrics with willingness-to-pay metrics, retention-after-price-increase metrics, and unit economics.

---

## Decision checklist

Before locking in a metrics dashboard:

1. Have we listed strategic assumptions and identified the metric that would falsify each?
2. Is there one North Star — same on every dashboard?
3. Are there guardrails to catch optimization-at-expense-of-other-things?
4. Are activation, retention, and unit economics all visible — not just acquisition?
5. For multi-product cos: are standalone *and* bundle metrics tracked?
6. For each major bet: is there a pre-committed kill criterion?

If two are missing, the metrics layer is incomplete.
