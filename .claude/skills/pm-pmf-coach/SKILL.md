---
name: pm-pmf-coach
description: Walk a founder or early-stage PM through finding product-market fit on a specific bet. Use when the user is pre-PMF (no validated value hypothesis), has a candidate insight + audience + business model, and needs help deciding what to test next, how to interpret a failed experiment, and whether to pivot (change who/how) or restart (change what). Different from pm-value-hypothesis-tester which pressure-tests a single hypothesis statement statically; this skill runs the multi-step PMF process iteratively. Built on the Lean Startup synthesis (Rachleff, Ries, Blank, Moore, Christensen, Marks, Fitzpatrick, Cook).
---

# PM PMF coach

Walks a founder or early-stage PM through the discipline of finding product-market fit on a specific bet. Different from `pm-value-hypothesis-tester` (which pressure-tests one hypothesis statically); this skill runs the iterative loop: leap of faith → value hypothesis → experiment design → interpretation → pivot decision → distractions check.

Anchored in `decision-making/finding-pmf.md` (posture) and `decision-making/value-hypothesis.md` (mechanics).

## When to use

Use this when:
- A founder is pre-PMF and wants help structuring what to test next
- An experiment has produced a result (validated, partial, or failed) and the founder is deciding what to do
- A team is debating whether to pivot the who, pivot the how, or restart the what
- A founder has multiple candidate insights or audiences and needs help picking the lead pin
- A working PM is launching a new product (not a feature) inside an established company and needs the PMF discipline rather than the execution discipline

Don't use this when:
- The product already has confirmed PMF — use `pm-funnel-critic`, `pm-metrics-critic`, or `pm-decision-coach` for post-PMF questions
- The user wants critique of one specific value hypothesis statement — use `pm-value-hypothesis-tester`
- The user wants discovery interview help — use `pm-customer-interview-coach`
- The user is at a feature level inside an existing product with known PMF — use `pm-prd-drafter` or `pm-decision-coach`

## How to apply

### 1. Surface the leap of faith

Before anything else, ask: *what is the one underlying belief that, if false, makes this whole business dead?*

If the user names the value hypothesis (what/who/how) instead, push back. The leap of faith is upstream. Examples of well-formed leap-of-faith statements:

- "People will sleep in a stranger's home."
- "People will let software manage their investments."
- "Reusable rockets meaningfully reduce launch costs."
- "Enterprises will adopt SaaS for application performance monitoring instead of on-premises."

If the leap of faith has more than one assumption baked in, decompose it. Each assumption gets its own line. The MVP will need to test the one that's most upstream.

Reference `decision-making/finding-pmf.md` § "Leap of faith vs. value hypothesis."

### 2. Build the value hypothesis on top

Once the leap of faith is named, ask the user to write the value hypothesis in this shape: *"For [specific desperate who], we will build [specific what] grounded in [specific insight], monetized via [specific how]."*

Pressure-test each blank:

- **Insight (what just changed):** what technology, behavior, or regulatory inflection makes this newly possible? If "nothing," the bet is right-and-consensus. Acceptable but not outsized.
- **Who (the lead pin):** is the named segment *desperate* or merely *needy*? Apply the four-question filter (pays with little proof; has tried to build it themselves; actively frustrated; wants it now). See `decision-making/finding-pmf.md` § "Need is irrelevant. Desperation is everything."
- **What (the product):** is it tightly mapped to the insight? Or is it a generic product that happens to mention the insight in marketing?
- **How (the business model):** does the model enhance the product, or distract from it? Is the user willing to pay from day one (unless the model is advertising)? Free MVPs validate nothing about willingness to pay.

If any blank is generic ("SMBs in North America," "via subscription"), stop. Sharpen before designing the experiment. Reference `decision-making/value-hypothesis.md` for the full sharpening pass.

### 3. Design the smallest experiment that would falsify the leap of faith

Map the experiment to the leap of faith, not to the value hypothesis as a whole. The smallest test that would falsify the leap is usually one of:

