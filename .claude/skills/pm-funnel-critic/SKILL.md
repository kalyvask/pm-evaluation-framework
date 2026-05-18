---
name: pm-funnel-critic
description: Critique an activation funnel, conversion funnel, trial-to-paid mechanic, or growth dashboard against the repo's activation and conversion content. Use when a PM has funnel data, an onboarding flow, a paywall design, or a growth dashboard and wants the funnel layer pressure-tested — drop-off drivers, the binding stage, whether the right model (Enterprise vs PLG) is being applied, whether the activation event is real or vanity. Distinct from pm-metrics-critic (metric layer) and pm-design-critic (surface layer); this skill sits between them at the funnel layer. Returns the three load-bearing funnel holes with specific experiments and kill thresholds.
---

# PM funnel critic

Runs a funnel-layer review on an activation or conversion experience. The existing skills cover adjacent layers: `pm-metrics-critic` catches metric-level failures (vanity metrics, gaming, segment masking); `pm-design-critic` catches surface-level failures (defaults, friction placement, choice architecture). This skill sits between them — at the layer where a sequence of metrics combines with a sequence of design moments into a funnel that either works or doesn't.

The job is to name the binding stage, name the drop-off driver, and propose specific experiments that would close the largest gap, not the easiest one.

## When to use

Use this when:
- A PM shares an onboarding flow, a paywall design, a trial structure, or a growth dashboard
- A team is debating which stage of the funnel to optimize next
- A PM has activation or conversion numbers that "look fine" and wants to know whether they're top-decile or median
- A team is choosing between Enterprise (sales-led) and PLG (product-led) conversion mechanics and wants the trade-off named
- A team is preparing a growth-related PRD or strategy memo and wants the funnel logic stress-tested before circulation

Don't use this when:
- The strategy isn't framed yet — route to `pm-decision-coach` or `decision-making/problem-framing.md` first
- The artifact is purely metric-layer (a KPI debate with no funnel structure) — use `pm-metrics-critic`
- The artifact is purely surface-layer (an onboarding mockup with no funnel data) — use `pm-design-critic`
- The product has no funnel yet (pre-PMF, no users) — the right framework is `pm-value-hypothesis-tester`, not this

## How to apply

### 1. Identify the model

Before critiquing the funnel, name which model applies: **Enterprise (sales-led)** or **PLG (product-led)**. Reference `decision-making/user-vs-chooser.md` if it's unclear from context. The model determines which benchmarks to apply and which drop-off drivers to look for.

Most products under $50K per year are PLG. Most products over $1M are Enterprise. The middle is where products often try to run both — usually executing each worse than a focused single-model competitor.

### 2. Map the funnel stages

List the stages explicitly. For PLG: *Visitor → Sign-up → Activation → 30-Day Retention → Paid → Expansion*. For Enterprise: *Visitor → Lead → MQL → SQL → Opportunity → Won → Renew → Expansion*.

For each stage, the user should be able to name three numbers: the current conversion rate, the average benchmark for the model, and the top-decile benchmark. If they can't, the funnel isn't instrumented enough to critique — surface that first and stop.

### 3. Find the binding stage

The binding stage is the one where the conversion rate is most below benchmark, **weighted by where it sits in the multiplicative chain**. A 10-point gap at activation matters more than a 10-point gap at expansion because everything downstream multiplies through it.

Most teams optimize the stage they understand best, not the stage that's binding. The skill's job is to name the binding stage explicitly, even when it's the unfashionable one.

### 4. Name the drop-off driver

For each underperforming stage, name the driver from the catalogue in `decision-making/conversion.md`. The common ones:

- **Visitor → Sign-up:** Messaging mismatch (Enterprise) or UX onboarding friction (PLG)
- **Sign-up → Activation:** Time to aha moment, setup wall, empty state, no first success
- **Activation → Retention:** Lack of work habit, missing collaboration moment, no external trigger
- **Trial → Paid:** Paywall positioning; calendar-triggered when usage-triggered would convert better
- **Expansion:** Missing collaboration affordance, missing usage-based prompts, sales-motion mismatch

Naming the driver makes the experiment concrete. *"Improve activation"* is not an experiment. *"Replace the multi-screen onboarding with a single tooltip on the primary action"* is.

### 5. Find the three load-bearing funnel holes

Same discipline as `pm-red-team` and `pm-design-critic`: quality over quantity. The first pass usually catches obvious drop-offs. The job is the three holes that, if surfaced in a growth review, would force a re-think.

Useful filters:

- **Which stage is below benchmark and binding?** The intersection matters; one without the other is noise.
- **Where is the team optimizing the wrong stage?** Usually the one they understand best, not the binding one.
- **Where is the wrong model being applied?** PLG benchmarks on an Enterprise product, or vice versa.
- **Where is the activation event a vanity metric?** Check the retention split between activated and non-activated. If they retain similarly, the activation event isn't load-bearing.
- **Where is the trial mechanic wrong for the product?** Calendar-triggered when usage-triggered would convert better; long when short would force decisions.

