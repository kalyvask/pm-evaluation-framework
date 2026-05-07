---
name: pm-value-hypothesis-tester
description: Pressure-test a value hypothesis (the what / who / how / why-now) before resources are committed, design the smallest experiment that would falsify it, and pre-commit kill criteria. Use when the user is about to launch, fundraise, or scale a product and wants the bet stress-tested — or when they're stuck on a fuzzy "we'll figure it out" hypothesis. Catches insight-free products, segments that are needy but not desperate, hedged "who" decisions, and skipped early-adopter beachheads. Returns a sharpened hypothesis, the falsifying experiment, and the kill threshold.
---

# PM value hypothesis tester

Helps a PM articulate and stress-test the value hypothesis underneath a product before the team pours in resources to scale it. Anchored in `decision-making/value-hypothesis.md` (Rachleff's what/who/how, Christensen's disruption definition, Geoffrey Moore's chasm and bowling-pin strategy, Ries/Blank on MVP and leap-of-faith assumptions).

The skill is opinionated. It will refuse to accept "SMBs in North America" as a who. It will push back on "subscription" as a how when no rationale is given. It will demand the falsifying answer be written down before any experiment is run.

## When to use

Use this when:
- The user is **about to launch or scale** a product and wants the underlying bet pressure-tested
- The user is **fundraising** and the investor wants more evidence the bet holds together
- The user has a **product that's not growing** and is trying to figure out which assumption is wrong
- The user is **wrestling with whether to pivot** — and which dimension (who / how / what)
- The user is **starting from an idea** and wants to convert it into a testable hypothesis instead of jumping to building

Don't use this when:
- The product already has clear PMF and the question is **how to grow** — use `frameworks/04-post-pmf-growth.md`
- The user wants to **measure existing PMF** — use `frameworks/03-pre-pmf-validation.md` and `pm-metrics-critic`
- The decision is **whether to kill an existing feature** — use `pm-decision-coach` with kill-criteria framing
- The user wants to **design the actual interviews** that test the who — use `pm-customer-interview-coach`

## How to apply

1. **Force the one-line hypothesis.** Push the user to write: *"For [specific desperate who], we will build [specific what] enabled by [specific insight], monetized via [specific how]."* If any blank is generic, stop and re-write before evaluating anything else. A vague hypothesis cannot be falsified, which means it's not a hypothesis. Reference `decision-making/value-hypothesis.md` § "What a value hypothesis is."

2. **Stress-test the insight (the what).** What changed — technologically, behaviorally, or in regulation — that makes this newly possible? If the answer is *"nothing changed, we just think the existing solution is bad,"* that's a sustaining innovation, not a non-consensus bet. Apply Rachleff's right/non-consensus filter. Reference `decision-making/value-hypothesis.md` § "The 'what'." Cross-reference `decision-making/problem-framing.md` § "Problem vs. opportunity."

3. **Stress-test the who: desperation, not need.** Ask whether the segment is *desperate* by Andy Rachleff's bar:
   - Are they emotional about the problem, not just acknowledging it?
   - Have they cobbled together a manual workaround?
   - Do they have budget? Do they actively search for solutions?
   - Would they "reach across the table" to grab the product?
   If the answer to most of these is no, the segment is needy but not desperate. **Pivot the who.** Adding features doesn't fix this.

4. **Check Geoffrey Moore positioning.** Where on the adoption curve is the target? If the team is pitching to the early/late majority before crossing the chasm with early-adopter references, that's a chasm jump and it usually fails. Reference `decision-making/value-hypothesis.md` § "Geoffrey Moore's adoption curve."

5. **Check the bowling-pin discipline.** Is there *one* lead pin, named with multiple segmenting axes (vertical, role, company size, geography, JTBD, life situation)? Or is the team hedging across three customer segments in parallel? Hedging is the most common failure mode at this stage. Push for one lead pin, narrow enough that it could be dominated.

6. **Stress-test the how.** Ask:
   - Why this business model? Does it enhance the product or compete with it?
   - If not advertising-based, why isn't the team charging from day one?
   - Could this be made *disruptive* in the Christensen sense (simpler, cheaper, more convenient — uneconomic for incumbents to copy)? Reference `decision-making/value-hypothesis.md` § "The 'how'."

7. **Surface the leap-of-faith assumption.** Ries: *the one belief that, if false, the whole thing falls apart.* Force the user to name it. Then ask: *what's the smallest experiment that would falsify it?*

8. **Pre-commit the kill criterion.** Before any experiment runs, the user must write down: *if X happens, we pivot the who. If Y happens, we restart on the what.* If they can't write the falsifying answer in advance, they're not running an experiment — they're collecting evidence for a verdict they've already reached. Reference `cross-functional/failure-management.md` and `templates/decision-memo.md`.

9. **Distinguish product risk from market risk.** Is the dominant risk *will they buy it?* (market) or *can we build/grow it?* (product)? Customer interviews and design sprints resolve market risk well; they barely touch product risk. If the bet is mostly product risk (deep tech, consumer media), say so — interviews give a starting point but the user will have to build to learn the rest.

## Output structure

```
## The one-line hypothesis
**[Sharpened version, with all four blanks specific.]**

## What
**Insight:** [The technology / behavior / regulatory change that makes this newly possible.]
**Verdict:** [Right & non-consensus / right & consensus / no insight / insight-without-evidence]
[If no insight: name the gap. Most "right & consensus" bets are not worth pursuing.]

## Who
**Lead pin:** [Named with segmenting axes. Reject "SMBs" or "operators" alone.]
**Desperation evidence:** [Specific, behavioral. Not "I asked them and they said yes."]
**Verdict:** [Desperate / needy-but-not-desperate / hedged-across-segments / undefined]
[If hedged: the team needs to pick one. Recommend which one based on desperation signal.]

## How
**Business model:** [What you charge, who pays, why this model not another.]
**Disruptive?** [By Christensen's definition: simpler/cheaper/more-convenient + uneconomic-to-copy. Or no.]
**Verdict:** [Enhances product / neutral / undermines product / undefined]

## Leap-of-faith assumption
[The one belief this whole hypothesis rests on. If false, the rest doesn't matter.]

## Smallest falsifying experiment
[The cheapest, fastest test that could prove the leap of faith wrong. Specific cohort, specific signal, specific timeline.]

## Pre-committed criteria
- **Validated if:** [Specific behavior, threshold, timeline.]
- **Pivot the who if:** [What signal would say the segment is wrong.]
- **Restart on the what if:** [What signal would say the underlying insight is wrong.]

## What's missing
[The 1-2 things you'd want to see before committing real resources. Most often: a sized lead pin, an articulated insight, or a kill criterion.]
```

## What good looks like

- The sharpened hypothesis fits on one line and **names a desperate cohort**, not a TAM slice. *"For solo creators running daily livestreams in the US"* beats *"For creators."*
- The leap-of-faith assumption is **the one** that would kill the bet, not five comfortable ones. Most teams have multiple risky assumptions and try to test them all in parallel; the skill picks the load-bearing one.
- The falsifying experiment is **specific and cheap.** *"Pre-sell the product to 10 named earlyvangelists at full price by [date]; if fewer than 3 commit, the segment is wrong"* is the bar.
- The kill criterion is **pre-committed**, including which dimension to change (who vs. what). Most teams skip this and end up rationalizing post-hoc.
- The skill calls out hedging directly. If the user is targeting three customer segments in parallel, the recommendation is *pick one*, not *triangulate*.
- The skill names whether this is mostly market risk or product risk, and adjusts what interviews can and can't prove.

## Anti-patterns

- Accepting a generic who. *"Operators at logistics companies"* is not a lead pin. Push until there's a vertical, a role, a size band, and ideally a JTBD.
- Letting "we'll figure out the business model later" pass. The model is part of the hypothesis. If the team isn't charging because *"we want to grow first,"* surface that this is a deliberate (and risky) bet, not an absence of one.
- Recommending "more research" when the existing data already shows the segment isn't desperate. The right move is to pivot the who, not to interview more of the wrong cohort.
- Treating one earlyvangelist as PMF. One desperate user is a starting point; the bowling-pin needs ten before the segment is meaningfully validated. Reference `frameworks/03-pre-pmf-validation.md` § "10 happy users."
- Falsifying experiments that can't actually fail. If the test is "ship the MVP and see if anyone uses it," it isn't an experiment — every product gets *some* usage, and the kill threshold isn't pre-defined. Push for a specific behavioral threshold.
- Avoiding the disruption question. Most teams are building sustaining innovations and assuming they'll win on quality. Surface this — it's usually fatal in tech where good-enough wins.
- Calling a chasm-jump a strategy. If the plan is to skip early adopters and sell directly to the pragmatic majority, the hypothesis has a structural flaw. Name it.
