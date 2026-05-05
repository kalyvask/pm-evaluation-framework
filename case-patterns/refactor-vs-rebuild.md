# Refactor vs. rebuild

## The shape

A flagship product, acquired or built years ago, sits on a legacy stack. The company built newer capabilities on a modern stack. Every new feature on the legacy product requires workarounds. Four-week features stretch to twelve. Bugs cascade. The team commits to a "refactor in place" rather than a full rebuild — and nine months later, it isn't working.

The PM faces a forking decision: double down on the refactor, bring leadership in, migrate users to a different product, or rebuild from scratch. Underneath the four options is a single hard question: *how much trust do you have left to spend, and how do you make leadership believe "this time is different"?*

---

## Setup (anonymized)

A cloud data platform's most-used product (a browser-based query tool) came in through an acquisition years earlier and was never fully integrated into the platform's governance and permissions model. While the rest of the company built modern capabilities (AI agents, geospatial, time series) on a new stack, the query tool stayed on the old one. The team committed to a module-by-module refactor rather than a full rebuild — partly to avoid the daunting prospect of migrating hundreds of thousands of customers.

Nine months in, the architecture turned out to be harder to fix than expected. Even successful refactor work didn't unlock the deeper platform integrations the roadmap required.

Three pressures squeezed simultaneously:

- **Team morale was cratering.** Two engineers had left. Senior engineers leadership trusted were the same ones whose original call was now in question.
- **Customer trust was eroding.** Bug volume and support cases climbing. Sales warning that deals were at risk.
- **The AI wave was passing the legacy stack by.** Modern competitors and AI-native startups were shipping features the legacy stack structurally couldn't support.

The PM ran two adjacent teams: the legacy product (95% of users — analysts running individual queries) and a modern, cell-based authoring environment that supported AI features (5–10% of users — data scientists doing multi-step work).

## The four options

1. **Double down on refactor in place** — throw more engineers at it, treat it as a resourcing problem.
2. **Bring leadership in early** — admit the refactor isn't working, ask for help shaping the next move.
3. **Migrate users to the modern product** — stabilize the legacy product, lean into the new one.
4. **Build a new query tool from scratch** — rebuild on a modern stack, eventually migrate everyone.

## Door types

Critically, the four options have different reversibility profiles:

- **Option 1** — two-way door, but only because she could stop at any time. Months spent here, however, are *opportunity cost one-way*.
- **Option 2** — two-way door. She could escalate later; the cost is that "later" arrived with less credibility.
- **Option 3** — *one-way door for users*. Once you migrate users to a different product, undoing it is brutal.
- **Option 4** — one-way door at the architecture level (you don't unbuild a new product), two-way at the migration pace (you can choose how aggressively to push customers over).

Mis-categorizing the door types was a real risk. Option 3 looked attractive (cheaper engineering!) but was the most one-way for users. Option 4 looked terrifying (start over!) but had reversibility at the migration pace.

## What worked

The PM ran the analysis through two lenses:

**Lens 1 — Inflexible on problems, flexible on solutions.** The user problem (the analyst majority needs a stable, platform-integrated, AI-ready query tool) stayed fixed. The solution path was open.

**Lens 2 — Kano model with decay-of-delight.** AI-assisted features were migrating from delighter to performance to must-be within 12–24 months. The legacy stack structurally could not deliver them. Time was not neutral.

The reframed answer: instead of *migrating users off the legacy product onto the modern one* (which fought the modern product's design intent and forced 95% of users into a worse fit), or *building a new product from scratch* (12–18 months of customer waiting), or *continuing the refactor* (wrong-problem fix), the right move was:

**Build the next version of the legacy product on the modern product's infrastructure.** Same familiar UI for analysts. Modern stack underneath. Reuse what the modern team had already shipped.

This was "build new" in architecture but "meet customers where they are" in UX. It threaded the needle: solved the architectural problem (the actual bottleneck), preserved the analyst majority's mental model, leveraged a platform that was already built and shipping, and was the most defensible story to take to leadership ("we are not starting over — we are consolidating onto the modern stack we already have").

## Lessons

### 1. The "this time is different" problem

After a public underdelivery, leadership's confidence is finite. A "now we want to start over" pitch lands very differently from a "here's what we learned, and here's why this is the right call now" pitch.

The PM needed to bring three things to the leadership conversation:

1. **A blameless postmortem of the refactor.** *Was this the right problem? What did we learn? How could we have learned it sooner?* This re-establishes that the PM's judgment is still trustworthy.
2. **A clear recommendation.** Not three options weighted equally. *This is what we should do, here's why, here's what I'm willing to bet on it.*
3. **A specific ask.** Protected headcount, exec air cover for sales conversations, public internal narrative that this is a strategic platform investment, not a recovery from failure.

Without all three, the conversation defaults to "another expensive bet from a team that already missed once."

### 2. Add engineers to a wrong-problem effort, scale the failure not the output

Doubling down on the refactor was the riskiest option dressed up as the safest. The team had been solving "code quality" when the real problem was "architectural decoupling from the platform." Adding engineers wouldn't fix that.

When a project is underdelivering, the first question is not "do we need more people?" It's "are we solving the right problem?" If the answer is no, more people make the failure bigger, not the output.

### 3. Engineering morale is a leading indicator, not a lagging one

Two engineers had already left. Asking the team to keep going on a strategy that visibly wasn't working was the fastest way to lose more institutional knowledge. The morale signal was leading the diagnosis.

When engineers leave or disengage, take it as data. They often see the elephant in the room before the rest of the org.

### 4. Lighthouse customers are validation evidence and credibility cover

A specific recovery move: identify three or four enterprise customers (a mix of "loyal-but-tired" users and more sophisticated teams) and co-design the new product with them from week one. This serves three purposes:

- Produces real validation evidence for leadership
- Gives sales a concrete story ("we are building this with [customer]")
- Lets the PM distinguish revealed from stated preferences before committing to a UX

Loyal-but-tired customers are exactly the right population to design with — they have skin in the game and they want this to work.

### 5. Shield the legacy product during the build

The hardest version of "build new" is "we built a new thing and the old thing collapsed in the meantime." A small (3–4 person) maintenance team on the legacy code, with a frozen scope (no new features, only stability and security), preserves customer trust during the build.

### 6. Inflexible on problems, flexible on solutions — even on solutions you committed to publicly

The PM had publicly committed to the refactor. The hardest part of the redirect wasn't the technical decision; it was the credibility recovery. The framing matters: *"I have not changed my mind about what this product needs to be. Only about the path to getting there."*

That's the difference between a team that learned and a team that flailed.

---

## When to recognize this pattern in your own work

Symptoms:

- Multi-quarter underdelivery on a refactor or migration
- Engineering morale dropping; senior engineers leaving
- Bug volume rising; sales warning of deal risk
- Roadmap blocked because new features require workarounds
- Leadership confidence visibly eroding
- A modern adjacent product or capability that *might* be leverageable

Diagnostic questions:

- *Are we solving a code-quality problem or an architectural problem?* (They have different fixes.)
- *Which of our options are one-way doors for users? For architecture? For credibility?*
- *Is there a way to leverage existing modern infrastructure rather than starting over?*
- *Have we run a blameless postmortem of the underdelivery, or are we still re-litigating the original decision?*
- *Do we have lighthouse customers to co-design the next version with?*

If two or more of these are unresolved, the recovery plan is not yet ready to bring to leadership.
