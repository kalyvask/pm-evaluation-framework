# Conversion

Conversion is the discipline of getting users from one stage of the funnel to the next: visitor to sign-up, sign-up to trial, trial to paid, free to expanded paid, paid to renewed. Each stage has its own physics, its own benchmarks, and its own drop-off drivers. Treating *"conversion"* as one problem produces designs that solve none of them.

This file is the working-PM reference for the funnel-level conversion design problem. It pairs with `decision-making/activation.md` (early-funnel mechanics in depth) and `decision-making/user-vs-chooser.md` (the buyer-vs-user split that determines which conversion model applies).

---

## The unified growth equation

The simplest synthesis of the funnel. Total retained users at 30 days:

> **U_R30 = M · c_vis · c_tri · c_act · R_30 · (1 + Σ K^n)**

Where:

- **M** = reach (top-of-funnel volume)
- **c_vis** = visitor-to-interest conversion
- **c_tri** = trial / lead signup rate
- **c_act** = activation rate (the aha moment — see `decision-making/activation.md`)
- **R_30** = 30-day retention of activated users
- **K** = expansion factor (viral coefficient)

The equation is the structure, not the answer. Three implications worth internalizing:

1. **Conversion is multiplicative.** A 10 percent gain at three stages produces a ~33 percent gain in total. A 30 percent loss at one stage halves the funnel regardless of how good the rest is.
2. **The weakest stage is the binding constraint.** Optimizing a stage that isn't the binding one produces little movement in U_R30. Most growth teams optimize the stage they understand best, not the stage that's binding.
3. **K compounds geometrically.** When K is meaningfully above zero, every cohort produces additional cohorts, and the geometric series in the equation grows. Getting K from 0.1 to 0.3 has more lifetime impact than getting c_act from 25 percent to 40 percent.

---

## Two conversion models: Enterprise (sales-led) and PLG (product-led)

The same equation applies to both, but the stages and the drop-off drivers look different. The user-vs-chooser tier (see `decision-making/user-vs-chooser.md`) usually determines which model applies. Under-$50K is typically PLG. Over-$1M is typically Enterprise. The middle is where products often try to run both — usually with mediocre execution of each.

### Enterprise funnel benchmarks

| Stage | Average | Top decile | Drop-off driver |
|---|---|---|---|
| Visitor to Lead | 0.7–1.4% | 3.0%+ | Messaging mismatch |
| Lead to MQL | 31–34% | 45%+ | BDR/SDR response time |
| MQL to SQL | 13–21% | 30%+ | Qualification friction |
| Opportunity to Won | 19–21% | 31%+ | Procurement / legal lag |

### PLG funnel benchmarks

| Stage | Average | Top decile | Drop-off driver |
|---|---|---|---|
| Visitor to Sign-up | 2.0–5.0% | 10.0%+ | UX onboarding friction |
| Activation Rate | 25–40% | 60%+ | Time to aha moment |
| Free to Paid (Trial) | 15–25% | 40%+ | Paywall positioning |
| 30-Day Retention | 10–30% | 45%+ | Lack of work habit |

The benchmarks tell you whether each stage is at industry baseline or top-decile. The drivers tell you where to look when a stage underperforms.

Note that **the Enterprise model is sales-bottlenecked** — the drivers are people-and-process (response time, qualification, procurement). **The PLG model is design-bottlenecked** — the drivers are product surface (friction, TTV, paywall). The interventions are different. Optimizing BDR response time in a PLG funnel is wasted effort; optimizing onboarding UX in an Enterprise funnel is too.

---

## Activation as the conversion gate

For PLG, **activation is the single most consequential variable** in the conversion chain. It's covered in depth in `decision-making/activation.md`. The summary:

- Activation Rate is the strongest predictor of 30-day retention.
- TTV under four minutes is the bar.
- The aha moment is product-specific; generic playbooks don't transfer.

For Enterprise, the analog is the **POC success rate** — the proof-of-concept demonstration that produces a buyer-level outcome within the first 30 days. A POC that demonstrates measurable value early converts at multiples of one that does not. The Enterprise version of the activation gate is the *implementation gap* — the first 30 days after contract signing where the customer either gets to value or starts the slow drift toward year-end non-renewal.

---

## Trial-to-paid mechanics

The trial design is its own conversion problem. Three key choices.

### Trigger type

- **Calendar-triggered.** Trial ends after N days. Simple. Treats every user the same regardless of where they are in their evaluation.
- **Usage-triggered.** Trial ends after N actions, projects, integrations, or other usage thresholds. Catches the user when they've experienced value.

**Usage-triggered conversions convert at roughly 3.2x the rate of calendar-triggered ones** in the same product. The mechanic works because it places the paywall at the moment of demonstrated value, not at the moment of arbitrary deadline. Default to usage-triggered wherever the product analytics can support it.

### Trial length

- **Short trial (7–14 days).** Forces decision. Compresses TTV implicitly because the user has limited time to find value. Right for products where TTV can be under a few minutes.
- **Long trial (30 days).** Allows for habit formation. Right for products where the value compounds over weeks (project tools, productivity suites, planning tools).

The right answer depends on how long it actually takes a representative user to reach the aha moment, plus a buffer. Trial length should be set from data on real user behavior, not from competitor benchmarks.

