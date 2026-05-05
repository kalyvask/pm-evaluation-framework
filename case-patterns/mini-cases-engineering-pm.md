# Mini cases — PM/engineering tension

Two short patterns that show up often enough to deserve their own treatment.

---

## Mini case 1 — UXR demand vs. architectural constraint

### Setup (anonymized)

A team is launching a new code-management platform to replace a legacy system. Disagreement: should single-file sharing be in V1?

- **PM**: anchored to UXR signals. Users have asked for single-file sharing. Hard adoption targets depend on it.
- **Engineering Lead**: argues that the feature requires a backend hack that introduces systemic fragility, risks regression across the entire sharing system, and pushes against the intended repo-based mental model of the platform.

Tension: short-term adoption insurance vs. long-term system integrity.

### What good looks like

UXR signals are inputs, not mandates.

The relevant question is not *"do users want file sharing?"* — it's *"what job are users hiring file-sharing to do, and is there another way to fulfill it?"*

The answer here, on closer inspection: users want low-friction sharing of discrete work artifacts. A project-scoped share with a clean migration path could fulfill that job without the architectural hack.

UXR signals also need to be stress-tested:

- **Segment size** — what % of the adoption target is *blocked* (not just *prefers*) without it?
- **Switching cost** — would they actually walk away, or just complain?
- **Workaround analysis** — what are users using today? How painful is the workaround?

When a feature requires a hack, the right response is to validate whether the hack's blast radius is acceptable — not to treat UXR demand as the tiebreaker.

### Specific moves

1. **Re-frame the user job.** Discrete-artifact sharing, not file sharing per se. Project-scoped sharing may serve the job.

2. **Quantify both sides.**
   - PM: what % of adoption target is genuinely blocked vs. prefers? Define "blocked" testably.
   - Engineering: what's the blast radius of the hack? Is it contained and reversible, or does it couple to core access control?

3. **Run a spike.** A 1–2 day technical investigation. Prototype the hack. Quantify regression risk. If the spike confirms the hack is brittle, that's defensible data. If the spike shows narrower-than-expected blast radius, the V1 calculation changes.

4. **Run a concierge MVP.** Identify the specific users who flagged single-file sharing as a blocker. Walk them through the new platform. Reveal whether they're truly blocked or whether a good migration UX resolves the concern.

5. **If the spike shows the hack is brittle and the concierge MVP shows users are not actually blocked**: ship V1 without single-file sharing, with a time-boxed post-launch sprint and a written commitment.

### The pre-mortem categorization

- **File-sharing hack** — paper tiger. Visible and worrying, but potentially manageable with proper scoping.
- **Regression of the entire sharing system** — elephant. Looks small in isolation but structurally large; deserves more weight.

The team should weight the elephant heavier than the paper tiger. That biases against the hack.

### What "must-have" should mean

The framing should shift from *"what do users want?"* to *"what is the minimum set of capabilities that makes adoption possible for our primary target segment, without creating technical debt that blocks future velocity?"*

A *must-have* is something whose absence causes a defined user segment to **reject the product entirely** — not just *prefer* a different version. Most "users want X" arguments don't meet that bar; they belong in the *should-have* tier.

---

## Mini case 2 — Product readiness vs. GTM readiness

### Setup (anonymized)

A B2B engineering team has built a no-code spreadsheet interface for massive datasets, technically superior to anything in market.

- **Engineering Lead**: believes the product's technical superiority will drive word-of-mouth adoption. Wants to ship.
- **PM**: argues that in an enterprise B2B context, the product lives inside the company's larger product bundle, and sales reps are *coin-optimized* — they won't push a product without commission upside. Wants to hold until GTM incentives are solved.

Tension: ship a genuinely great product vs. hold until GTM incentives are aligned.

### What good looks like

In B2B, **distribution is product**. A technically superior product that doesn't get in front of buyers has zero value — and in enterprise, sales reps are the primary distribution mechanism. The PM's concern is real.

But "pause everything" is also wrong. It treats an internal process problem as a product readiness problem. Those are different.

The right framing: **GTM readiness is a launch criterion, not a build criterion.** Engineering should continue to a production-ready state in parallel with GTM alignment. The launch waits for both.

### Decompose readiness

PM and Engineering are measuring different things, so "tie-breaking" is the wrong frame. Decompose readiness into separate, explicit criteria with separate owners:

- **Technical readiness** — Engineering's domain. Stable, scalable, supportable.
- **GTM readiness** — PM's domain. Viable distribution path, equipped sales team, clear ICP.

A launch should require both gates to be green. Neither side can unilaterally block progress.

If sales-incentive alignment is genuinely launch-blocking, the PM needs to define *what aligned means specifically* — SPIF structure, sales training, quota attribution — and put a timeline on it.

If a subset of customers is reachable without sales-rep involvement (PLG, existing champion accounts), that gives a path to a *limited GA* without waiting on full incentive redesign.

### Specific moves

1. **Joint launch-criteria document.** Both gates explicit and measurable, with named owners and timelines.

2. **Two parallel experiments**, runnable in 4–6 weeks:

   - **PLG bypass experiment.** Identify 3–5 existing customers where a technical champion (data lead, analytics manager) already has exposure to the product. Enable self-serve access. Measure whether the champion can drive adoption within their org without a sales assist. Tests whether reps are necessary at all.

   - **Sales-rep SPIF pilot.** Pilot a single sales rep with a clear SPIF for closes on this product. Tests whether commission alignment unlocks the sales motion, without requiring a full incentive redesign.

3. **Define the right test population.** Existing power users, not cold prospects. The validation should answer "does adoption work in conditions favorable to it?" not "does it work in cold outreach?"

### Predictions, in order of likelihood

- **Most likely outcome:** PLG works for some segments (technical champions with strong internal networks), SPIF works for others (champions with less internal pull who need a rep introduction). Hybrid GTM motion.

- **Second most likely:** PLG is too slow at scale, SPIF works once the rep economics are right. Sales-led with PLG as a pre-qualification motion.

- **Less likely but possible:** Neither works without significant investment. The product needs more than just GTM alignment — it needs different positioning, packaging, or pricing.

The point of the experiments is to answer this with data, not opinion.

---

## Pattern across both mini cases

Both patterns are about **readiness being a multi-dimensional thing, not a single boolean.**

In Mini Case 1, technical readiness and customer-job satisfaction are different gates with different evidence requirements.

In Mini Case 2, technical readiness and GTM readiness are different gates with different owners.

The common failure: PM and Engineering argue past each other because they're each defending their own gate, and there's no shared framework that distinguishes them.

The common fix:

1. Decompose readiness explicitly
2. Assign owners to each gate
3. Define measurable criteria for each gate
4. Require all gates to be green before launch
5. Run experiments to resolve disputes about whether a gate is met

This is the bones of a **launch criteria document** (see [`templates/launch-criteria.md`](../templates/launch-criteria.md)).
