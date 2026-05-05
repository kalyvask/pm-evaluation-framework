# Problem framing

Most product failures are not execution failures. They are diagnosis failures — a team built something well, shipped it on time, and aimed it at the wrong constraint.

This file is about getting the diagnosis right *before* you commit resources.

---

## Inflexible on problems, flexible on solutions

The single most useful PM posture. Hold the user's problem fixed; let the solution be argued.

When engineering pushes back on scope, when design wants a different metaphor, when sales asks for a workaround — re-state the *problem* and ask whether the proposed change still solves it. Most disagreements collapse once everyone re-anchors on the user pain. The ones that don't usually reveal that the team has been quietly drifting from the original problem to an easier one.

The opposite failure — *flexible on problems, inflexible on solutions* — is what produces products that ship on time and don't matter. The team kept the spec; they just stopped solving the user's problem along the way.

---

## Problem statement structure

Write the problem in this shape, on one line:

> **[Specific user]** is trying to **[specific job]** but **[specific blocker]**, which causes **[concrete cost]**.

Concrete bad:

> Users want better collaboration features.

Concrete good:

> A solo creator running a daily live show wants to bring a guest on stage without exposing their channel to coordination overhead, but today they have to set up a private Discord, vet the guest manually, and walk them through tooling — which costs them 20–40 minutes of off-stream prep per session and limits how often they run guest segments.

The good version is testable, falsifiable, and tells you what to measure. The bad version is a feature request dressed as a problem.

---

## The Five Whys

Ask "why" five times, starting from the surface complaint, drilling toward the root cause.

> **Surface:** "Users say they want a 'simpler interface.'"
> **Why?** They get lost on the second screen.
> **Why?** The second screen is the first time they have to make a decision; the labels are jargon.
> **Why?** The labels were chosen by engineering, mirroring the data model.
> **Why?** No one validated the labels with new users in onboarding research.
> **Why?** The team treats onboarding as a marketing problem, not a product one.

Real fix is at level five — restructure how onboarding is owned — not at level one (redesign the second screen).

The Five Whys is most valuable when the surface complaint is *too easy to fix*. If the obvious patch feels suspicious, drill before you build.

---

## "What would you have to believe for this to be true?"

A stress-test question for any strategic claim.

When someone says "this segment will adopt this product because it solves their problem" or "users will pay 2× more for this premium tier," ask: *what would have to be true* for that statement to hold?

Then list the load-bearing assumptions explicitly. For each one, mark whether you have evidence, a hypothesis, or a guess. The guesses are where the strategy can break.

Example:

> Claim: "Top creators will adopt our collaboration product, and smaller creators will follow them."
>
> What would have to be true:
> 1. Top creators have an unmet collaboration need *and* the product solves it. **Evidence?** Talked to 3, none of whom adopted. *Guess.*
> 2. Smaller creators imitate top creators specifically through collaboration features. **Evidence?** Anecdotal, no causal data. *Hypothesis.*
> 3. The product doesn't impose a cost on top creators (e.g. going offline) that breaks their normal stream economics. **Evidence?** It does require going offline. *Guess that's already falsified.*

When the load-bearing assumptions are guesses — especially falsified ones — the strategy is broken. Pivot before you launch, not after.

---

## Wrong-bottleneck diagnosis

A common diagnostic failure: the team is solving a real, validated user problem — but it's not the *constraint* that determines user behavior.

Symptoms:
- The team's research is sound
- The product addresses pain points users described
- Users still don't adopt at the rate the team expected

When this happens, the team usually optimized for **friction** when the actual constraint was **incentive structure**. They made it easier for users to do something users had no economic reason to do.

The fix: when adoption fails despite good research, ask not "what feature is missing?" but "what does adopting this product cost the user, and what do they get?" Sometimes the product asks the user to give up something (audience, subscriber base, autonomy, status) that no amount of feature polish will compensate for.

(See `case-patterns/wrong-bottleneck.md` for the canonical example, anonymized.)

---

## Problem vs. opportunity

Two different framings, each useful in different contexts.

- **Problem framing** — anchors on user pain. *"Users are losing 40 minutes per session to coordination overhead."* Most useful when the user is articulate about their pain and the team is at risk of building features no one needs.
- **Opportunity framing** — anchors on a market shift or a capability gap. *"Generative AI now makes it possible to summarize meetings automatically; no incumbent has shipped a credible version."* Most useful in greenfield or platform-shift situations, where existing users don't yet know to want what's possible.

Don't conflate them. An *opportunity* is not a *problem* until you can articulate which user, in which job, gains what. Many "AI opportunity" decks fail this test.

---

## Diagnostic checklist

Before any solution discussion, you should be able to answer:

1. **Who, specifically, has this problem?** Named segment, sized market.
2. **What are they trying to do?** Job, not persona.
3. **What's blocking them today?** Including all current workarounds and substitutes.
4. **What's the cost of not solving it?** In time, money, missed outcomes.
5. **Is the constraint we identified actually the *bottleneck*, or is it merely *related to the bottleneck*?**
6. **What would have to be true** for our hypothesis to hold? Which of those things is currently a guess?

If two or more of these are vague, you are not ready to scope a solution. Sharpen the diagnosis.
