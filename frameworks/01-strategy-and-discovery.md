# Phase 1 — Strategy & Discovery

**Focus:** Define the *why* for PMF. Before you scope an MVP, you need a defensible answer to: *which problem, for whom, and why does anyone care now?*

---

## PMF Narrative

A short, written hypothesis covering three things:

- **The problem** — what is the user trying to do, and what's blocking them today?
- **The audience** — which segment(s) feel this most acutely, and how big is that pool?
- **The value proposition** — what specifically changes for the user when this works, that they cannot get from alternatives?

Write it as one paragraph. If you cannot, you don't yet have the narrative — you have a feature idea. Re-write until each sentence would survive being read aloud to a customer.

**Common failure:** the value prop is described in product features ("AI-powered, real-time, collaborative") rather than user outcomes ("they can ship the report on Monday morning instead of Tuesday afternoon").

---

## Working Backwards (PR/FAQ)

Write the press release and the FAQ *before* writing any code.

The PR forces you to articulate the customer-facing benefit in plain language: who is the customer, what is the problem, what is the experience, how is it different. The FAQ forces you to answer the questions skeptical executives, customers, and engineers will ask. If either document is hard to write, the product idea is not yet sharp enough to build.

A good PR is one page. A good FAQ surfaces the hardest internal disagreements rather than papering over them.

---

## Pre-Mortem Analysis

Before launch, imagine the product has failed. Then ask the team: *what killed it?*

This works because it's psychologically easier to surface concerns about a hypothetical failure than to challenge a colleague's plan. It also routes around groupthink — people who would not voice doubts in a normal review will offer them when the prompt is "imagine we just bombed."

Useful taxonomy for the risks people surface:

- **Tigers** — risks that will definitely bite you. Treat as constraints to design around.
- **Paper tigers** — risks that look terrifying but are manageable with proper scoping. Don't over-invest.
- **Elephants** — risks that look small in isolation but are structurally large. Underweighted by default; deserve outsized attention.

Run the pre-mortem at strategy pivots, not just pre-launch. The most expensive failures are diagnosed before the launch but not acted on.

---

## Execution Risk Matrix

Plot each work-stream on two axes: cost/risk of execution × strategic alignment.

- **High alignment, low risk** → ship now
- **High alignment, high risk** → invest in de-risking before commitment
- **Low alignment, low risk** → only if it serves a learning goal
- **Low alignment, high risk** → kill

The point of the matrix is not the placement, it's the conversation. Forcing the team to defend why something is on the strategic axis usually surfaces work that's there because someone wanted it, not because it serves the strategy.

---

## One-Way / Two-Way Doors

Categorize decisions by reversibility before you spend any decision quality on them.

- **Two-way doors** are reversible: ship a feature, run an experiment, change a copy. The cost of being wrong is small. *Bias toward speed.*
- **One-way doors** are not: hardware launches, regulated commitments, public partnerships, architectural choices that propagate, brand promises, contractual lock-in. The cost of being wrong is high and structural. *Bias toward rigor.*

PMs habitually mis-categorize: they treat reversible decisions as one-way (slow them down with too much process) and irreversible decisions as two-way (rush them).

A useful test: *if this turns out to be wrong in three months, what does the unwind look like?* If the answer is "press a button," it's two-way. If the answer involves customer notifications, partner renegotiation, or "we'd basically have to start over," it's one-way.

**Hardware and regulated products skew heavily toward one-way.** The cost of a mistake compounds because you can't iterate without recall, regulatory filing, or physical retooling. Spend more time upfront, prototype more aggressively, and require evidence at a higher bar than you would for a digital surface.

---

## When this phase is done

You should be able to answer, on one page:

1. What problem are we solving, for whom, and why now?
2. Which decisions on the path forward are one-way doors? What confidence do we have on each?
3. What are the three failure modes most likely to kill this — tigers, paper tigers, and elephants?
4. What would have to be true for this to succeed? Which of those things do we believe, and which are we guessing at?

If any of these is unclear, do not move to MVP scoping. The cost of building the wrong thing is always higher than the cost of one more week of framing.
