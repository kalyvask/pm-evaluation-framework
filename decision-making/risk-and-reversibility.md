# Risk and reversibility

How to think clearly about which decisions deserve rigor and which deserve speed.

---

## One-way vs. two-way doors

The single most useful question to ask before any major decision: **is this reversible?**

- **Two-way door:** you can walk back through it cheaply. Ship the feature, run the experiment, change the copy, A/B the price. If it's wrong, roll back, iterate, kill it.
- **One-way door:** you cannot walk back, or the cost of walking back is structural. Hardware launches, public commitments, regulated filings, brand promises, architectural choices that propagate through the codebase, contractual lock-in, partnerships, naming.

The mistake PMs make is **mis-categorizing** — treating reversible decisions as one-way (and slowing them down with too much process) or treating irreversible decisions as two-way (and rushing past the rigor they deserve).

The decision quality budget is finite. Spend it where reversibility is low.

### A useful test

> *If this turns out to be wrong in three months, what does the unwind look like?*

If the answer is "press a button" or "ship a fix" — two-way door. Move fast.

If the answer involves customer notifications, partner re-negotiation, regulatory filings, or "we'd have to start over" — one-way door. Slow down. Prototype. Get external review. Pre-mortem hard.

### Hardware and regulation skew one-way

Two product domains where almost every decision is one-way-ish:

- **Hardware** — once it's manufactured and shipped, recall is the only reversal, and it's expensive. Test in real conditions, not labs. Static mockups frequently miss issues that only appear when the hardware is in motion or in the user's hand.
- **Regulated industries** (financial services, healthcare, autonomous systems) — choices about disclosures, data handling, eligibility, pricing structure all interact with regulatory classification. Once classified one way, re-classification is slow and expensive.

In both, the upfront rigor bar should be much higher than for software. Spend the prototype/research time before you commit.

---

## Pre-mortem

Before launch, imagine the project failed. Then ask: *what killed it?*

The point is to surface concerns the team would not voice in a normal go-no-go review. People who would never say "I think this won't work" will gladly say "in the failed-future where we had to explain why this flopped, I think the reason would have been X."

The output is a list of risks. Sort them:

- **Tigers** — risks that will definitely bite. Treat as constraints. Design around them.
- **Paper tigers** — look terrifying but are manageable with proper scoping. Don't over-invest.
- **Elephants** — look small in isolation but are structurally large. The risk that a senior person waved off because "we'll handle that in v2" — and v2 never comes. These are systematically underweighted; spend extra time on them.

Run pre-mortems at strategy pivots, not just pre-launch. The most expensive failures are the ones where everyone saw the elephant in the room but no one was willing to name it.

---

## Sensitivity analysis

For any decision with quantitative inputs (pricing, capacity planning, model choice, GTM spend), explicitly compute:

- **Best case** — everything goes right
- **Base case** — what we expect
- **Worst case** — most assumptions break

Then ask: *can we live with the worst case?*

If the worst case is acceptable (we lose some users, learn, iterate) — proceed. If the worst case is existential (we run out of money, lose the partnership, break the product) — change the plan.

The point is not to assign probabilities. The point is to make the downside *explicit* before committing, so you don't get there by accident.

---

## "What would have to be true?"

Both a problem-framing tool (see `problem-framing.md`) and a risk-management tool. List the load-bearing assumptions of any plan. For each one:

- Mark whether it's evidence, hypothesis, or guess
- Identify the cheapest way to test the guesses
- For assumptions that *cannot* be tested before commitment, name a kill criterion that would force you to abandon the plan if you see it after launch

Plans built on guesses without kill criteria are not plans. They are bets.

---

## Acceptable failure ranges (define them upfront)

For any new project, write down — *before* the work starts:

1. **What does success look like?** Specific metric, specific value, specific date.
2. **What does failure look like?** Specific metric, specific threshold, specific date.
3. **What's the acceptable failure range?** What level of underperformance can we live with as a learning, vs. what level forces us to kill the project?

This matters because, after the fact, every result becomes negotiable. Without pre-committed thresholds, the team will rationalize whatever happened. Pre-commitment turns the post-launch conversation from "is this good or bad?" (subjective) to "did we hit the bar we set?" (objective).

It also gives executive cover for the kill decision. "We agreed in advance that <X% adoption at <Y> weeks would mean we stop. We're at <X−5%>." That's a much easier conversation than retroactive judgment.

---

## Type 1 vs. Type 2 decisions in regulated and high-stakes contexts

In regulated industries (or any high-stakes domain), the cost of a wrong decision is asymmetric. False positives (shipping something bad) often cost more than false negatives (failing to ship something good).

For these decisions:

- The bar for evidence should be higher
- The number of stakeholders consulted should be larger
- The time horizon for review should be longer
- The default should be *don't ship* unless evidence is overwhelming, not *ship* unless there's a clear blocker

The cost of slowness is opportunity cost. The cost of speed is realized harm. They are not symmetric.

---

## Decision checklist

Before committing to a major decision:

1. **One-way or two-way?** Honestly. Don't downgrade the rating to ship faster.
2. **What's the worst case?** Can we live with it?
3. **What are the load-bearing assumptions?** Which are guesses?
4. **What does success look like?** Failure?
5. **What's the kill criterion** if this doesn't work post-launch?
6. **Has anyone run a pre-mortem?** What were the elephants?
7. **For regulated/hardware decisions:** has the rigor matched the irreversibility?

If you can't answer all of these, you're not ready to commit.
