# Phase 6 — Product process for finding PMF

**Focus:** the explicit process a head of product (or founder, or new-product lead) implements so that new products have the highest possible chance of finding product-market fit. The process starts after an insight has been identified and ends when the team is either ready to test growth hypotheses or stop further development.

This file is the operational **spine**. The posture for *why* this is the right process lives in [`../decision-making/finding-pmf.md`](../decision-making/finding-pmf.md). The mechanics of each hypothesis component live in [`../decision-making/value-hypothesis.md`](../decision-making/value-hypothesis.md). The validation measurement and PMF metrics live in [`03-pre-pmf-validation.md`](03-pre-pmf-validation.md). This file connects them as one explicit process.

Built on the Lean Startup synthesis (Rachleff, Ries, Blank, Moore, Christensen, Marks, Fitzpatrick, Cook).

---

## The eight-step spine

Strip the methodology down to its operational sequence. Almost every successful tech company went through these steps (most by accident; this version is deliberate). Never skip a step. The *why* of each step matters as much as the *what*, because the temptation to skip a step always sounds reasonable in the moment.

### Step 1: Identify the inflection point

**What.** Name the technology, behavior, or regulatory change that just made this newly possible. If "nothing changed," the insight is suspect.

**Why this is step one.** Static markets are won by incumbents. The incumbent already has distribution, brand, capital, and customer relationships. A new entrant cannot beat them on execution alone, because the incumbent is by definition at least as good at execution. What a new entrant *can* beat the incumbent on is **change**. An inflection (LLMs that produce production code, smartphones with GPS, regulatory shifts that legalize a category, behavioral shifts like remote work) creates a window where the incumbent's existing advantages stop applying. That window is the only place a new tech company can compete asymmetrically.

**The skip cost.** Founders who skip this step end up pursuing right-and-consensus bets ("a better project management tool," "a faster CRM"). Anyone can pursue them, so the expected returns get arbitraged away. Founders who can't name their inflection are usually competing on execution in a known frame, which is the worst place to compete from in tech.

### Step 2: Articulate the value hypothesis

**What.** Write *what / who / how* on one line: *"For [specific desperate who], we will build [specific what] grounded in [specific insight], monetized via [specific how]."* Surface the *leap of faith* separately, on its own line, as the one belief that must be true.

**Why this is step two.** A hypothesis you can't write on one line is a hypothesis you can't test. Ambiguity inside a team protects bad ideas from criticism. The forcing function of compressing it to one line surfaces the parts the team has been hand-waving over. Putting the leap of faith on its own line is the discipline that prevents the single most common pre-PMF failure: an MVP that tests five assumptions at once and teaches you nothing when it fails, because you can't tell which assumption broke.

**The skip cost.** Teams that skip the articulation end up with multiple competing internal narratives about what the product is and who it's for. When experiments produce ambiguous results, the team can't agree on what to do next because they were never aligned on what was being tested. Every subsequent step suffers.

### Step 3: Identify the most desperate bowling pin

**What.** Pick the narrowest possible lead segment that is desperate (not just needy), targetable, and adjacent to other markets you could expand into later.

**Why narrow.** Desperate audiences are by definition narrow. Broad markets contain mostly non-desperate users who dilute the signal. A 60% activation rate across a broad market might be 90% for a tiny sub-segment and 10% for the rest. Aggregate metrics on a heterogeneous cohort produce wrong decisions about what to build next. The narrower the segment, the fewer features it needs to be a complete product, the easier it is to dominate, and the faster you learn.

**Why desperate, not needy.** Need produces interest. Desperation produces customers. Many products solve real needs for real users and still fail because the users were never desperate. The behavioral signature of desperation (paid for a workaround, hired a consultant, built a janky internal version) is observable. The attitudinal signature of need ("yeah, that'd be nice") is not actionable. Desperation is what carries a product across the chasm; need does not.

**Why adjacency matters.** Your post-PMF growth path runs through adjacent markets. If your lead pin has no plausible adjacencies, you may win the pin and have nowhere to expand. The adjacencies don't need to be sized or named in advance; they just need to plausibly exist.