- **Concept test** (landing page, one-page deck, in-person pitch). Tests whether anyone wants the thing at all. Days to set up.
- **Implementation test / design sprint** (week-long prototype + customer test, from Knapp). Tests whether the specific implementation produces desperation.
- **Concierge MVP** (a human does the work manually for 5-10 named users). Tests whether the outcome is valuable before automating delivery.
- **Wizard of Oz** (looks fully automated; behind the curtain, humans do the work). Tests the user experience without paying to build the automation.
- **Thin-slice MVP** (real end-to-end product covering one job for one segment). Last resort because cost is high.

Reference `decision-making/value-hypothesis.md` § "Prototype types" for the full menu.

The discipline: pick the smallest experiment that could prove the leap of faith **wrong**. Not the smallest that could prove it right. Confirmation is cheap; falsification is what generates learning.

### 4. Interpret the result honestly

After the experiment, the user comes back with one of three outcomes:

- **Leap of faith validated.** Customers behave as predicted. Word of mouth begins. Sales yield trends toward >1 in B2B, or organic growth begins to accelerate in consumer. The four desperation signals show up unprompted.
  - *Next step:* build the next experiment on the next assumption, or expand the lead pin to the first adjacent market. Resist the urge to switch to growth-hypothesis mode prematurely. One validated experiment is not PMF.

- **Leap of faith falsified.** Customers do not behave as predicted. No desperation, no retention, no word of mouth.
  - *Next step:* run the five-whys (Fitzpatrick, Blank) to find the root cause of the rejection. Seek the objection; do not overcome it. The five-whys output points at *which* part of the hypothesis failed.

- **Surprise.** Customers behave differently than predicted: worse on the predicted dimension, but unexpectedly *better* on a different dimension. A segment you didn't target loves it. A feature you considered minor gets outsized adoption. A use case you didn't design for becomes the use case.
  - *Next step:* drop the original hypothesis. Savor the surprise (Cook). Build the next experiment on the new signal. Most successful tech companies pivoted (sometimes restarted) on a surprise.

### 5. Decide: pivot the who, pivot the how, or restart the what

Most experiments produce "leap of faith falsified." The decision tree, in order of probability and success rate:

- **Pivot the who** (the most common pivot, highest success rate). The five-whys reveals the chosen segment was not desperate. Choose a different segment from the adjacent-market list. Keep the insight constant. Each new segment requires going back to early adopters and building toward the whole product for them.
- **Pivot the how** (less common). The five-whys reveals the segment is desperate but the business model is wrong (free when it should be paid, subscription when it should be transaction, advertising when it should be SaaS). Change the model. Keep the insight and the audience.
- **Restart the what** (almost never). The insight itself is wrong. Acknowledge the burn rate, fundraise if cash is short, and start over. Restarts have a much lower success rate than pivots. Do not confuse a pivot with a restart.

The vocabulary discipline matters because the moves require different organizational responses. A pivot keeps the team, keeps the insight, swaps the segment or model. A restart is closer to founding a new company inside the old one.

### 6. Run the distractions check

Before the user closes the loop, run the distractions check. Ask: *are you spending pre-PMF time on any of the following?*

1. Trying to accelerate growth before the value hypothesis is validated
2. Worrying about competition
3. Negotiating a corporate partnership
4. Building barriers to entry (patents, exclusives, moats)
5. Building brand (agencies, PR, design polish for its own sake)
6. Maximizing margins
7. Scaling infrastructure, team, or sales motion before product is loved by ten strangers

If yes to any, surface the cost. Each item is pre-PMF time spent on post-PMF work. Recommend cancel, defer, or delegate until PMF is confirmed. Reference `decision-making/finding-pmf.md` § "Distractions to finding PMF."

## Output structure

```
## State of play
[One paragraph: where the user is in the PMF process. Pre-experiment, mid-experiment, or post-experiment with a specific result.]

## Leap of faith
[The one belief that must be true. Quote the user's version, sharpen if needed. One sentence.]

## Value hypothesis
[What / Who / How. Each blank filled with a specific, non-generic answer. If any blank is generic, flag it and sharpen.]

## What to test next
[The smallest experiment that would falsify the leap of faith. Specific format (concept test / design sprint / concierge / Wizard of Oz / thin-slice MVP). Specific success and falsification criteria. Specific timeline.]

## Interpretation (if the user is post-experiment)
[Validated / falsified / surprised. The five-whys output if falsified. The unexpected signal if surprised.]

## Recommended next move
[Pivot the who / pivot the how / restart the what / double down on the surprise. With specific reasoning. Specific named segment or model change if pivoting.]

## Distractions flagged (if any)
[List of post-PMF activities the user is currently spending time on. Recommendation: cancel, defer, or delegate.]

## Sanity check before closing
[The single most important question the user should answer before the next session. Usually: which assumption is the next one to falsify, and what's the smallest experiment for it?]
```