### Paywall positioning

- **Feature-gated.** Free users get a subset of features; paid users get more. Risk: free users don't experience the paid value, so the gate doesn't tee up conversion.
- **Usage-gated.** Free users get up to N actions; paid users get unlimited. Better — the user experiences value before hitting the gate.
- **Time-gated.** Free trial, then paywall. Cleanest if trial mechanics are designed well.

Hybrid models (usage-gated trial with feature-gated free tier) are common in PLG products that need both top-of-funnel reach and clear paid value.

---

## The 30-day retention cliff

R_30 is the most-misread metric in the funnel. Two distinct meanings depending on the model:

- **Enterprise R_30: 60–90 percent.** Looks great. Mostly artificial — driven by contract obligation, not product value. The real test is renewal at month 12, not retention at day 30.
- **PLG R_30: 10–40 percent.** Looks brutal. Honest. Represents true behavioral fit. Below 20 percent, customer acquisition cost will eventually outweigh lifetime value.

The implication: if you're benchmarking R_30 against Enterprise SaaS averages while running a PLG product, the numbers will look catastrophic. They're not — they're measuring something different. PLG retention needs PLG benchmarks, and the bar for *healthy* is much lower in absolute terms.

The same metric can be a signal of strength or weakness depending on which model you're in. Picking the wrong reference class is one of the most common funnel-diagnosis mistakes.

---

## Expansion as the primary growth lever

In mature SaaS in 2025, **roughly 52 percent of new revenue comes from expansion** of existing accounts, not new logo acquisition. The K factor compounds in the equation above; new-logo conversion does not.

This shifts what conversion design should optimize:

- **Seat expansion.** Mechanisms that turn a single-user adoption into a team adoption. Collaboration invites, shared workspaces, network notifications.
- **Tier expansion.** Mechanisms that turn a basic-tier user into a higher-tier user. Feature discovery, usage-based prompts, role-based recommendations.
- **Account expansion.** Mechanisms that turn one team's adoption into an organization-wide deployment. The wedge-to-wall pattern (see `decision-making/user-vs-chooser.md`).

For B2B SaaS, **a K of 0.1 to 0.4 is strong** and meaningfully reduces blended CAC. K > 1 is exponential and rare; chasing it is usually a distraction from the more achievable 0.2 to 0.4 zone.

---

## Average drop-off friction

Across PLG products, typical funnel attrition:

| Stage | Typical drop-off |
|---|---|
| Visitor → Sign-up / MQL | ~98% |
| Sign-up → Activation | ~65% |
| Activation → Retained (D30) | ~75% |
| Retained → Paid Upgrade | ~90% |

The compounding implication: for every 100,000 visitors, roughly 2,000 sign up, 700 activate, 175 retain at D30, and ~18 convert to paid. **Top-of-funnel volume has to be massive for PLG math to work**, which is why PLG products that lack a viral or content-driven acquisition channel rarely scale.

This also explains why expansion (K) matters disproportionately in PLG — it's the only stage of the funnel that *adds* to the equation rather than subtracting from it.

---

## Anti-patterns

- **Treating the funnel as one stage.** Each stage has its own drop-off driver and its own design fix. Aggregate "conversion" is a vanity metric.
- **Optimizing the wrong stage.** Most growth teams optimize the stage they understand best, not the stage that's binding. The binding stage is usually two stages further down than the team thinks.
- **Comparing PLG retention to Enterprise retention.** Different physics. Use the right benchmark for the model.
- **Optimizing visitor-to-signup when activation is broken.** More signups into a broken activation experience just increases the number of churned users.
- **Treating expansion as a sales motion when it should be a product motion.** In PLG, expansion is a product surface (in-app prompts, sharing affordances). In Enterprise, it's account management. Mixing the two produces neither.
- **Calendar-based trial endings when usage-based would convert ~3x better.** Default to usage-triggered wherever the analytics support it.
- **Importing a competitor's trial length without checking your TTV.** A 14-day trial in a product whose TTV is 30 minutes works. The same length in a product whose TTV is two weeks is a kill.

---

## Diagnostic checklist

Before claiming the funnel is optimized:

1. **Which model applies?** Enterprise (sales-bottlenecked) or PLG (design-bottlenecked)?
2. **What's the binding stage?** Where in the funnel is conversion compounding worst, weighted by position in the chain?
3. **Are you using the right benchmark?** PLG retention against PLG numbers, Enterprise against Enterprise.
4. **Is activation instrumented?** TTV, activation rate, retention split between activated and non-activated.
5. **Is the trial trigger right for the product?** Calendar vs usage. Usage triggers convert at ~3x in most products.
6. **Is K being measured and optimized?** Expansion factor matters more than new-logo conversion in mature SaaS.
7. **Are the drop-off drivers being addressed at the right level?** Sales-side drivers need sales fixes; design-side drivers need design fixes.

If two of these are vague, the funnel isn't a system — it's a collection of metrics waiting for someone to do the actual diagnosis.

See also `decision-making/activation.md` for the early-funnel mechanics in depth, `decision-making/metrics.md` for the metric-layer discipline behind these numbers, and `decision-making/user-vs-chooser.md` for the buyer-tier framework that drives the Enterprise-vs-PLG choice.