**The skip cost.** Hedging on segments (running three lead pins in parallel because you can't decide) is the single most common pre-PMF failure. Each segment requires its own iteration cycle. Three in parallel means each cycle is a third as fast. Pick one.

### Step 4: Test the concept

**What.** Cheapest, fastest validation: smoke test, explainer video, Kickstarter pre-orders, concierge experiment, follow-me-home observation. Days to set up. Skip directly to step 5 if the MVP can be built in one or two months.

**Why before building.** Build cycles are the most expensive way to learn. A concept test costs days; an MVP costs months. If no one is interested at the concept level, the implementation can't fix that. The point of step 4 is to falsify the cheapest version of the hypothesis before committing to the expensive version.

**Why behavioral signals, not surveys.** Intent is unreliable. Survey questions like "would you use this?" produce socially polite answers that don't correlate with purchase behavior. The reliable concept tests (smoke test with a checkout button, Kickstarter pre-orders, explainer-video click-through, concierge experiments) all require an *action*, not just an opinion. Action signals are an order of magnitude more reliable than intent signals.

**The skip cost.** Founders who skip the concept test and go straight to MVP often spend three to six months building a product nobody wanted, and only learn it from the MVP failure. A two-day concept test would have told them the same thing.

### Step 5: Validate the implementation

**What.** A design sprint (week-long prototype plus customer test with 5-10 named users) tests whether the specific implementation produces *desperation*. The signals are "when can I have it?" and "I have been trying to build this myself." Use the five-whys when prospects object; seek the objection, don't overcome it.

**Why the design sprint specifically.** The design sprint is a high-fidelity test bounded by a week so the cost is contained. It tests desperation (not curiosity, not interest) by putting a prototype in front of named users and observing whether they ask "when can I have this?" The week-bounded format also forces the team to make hard tradeoffs about scope before committing engineering cycles. If the team can't agree on the prototype scope in a week, they don't have a hypothesis they can test.

**Why five-whys instead of overcoming objections.** The goal of step 5 is to learn which audience to pivot to, not to convince this audience to buy. When a prospect objects, the temptation is to add the feature they asked for and try to close them. That move turns the validation pass into a sales call and obscures the real signal. The five-whys keeps the test honest: each "why?" peels back a layer of polite cover until the team learns whether the right audience would be a different segment entirely.

**The skip cost.** Teams that skip step 5 often build MVPs that work technically but fail to produce desperation. The MVP teaches them the same thing the design sprint would have, but weeks later and at much higher cost.

### Step 6: Measure the behavioral signal

**What.** Once a real MVP is in customers' hands, measure word of mouth and retention. For consumer products, exponential organic growth in users or revenue. For B2B, sales yield approaching one (gross margin per non-founder rep divided by fully-loaded cost per rep).

**Why behavior beats intent.** Step 6 is the move from belief to evidence. NPS, surveys, "would you be disappointed?" tests, and similar instruments measure opinion. Word of mouth, retention, organic growth, and sales yield measure action. Opinion lies (people don't want to hurt the founder's feelings). Action doesn't. Behavioral signals are the only reliable proof that PMF is happening.

**Why these specific metrics.** Organic growth is ungameable. You can game LTV-to-CAC ratios, viral coefficients, signup counts, and engagement scores. You cannot game organic growth on a clean baseline. Sales yield captures real economic substitution: a non-founder rep generating more gross margin than the rep's fully-loaded cost can only happen if prospects are reaching out and asking for the product. Founders don't count toward sales yield because a founder can sell through sheer personality.

**The skip cost.** Teams that measure intent (Sean Ellis "very disappointed" surveys, NPS, signup counts) often conclude they have PMF when they don't, then raise growth capital and watch growth fail to retain as the underlying value gap surfaces.

### Step 7: Confirm economic sustainability

**What.** Sales yield greater than one, or organic growth compounding consistently month over month, ungamed by referral mechanics or paid acquisition. The inflection at sales yield equals one is the proof of PMF in enterprise; consumer PMF is proved by accelerating organic growth on a clean baseline.

**Why sustainability matters.** PMF without sustainable unit economics is not PMF. Growth on top of broken economics burns capital at scale and produces a forced pivot in Series B or C, when team capacity and political surface area are highest. The inflection at sales yield equals one is structural: below one, you need a founder in the room to sell every deal; above one, the product is being pulled out of your hands and the sales motion compounds.

**Why ungamed organic growth.** Referral programs, paid acquisition, and viral coefficients all inflate growth numbers without proving value. The clean version is the question: if you turn off referral incentives and paid acquisition tomorrow, does growth continue? If yes, the signal is real. If growth collapses, what looked like PMF was a growth experiment running on top of an unvalidated value hypothesis.

**The skip cost.** Founders who skip step 7 and go to scale on validated value-but-broken-economics raise a round, scale, and then face the structural problem that sustainable growth requires either price increases (which damage the value proposition) or cost cuts (which damage the product). The sequencing failure compounds because it happens after team and capital are committed.

### Step 8: Only then scale

**What.** Switch from value-hypothesis mode to growth-hypothesis mode. Different organization, different metrics, different culture. This is when execution starts to matter again.

**Why scaling before this point is dangerous.** Growth amplifies whatever exists. If value is shallow, growth amplifies churn. If targeting is unclear, growth amplifies acquisition waste. If sustainability is unproven, growth amplifies the burn rate. The most common pre-PMF mistake is to scale prematurely because growth feels like progress. It isn't; it's risk amplification on an untested foundation.

**Why the organization design changes.** Learning culture and execution culture optimize for opposite things. Learning culture rewards killing bad ideas fast, intellectual honesty about weak signals, and detaching ego from the product. Execution culture rewards hitting predefined targets, operational efficiency, and protecting what's been committed to. The same team cannot do both well at the same time. Step 8 is the explicit handoff from one mode to the other, and the moment when the kinds of metrics, hires, and processes the company invests in change deliberately.

**The skip cost.** Teams that scale before completing steps 6 and 7 frequently look successful for one round (the growth metrics show momentum) and then collapse in the next round when the growth fails to convert to durable revenue. The cleanest version of this failure: a growth-stage company raises a large round, scales the sales team and the marketing budget, and watches CAC payback periods balloon as the value hypothesis turns out not to have been validated.

---

The discipline is to never skip a step. The temptation when something is working is to leap to scale (skipping steps 6 and 7). The temptation when something is not working is to add features (skipping the pivot of the *who* in steps 3 and 5). Both end the same way: a company built on a foundation that has not been pressure-tested.

---

## The counterintuitive doctrine

Stated as a list of principles the process enforces. None of them sound shocking individually. Taken together they describe a methodology that is roughly the inverse of conventional product playbooks.

1. **Do not change the *what*. Change the *who*.** When experiments fail, pivot the audience. Hold the insight constant.
2. **Start with early adopters, not the early majority.** The majority demands references you don't have yet. Build a beachhead with early adopters first.
3. **Build to learn, not to execute.** Pre-PMF, optimize for rate of learning. Post-PMF, optimize for execution at scale.
4. **Do things that do not scale to accelerate insight.** Hand-deliver. Pre-fill data manually. Call every customer personally. Each non-scalable act buys learning at the highest possible fidelity.
5. **Desperation is more important than features.** Adding features does not create desperation. If the audience is needy but not desperate, change the audience.
6. **Revenue is signal, not finance.** Revenue from real customers (not from friends, not from grant money) is the most reliable proof of desperation. Start charging early. Free MVPs validate nothing about willingness to pay.
7. **Sales yield greater than one proves enterprise PMF.** A non-founder rep generating more gross margin than the rep's fully-loaded cost. Founders do not count toward this metric because a founder can sell through personality alone.
8. **Exponential organic growth proves consumer PMF.** Ungameable. Cannot be bought, cannot be referral-incentivized into existence. The signal that the product is selling itself.
9. **Platforms are for growth, not for discovery.** Pre-PMF, do not build a platform. Build the smallest product that tests the leap of faith. Platforms come post-PMF.
10. **Savor surprises.** When an experiment produces unexpected positive signal on a dimension you didn't design for, drop everything and double down. The market is telling you something you didn't know.

---

## Built to learn vs. built to execute

The organizational implication of treating PMF as a discovery problem. The pre-PMF team is structured to learn, not to deliver against a plan.

| Culture | Optimizes for | When right | When wrong |
|---|---|---|---|
| **Learning culture** | Rate of learning, falsifiable experiments, killing bad ideas fast, intellectual honesty about weak signals, detaching ego from the product | Pre-PMF, any new bet, internal product incubation | Post-PMF, where scale demands predictable execution |
| **Execution culture** | Predictability, operational efficiency, hitting predefined targets, process discipline, scaling systems | Post-PMF, where the answer is known and the question is "how do we deliver it reliably?" | Pre-PMF, where execution culture locks the team into the wrong direction, builds emotional commitment to a flawed strategy, and rewards hitting fake metrics over discovering truth |

The doctrine: **OKRs are wrong before PMF.** OKRs are a planning tool for known systems. Pre-PMF, the system is unknown. Setting a Q3 OKR for "10,000 active users" is a fake target. You have no basis for the number, and hitting (or missing) it tells you nothing about whether you're learning.

Inside a large company, this is the hardest part. Large companies have established execution cultures. Launching a new product inside one requires actively protecting the new product's learning culture from the existing execution culture. The instinct of the broader organization will be to measure the new product on execution metrics (velocity, ships per quarter, OKR completion). That instinct kills new products. The discipline is to insist on different metrics for the pre-PMF team: experiments run, hypotheses falsified, surprises captured, pivots executed.

---

## Financing milestones mapped to PMF stages

The financing system rewards different milestones at each stage. Knowing what each round actually funds prevents the common failure of raising for the wrong stage.

| Round | What you should have | What it funds |
|---|---|---|
| **Pre-Seed** | An insight, an authentic team, ideally some early concept validation (smoke test, Kickstarter, concierge experiment) | Discovering the value hypothesis. Investors are betting on the founder and the insight. |
| **Seed** | Concept validation plus implementation validation. Behavioral signal that desperate audiences exist for the proposed implementation. | Building an MVP that tests the leap of faith with real customers. |
| **Series A** | Behavioral signal from a real MVP. Word of mouth beginning. Sales yield approaching one (enterprise) or organic growth starting to compound (consumer). | Validating or invalidating PMF through the MVP cycle. |
| **Series B** | Validated PMF. Sales yield meaningfully greater than one and accelerating, or exponential organic growth for several quarters. | The **growth hypothesis**: whole product, next bowling pin, scaling sales force, brand investment. Execution starts to matter again. |
| **Series C** | Proven growth hypothesis at scale in the first market. Ready to expand into adjacent markets, geographies, or product lines. | Each expansion is its own internal PMF exercise within the new pin. |

The deeper rule: **proof of value, not proof of growth, attracts the best investors.** Many funds conflate the two. The best ones do not. A validated value hypothesis raises growth capital easily. Growth without validated value raises easily for one round, then struggles as growth fails to retain.

A note on incentives. Most accelerators and growth-stage funds are calibrated to optimize for growth-first, because growth metrics are easier to put in the next fundraising deck. That works for some founders. It is not the path of this process. Founders following this process should expect some financings to be harder and some valuations to be lower than peers who chose growth-first. The compounding payoff is durability through the next downturn.

---

## When this process applies inside a large company

The same eight-step spine applies inside an established company launching a new product (not a feature). The same counterintuitive doctrine applies. The same milestones apply, with internal capital allocation playing the role of external rounds.

Two specific challenges inside a large company:

1. **Brand-damage objections.** Internal stakeholders resist concept tests and rough MVPs because they fear damaging the parent brand. The discipline: sandbox the new product under a sub-brand (or no brand) so experiments do not implicate the parent. Concept tests and rough MVPs ship under names the parent organization can disown if needed.

2. **Cultural pressure to execute.** The existing organization measures on velocity and OKR completion. The new product team needs different metrics. The head of product's job is to insist on those metrics, defend them at every quarterly review, and resist re-allocation of the team to execution work until PMF is confirmed.

If the head of product cannot get the organization to accept different metrics for the pre-PMF team, the new product almost certainly dies. Not because the team is bad. Because they are being measured on the wrong thing.

---

## Decision checklist for the head of product

Before signing off on a new-product team's quarterly plan:

1. Has the team named the **inflection point** underneath the insight? If no, the bet is right-and-consensus and the expected return is low.
2. Has the team isolated the **leap of faith** on its own line, separate from the value hypothesis? If no, the MVP will test too many things at once.
3. Has the team picked **one lead pin** (not three)? If multiple, the team is hedging and will not learn fast enough.
4. Has the team chosen the **smallest validation step appropriate to the stage** (concept test, design sprint, or MVP)? If they are skipping to MVP without earlier validation, they may be wasting build cycles.
5. Has the team picked a **behavioral metric**, not an intent metric, as the PMF proof? If they are using NPS, "would you be disappointed?", or signup count as the proof, the bar is too soft.
6. Has the team explicitly named what they would consider **falsification of the leap of faith**? If no, the experiment is not designed.
7. Is the team **protected from execution-culture metrics** until PMF is confirmed? If they are being graded on velocity or OKR completion, the wrong things are being optimized.

If three of these are weak, the plan is not ready to fund.

---

## When this phase is done

You have either:

- Confirmed PMF (sales yield > 1 with acceleration in B2B, or exponential organic growth in consumer, plus visible word of mouth), and you move to growth-hypothesis mode and the post-PMF playbook in [`04-post-pmf-growth.md`](04-post-pmf-growth.md), or
- Falsified the leap of faith and either pivoted the *who* (most common, highest success rate), pivoted the *how* (less common), or restarted the *what* (rare, low success rate), and re-entered this process from step 2 with the revised hypothesis.

If the team is stuck at step 5 or 6 for more than two pivots without learning, it is worth pausing the process to revisit whether the insight (the *what*) is the issue rather than the audience (the *who*). Restarts are expensive but sometimes necessary.

The probability of success is a function of the quality of the insight and the rate of learning. The process improves the rate of learning. The insight has to come from elsewhere.
