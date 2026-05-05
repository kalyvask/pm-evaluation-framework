# What makes a good PM

A short, opinionated take. The rest of this repo is the long version.

---

## The core posture

**Inflexible on problems. Flexible on solutions.**

A good PM holds the user's problem fixed and lets the solution path be argued. They will trade away their favorite design, their original spec, their preferred tech stack — but they will not let the team quietly drift from the actual user pain to a different, easier problem. When engineering pushes back, the PM does not capitulate on the problem; they ask which constraint is real and re-scope the solution.

Symptom of doing this badly: the team ships something close to what was originally specced, but no one can articulate which user is now meaningfully better off.

---

## What good PMs do differently

### 1. They diagnose before they design

Most product failures are diagnosis failures, not execution failures. The team built something well-researched, well-shipped, and aimed at the wrong constraint. A good PM spends disproportionate energy upfront making sure the bottleneck they're solving is the bottleneck that determines user behavior.

A useful test: if the product fails, will the postmortem read "we built the wrong thing" or "we built the right thing badly"? Diagnosis-first PMs almost always end up in the second category.

### 2. They humanize problems with stories, then back them with data

A persona deck is not the same as five quotes from real users describing what they were trying to do when the product failed them. Good PMs collect those quotes and use them to ground every cross-functional conversation. The data follows the story; it does not replace it.

### 3. They categorize decisions by reversibility, not by importance

Important is not the same as irreversible. A high-stakes feature launch on a digital surface is usually reversible — you can roll back, iterate, or kill it. A hardware decision, a regulatory commitment, a public partnership, an architectural choice that propagates — those are one-way doors. Good PMs spend their decision quality budget on the irreversible ones and ship faster on the reversible ones.

### 4. They present problems to engineering, not solutions

The fastest way to lose engineering trust is to walk in with a fully-specced solution and expect implementation. Good PMs walk in with a clearly-defined user problem, the constraints they understand, and the open questions. They let engineering be a thought partner on the *how*. When engineering proposes a path the PM didn't expect, the right response is curiosity, not defensiveness.

### 5. They define what success and failure look like *before* the work starts

What is the metric? What value of that metric counts as success? What value would force us to kill it? Without these answers in advance, every result becomes negotiable, and the team rationalizes shipping the thing they already built.

### 6. They shield the team in public and challenge it in private

When something goes wrong externally, the PM takes the hit. They do not throw engineering, design, or sales under the bus to a customer or executive. Internally, they push hard on quality, on missed details, on faster iteration. The asymmetry is the point: trust gets built by absorbing blame the team didn't earn.

### 7. They notify executives early — with a heads-up, not a complete analysis

The worst version of an exec conversation is one where the executive learns about a problem from a customer or a competitor. A good PM gets ahead of that with a brief, honest message: *here's what we're seeing, here's what we don't yet know, here's what we're doing about it, here's when I'll have more.* Tell your boss before they hear it from somewhere else.

### 8. In the AI era: they can build a prototype before asking for engineering investment

The bar has moved. A PM who can stand up a working prototype — not a Figma flow, an actual interactive thing — can validate demand, surface real friction, and build internal buy-in *before* asking for headcount. Pitching a feature you've never tried to use yourself is increasingly a luxury.

---

## What good PMs avoid

- **Optimizing for the wrong variable.** Beautiful research, clean execution, wrong target metric.
- **Treating UXR signals as mandates.** User research is an input. Stress-test segment size, switching cost, and revealed-vs-stated preference before treating it as a tiebreaker.
- **Confusing user love with business viability.** A product can have unusually strong NPS and still fail to find a sustainable economic model. PMF and business-model fit are not the same thing.
- **Confusing free adoption with PMF.** "People are using it" is not the same as "people would pay for this and renew."
- **Sunk-cost-driven roadmaps.** Continuing because you've already spent nine months, not because the path forward is right.
- **Hope as a strategy.** "If we ship this, the segment we need will adopt it" is a hypothesis, not a plan. If the GTM depends on that segment, that segment must be in the validation cohort.
- **Avoiding the hard segment in research.** Research with the convenient users instead of the strategically necessary ones.
- **Killing too early or holding too long.** The hardest call is between perseverance ("things take time") and sunk cost ("we keep thinking the next thing will do it"). You will not always make the right call. Build the discipline of explicit kill criteria so the decision isn't made by inertia.

---

## The three capabilities that matter most

Drawn from the patterns in this repo, three capabilities determine more PM outcomes than any others:

1. **Diagnostic clarity** — the ability to identify the actual constraint before designing a solution
2. **Cross-functional credibility** — the trust to be heard by engineering, design, sales, exec, and customers, often in the same week
3. **Calibrated conviction** — strong opinions on the right things, held loosely on the wrong ones, revised when the evidence demands it

These are also the three places where PMs most often fall short, in roughly that order.
