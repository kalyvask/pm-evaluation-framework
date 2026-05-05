# Phase 2 — Defining the MVP

**Focus:** Scope the minimal path to *aha*. The MVP is not a half-built product; it's the smallest complete experience that lets a real user feel the value.

---

## JTBD (Jobs to be Done) Ranking

Forget personas for this exercise. Personas are useful for top-of-funnel framing and stakeholder alignment, but they are too abstract for feature-level decisions.

Instead, list the specific *jobs* a user is hiring the product to do. For each job:

- How **frequent** is the job? Daily, weekly, monthly, once?
- How **important** is the job? Painkiller-tier or vitamin-tier?
- How **well-served** is the job today by existing alternatives (including duct-tape workarounds like spreadsheets, Discord, email)?

Rank by frequency × importance × under-served-ness. The MVP should ship the top one or two jobs done well, not the top ten done badly.

**Useful sharpening question:** "What is the user actually doing the moment before they reach for our product?" The answer often reveals a job the persona deck never named.

---

## MoSCoW Method

Categorize every proposed feature into one of four buckets:

- **Must-have** — without this, the product fails for the target segment. Absence is a deal-breaker.
- **Should-have** — important, painful to ship without, but the product still works.
- **Could-have** — desirable, ships if there's time.
- **Won't-have (this release)** — explicitly out of scope. The most valuable category, because it kills scope creep.

The discipline is in the *Must-have* column. A *must* is something whose absence causes a defined user segment to **reject the product entirely** — not just *prefer* a different version. If the team is calling everything must-have, you have not yet picked your target user.

Pair this with a launch criteria document that names *which user segment* defines must-have, so the bar is testable.

---

## Kano Model

Plot features on two axes: how much they're *implemented* × how much *satisfaction* they generate. Three feature tiers emerge:

- **Must-be (basic) features** — their absence destroys satisfaction; their presence does not increase it. Stability, security, governance, table-stakes integrations. Failing here is the most damaging because dissatisfaction compounds while satisfaction stays flat no matter how well other features perform.
- **Performance features** — satisfaction grows linearly with quality. Speed, accuracy, sharing, completeness.
- **Delighter features** — unexpected; their presence raises satisfaction sharply, their absence is unfelt. Today's delighter is tomorrow's performance feature.

**The decay-of-delight dynamic matters for roadmap.** AI-assisted query generation and natural-language exploration were delighters two years ago; they're already migrating to performance, and within 12–24 months they'll be must-be in many categories. Time is not neutral. Every quarter you don't ship a feature that's drifting from delighter to must-be, the cost of catching up grows.

A common failure: shipping delighters while the must-be tier is broken. Users are not delighted by clever features when the basics fail.

---

## Story Mapping

Lay out the user's end-to-end journey as a horizontal axis (steps in chronological order: discover → onboard → first use → habituate → advocate). Below each step, stack the features needed to support that step.

The MVP is then the **thinnest vertical slice** that covers the whole journey — not the full set of features for the first step. A tool with great onboarding and broken first-use is not an MVP; it's a half-built product.

Story mapping is also the best tool for spotting bundle effects. A feature that touches procurement, admin onboarding, support, billing, and the end user is rarely as scopeable as it looks at first.

---

## Cupcake Model

The MVP should be a **cupcake, not a half-baked wedding cake.**

A cupcake is small, complete, and delightful. A half-baked wedding cake is large, ambitious, and inedible. Both are "minimum" in some sense. Only one teaches you what the user actually wants.

This means an MVP can have *fewer features than the eventual product* — but the features it does have should be **finished**. A confused, buggy, half-functional surface does not validate demand; it teaches you that users hate confused, buggy, half-functional surfaces.

Test: hand the MVP to a real user, ask them to do one thing, and watch. If they finish it without help and feel good about the experience, you've built a cupcake. If they ask "is that all?" or get stuck, you've built a wedding cake fragment.

---

## When this phase is done

You should be able to answer, on one page:

1. Which job(s) does the MVP do, and why those?
2. What's in the *must-have* bucket and what's explicitly *won't-have*?
3. Where on the user journey are we covering, end to end?
4. What's the smallest complete experience we can ship, and how will we know it worked?

If you cannot ship something you'd be proud to demo to a target customer in 6–12 weeks, the MVP scope is wrong, not the timeline.