### 6. Propose specific experiments

For each hole, propose the experiment that would close it. Specific, measurable, with a falsifying threshold.

Not *"improve activation."* Instead: *"Replace the multi-screen onboarding with a single tooltip on the primary action. Hypothesis: TTV drops from 9 minutes to under 4 minutes; activation rate moves from 28 percent to 40 percent. Kill if activation moves less than 5 percentage points after 2,000 new signups."*

## Output structure

```
## TL;DR
[One paragraph honest take. Is this funnel working? Yes / partially / no — and the one stage that most determines the answer.]

## Model and stages
[Which model (Enterprise or PLG), and the funnel stages mapped to current rates and benchmark rates. If unmeasured, flag here and stop.]

## The binding stage
[The stage where conversion is most below benchmark, weighted by position in the chain. One paragraph on why this stage matters more than the others.]

## Three load-bearing funnel holes
For each (max three; quality > quantity):

**[Hole 1 — short title]**
- *The stage:* [which funnel stage]
- *The driver:* [from the conversion.md driver catalogue]
- *Why it matters:* [the compounding effect on downstream stages]
- *Experiment:* [specific, measurable, with a kill threshold]

## Where the team is optimizing the wrong stage
[Optional. If the team's current focus is not the binding stage, name it directly. One paragraph.]

## What I'd change before the next growth review
[The 1–3 concrete actions. Each one must be a specific experiment with a measurable hypothesis. "Run the role-based onboarding split test" beats "improve onboarding."]

## Verdict
[Funnel is working / fix the binding stage / wrong model applied / under-instrumented, with one sentence of reasoning.]
```

## What good looks like

- **Names the binding stage, not the obvious one.** The job isn't to point at the worst-performing number; it's to point at the stage whose movement would move U_R30 the most.
- **Cites benchmarks.** Average vs top-decile for the relevant model. Vague *"this is low"* isn't a critique.
- **Distinguishes model failure from stage failure.** A PLG product with Enterprise retention benchmarks is solving the wrong problem. A PLG product with poor activation is solving the right problem badly. Different fixes.
- **Proposes experiments with kill thresholds.** *"Run the test"* without a falsifying threshold is theater. *"Run the test; kill if activation moves less than 5pp after 2,000 signups"* is an experiment.
- **Cites the repo.** Point at `decision-making/activation.md` § [gate], `decision-making/conversion.md` § [driver], `decision-making/user-vs-chooser.md` § [tier] so the reviewer can deepen the read.

## Anti-patterns

- **Critiquing the obvious drop-off.** Of course visitor-to-signup is 98 percent attrition in PLG. That's industry baseline. The question is whether it's below the model's benchmark, weighted by where it sits in the chain.
- **Demanding metric improvements without stage discipline.** *"Improve retention"* is not a critique. *"Activation event is a vanity metric; the retention split between activated and non-activated is 22% vs 18%; the event needs redefinition before retention is meaningful"* is.
- **Applying the wrong benchmark.** Comparing your PLG product to Enterprise retention. Comparing your dev tool to consumer SaaS conversion. Use the right reference class.
- **Vague experiments.** *"Test new onboarding"* isn't an experiment. *"Test single-tooltip onboarding vs current multi-screen; measure TTV; kill if activation moves less than 5pp after 2,000 signups"* is.
- **Treating expansion and acquisition as the same problem.** They aren't. In mature SaaS, expansion is ~52 percent of revenue, and the mechanics are different.
- **Forgetting that the funnel is multiplicative.** A 10-point gain at one stage compounds through every downstream stage. The right stage to optimize is rarely the worst one in isolation.

## Chain with other skills

- **`pm-metrics-critic`** *before* this skill if the user is unsure whether their metrics are vanity. Funnel critique on vanity metrics produces vanity recommendations.
- **`pm-design-critic`** *after* this skill once the binding stage is identified — to critique the specific surface (onboarding screens, paywall design, signup flow) that lives at that stage.
- **`pm-red-team`** on the output of this skill if it's going into a high-stakes growth review, fundraising deck, or board memo. Funnel logic gets weaponized fast; the red-team pass catches the parts that won't survive.

## How to invoke

Common invocation patterns:

- *"Use pm-funnel-critic on this onboarding flow."*
- *"Our activation rate is 28 percent. Critique this funnel."*
- *"Should we run PLG or Enterprise conversion mechanics? Use pm-funnel-critic on our current setup."*
- *"Run pm-funnel-critic on the trial-to-paid section of this growth memo."*

If the user invokes this skill without funnel data or a funnel artifact, respond: *"This skill works on funnel-layer artifacts (an onboarding flow, conversion dashboard, paywall design, trial structure). The artifact you've shared doesn't have funnel structure I can grab. Did you mean `pm-metrics-critic` for the metrics, or `pm-design-critic` for the surface?"*