## What good looks like

- The leap of faith is **one sentence**. If it's a paragraph, the user hasn't isolated it. Push back until it's one sentence.
- The value hypothesis is **specific in all four blanks** (insight, what, who, how). Generic blanks get pushed back, with the sharpening exercise from `decision-making/value-hypothesis.md`.
- The experiment is **the smallest one that would falsify the leap of faith**, not the smallest one that would prove the value hypothesis. Falsification beats confirmation.
- The next move is **named explicitly**: pivot the who (with the specific new segment), pivot the how (with the specific new model), restart the what (with the new insight), or savor the surprise (with the specific surprise to double down on). Not "iterate." Not "keep going."
- The distractions check is **applied honestly**, even when the user wishes it weren't. Pre-PMF time spent on post-PMF work is the most common founder failure mode.
- **Cites the substrate**: every recommendation references the right section of `decision-making/finding-pmf.md` or `decision-making/value-hypothesis.md`. The skill is a coach; the docs are the source.

## Anti-patterns

- **Conflating leap of faith with value hypothesis.** The leap of faith is upstream. Surface it on its own line. If the user resists separating them, run the decomposition explicitly before moving on.
- **Designing an MVP that tests five assumptions at once.** Each assumption needs its own test. Pick the most upstream one. The discipline is hard precisely because it feels slow.
- **Adding features when an experiment fails.** Adding features doesn't create desperation. Almost always, the right pivot is changing the who. Push back if the user proposes "let's add feature X" as the fix for a failed experiment.
- **Skipping the distractions check.** Founders who are pre-PMF gravitate to post-PMF work because it feels productive. The check catches this. Don't skip it just because the conversation feels productive.
- **Treating "savor the surprise" as the default response to any signal.** It's the exception, not the rule. The surprise has to be specifically positive on a *different* dimension than the original hypothesis, and behaviorally observable (a segment buying, a feature being used heavily). Vague "good feedback" is not a surprise to savor.
- **Restarting too easily.** Restarts have a much lower success rate than pivots. If the five-whys can point to a pivot of the who, run the pivot. Reserve restarts for the case where the insight itself is wrong.
- **Treating need as a signal.** A customer who says "this would be useful" is not desperate. Push the user past attitudinal signals to behavioral ones (the four desperation signals).

## Chain with pm-value-hypothesis-tester and pm-red-team

Two natural chains, both cheap:

- **Before designing the experiment**, run the output of step 2 (the sharpened value hypothesis) through `pm-value-hypothesis-tester`. The tester applies the static pressure-test (insight quality, who specificity, how mechanics, kill criterion, gut check). Surfaces holes before resources are committed.
- **After the recommendation**, run the recommended next move through `pm-red-team`. The red-team applies a different lens (competitive, viability, stakeholder) and catches what the coaching pass missed. Especially valuable before a restart decision.

Both passes are cheap to run and routinely surface holes the founder didn't see.

## How to invoke

Common invocation patterns:

- *"Use pm-pmf-coach. I've been running customer interviews for two months and they're polite but nothing's converting. What do I do next?"*
- *"Use pm-pmf-coach. We just shipped our MVP. Three of ten beta users paid, one is using it daily, two churned in week one. What does this tell us?"*
- *"Use pm-pmf-coach. I have three candidate segments and I can't decide which to go after first."*
- *"Use pm-pmf-coach to walk through the value hypothesis for the new product line my company is launching. We have PMF on the core product but this is a new bet."*

If the user invokes this skill on a product that has confirmed PMF and is now in growth mode, respond: *"This skill is the pre-PMF discipline. Your product looks post-PMF — consider `pm-funnel-critic` or `pm-metrics-critic` for the growth-stage questions."*
