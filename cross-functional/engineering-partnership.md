# Engineering partnership

How PMs and engineers work well — or poorly — together. Most of this is hard-earned and not in any process doc.

---

## Present problems, not solutions

The single fastest way to lose engineering trust is to walk in with a fully-specced solution and expect implementation.

Good PMs walk in with:

- **A clearly-defined user problem** (see `decision-making/problem-framing.md`)
- **The constraints they understand** (technical, business, regulatory, budget, timeline)
- **The open questions** they don't yet know the answer to

Then they let engineering be a thought partner on the *how*. When engineering proposes a path the PM didn't expect, the right response is curiosity ("walk me through the tradeoffs"), not defensiveness ("but the spec says...").

The PM stays inflexible on the *problem*. The engineer is given the room to be inflexible on the *solution* — because they know the system better.

The wrong dynamic — PM specs the solution, engineer implements without context — produces:
- Worse solutions (PM lacks technical depth)
- Demoralized engineers (no agency)
- Slower iteration (PM is the bottleneck on every architectural decision)
- Brittle products (engineers shipped what was asked, not what was needed)

---

## Stated user desires vs. technical constraints

UXR signals are inputs, not mandates.

When users say they want X and engineering says X requires a hack with broad blast radius, the PM's job is **not** to break the tie by siding with research. It's to validate whether the hack's blast radius is acceptable, and whether the user's stated desire is actually what they need.

Two specific sharpening questions:

1. **Is the user's desire a *job* or a *solution*?** Often "users want single-file sharing" is a solution they imagined. The underlying *job* might be "share a discrete work artifact with a colleague." If so, a project-scoped share with a clean migration path may serve the job without the architectural hack.

2. **What's the blast radius of the technical workaround?** A contained, reversible patch is acceptable. A coupling to core access control that spreads through the system is a paper tiger that turns into an elephant six months later.

When a feature requires a hack, the right response is to scope the hack carefully — not to treat UXR demand as the tiebreaker that overrides architecture.

---

## "Must-have" requires a testable definition

PM and Engineering align on launch criteria when *must-have* is testable. Otherwise the conversation devolves into "I think it's must-have" / "I think it's not."

Testable definition:

> A feature is *must-have* for a release if its absence causes a defined user segment to **reject the product entirely** — not just *prefer* a different version.

Two specific things:

- **Defined user segment.** Not "everyone." Pick the strategically necessary segment.
- **Reject, not prefer.** A feature whose absence makes 80% of users *prefer something else* is a *should-have*, not a *must*. Strong should-haves are real. They are not launch-blockers.

When PMs over-classify features as must-have, engineers learn to discount the label. When engineers over-classify constraints as showstoppers, PMs learn to discount their pushback. Both sides need to keep the labels meaningful.

---

## Test before you commit

The fastest dispute-resolution move: **prototype the disagreement.**

When PM and Engineering disagree on a feature's value or feasibility, the highest-leverage move is usually to run a small, time-boxed test:

- **Concierge MVP / friction audit** — for "do users actually need this?" Identify a few users who flagged the issue and watch them complete the workflow with and without the proposed feature. Often reveals whether they're truly blocked or whether a good migration UX resolves the concern.
- **Engineering spike** — for "is this technically feasible without breaking other things?" Time-box 1–2 days. Build a thin prototype to quantify the regression risk before committing to a full build.
- **Lighthouse co-design** — for "will this drive adoption among the strategic segment?" Pick 3–4 customers from that segment and design with them. Their behavior, not their stated preference, is the signal.

The worst outcome is committing engineering effort to a feature without testing whether it actually drives the outcome the PM expected, or introducing technical entropy without measuring the fragility.

---

## Decompose readiness; don't tie-break it

When PM and Engineering disagree on whether something is "ready," they're usually measuring different things.

- **Technical readiness** — is the product stable, scalable, supportable? Engineering's domain.
- **GTM readiness** — is the distribution path proven, the sales team equipped, the ICP clear? PM's domain (often shared with marketing/sales).
- **Quality readiness** — is the experience good enough that users will form positive associations? Shared.

Tie-breaking the wrong frame. The right move is to **decompose readiness into separate, explicit criteria with separate owners**, then require all gates to be green before launch. Neither side can unilaterally block; both sides must declare their gate met.

This is the single most useful artifact for cross-functional launches: a one-page **launch criteria document** with named owners and measurable gates. (See `templates/launch-criteria.md`.)

---

## In B2B, distribution is product

This deserves its own section because PMs from consumer backgrounds repeatedly under-weight it.

In B2B, **a technically superior product that doesn't get in front of buyers has zero value.** Sales reps are the primary distribution mechanism in most enterprise contexts.

Two implications:

1. **Sales-rep economics are a launch criterion.** "Coin-optimized" reps will not push a product without commission upside. If the comp plan doesn't reward selling this product, the product won't sell. This is solvable (SPIFs, quota attribution) but it must be solved.

2. **GTM readiness is a launch criterion, not a build criterion.** Engineering should continue to a production-ready state in parallel with GTM alignment. The launch waits for both. Pausing engineering until GTM is solved treats an internal process problem as a product readiness problem; they are different.

If a product is genuinely viable through PLG (technical champion adopts, drives adoption within their org), that's a parallel path. Test it: enable self-serve access for 3–5 existing customers' technical champions, measure whether champions can drive adoption without sales assist. That tests the PLG hypothesis directly without needing to redesign the comp plan.

---

## Engineering morale is a leading indicator

When engineers leave or disengage, it's almost always a leading indicator of a *direction* problem, not a *resourcing* problem. Adding more engineers to a team that's losing engineers is treating the symptom.

Common direction problems that show up as morale issues:

- Team is solving the wrong problem (architecturally, strategically)
- Team is being asked to commit to a strategy after a previous one visibly failed, with no postmortem
- Team is spinning on dependencies it doesn't control
- PM is making decisions without engineering input, or vice versa

When morale drops, the question is not "how do we cheer them up?" It's "what direction problem are they sensing?" Engineers often see the elephant in the room before the rest of the org. Listen.

---

## What engineers wish PMs would do more

A composite list, drawn from real critiques:

- **Tell us *why* before *what*.** The user pain, the strategic context. We will design better solutions if we understand the problem.
- **Be willing to revise the spec when we surface tradeoffs.** Especially on architecture.
- **Don't bring the same feature back six months later under a different name.** If we said no for a reason, engage with the reason.
- **Cut scope under pressure, not quality.** Shipping a thin slice well is better than shipping a wide slice broken.
- **Take the public hit when something goes wrong.** Don't pin it on the team.
- **Stop polling for status.** Trust the standup. If you need more, change the standup.
- **Bring real users to engineering — at least once a quarter.** The most motivating thing for an engineer is watching a real user struggle with the thing they built.

---

## Decision checklist

Before any major cross-functional commitment:

1. Have I presented the *problem* to engineering, not the solution?
2. Are *must-have* features defined by which segment rejects the product without them?
3. Are launch criteria decomposed into technical / GTM / quality gates with named owners?
4. For B2B: is sales-rep economics a launch criterion, not an afterthought?
5. Has engineering had genuine room to push back on architecture before I committed publicly?
6. If engineers are leaving or disengaging, have I diagnosed the direction problem instead of the resourcing problem?

If two of these are weak, the cross-functional partnership is fragile, even if work is shipping.
