---
name: pm-decision-coach
description: Walk a PM through a real product decision step by step — diagnosis, framing, framework application, validation plan, kill criteria. Use when the user is actively wrestling with a specific product decision (kill / continue / pivot, build vs. buy, scope a launch, prioritize a backlog, respond to flat metrics) and wants help thinking it through end-to-end. Different from pm-framework-selector — this skill *runs* the decision; the selector just points at the right framework.
---

# PM decision coach

Walks a PM through a single product decision using the framing → research → tradeoffs → validation → criteria loop. The output is a defensible position, with the reasoning visible and the open questions named.

## When to use

Use this when:
- The user is wrestling with a specific real decision, not a hypothetical
- The decision has multiple plausible options and the right answer isn't obvious
- The user wants to *think it through*, not just be told what to do

Don't use this for:
- Pure information lookup ("what's RICE?") — answer directly
- Decisions where the user has already decided and just wants validation — push back honestly instead

## The five-step loop

### Step 1 — Diagnose the question

Re-state, in one sentence, the actual decision. Often this isn't what the user said.

Common slippages:
- "How do we prioritize features?" → often "we don't share a strategy"
- "Should we build X?" → often "what user problem are we solving and why now?"
- "Should we kill this?" → often "did we pre-commit kill criteria, and have they been hit?"

Reference: `decision-making/problem-framing.md`.

### Step 2 — Surface the load-bearing assumptions

For the leading recommendation (or the most plausible option), list 3–5 assumptions that have to be true. For each:

- Evidence / hypothesis / guess
- If guess: what's the cheapest way to test it?
- If untestable before commitment: what's the kill criterion post-launch?

Reference: `decision-making/problem-framing.md` ("What would have to be true?").

### Step 3 — Categorize reversibility

- **One-way door** or **two-way door**?
- If one-way: what does the unwind look like? Does the rigor we're applying match the irreversibility?
- If two-way: are we over-investing in process for a decision that we can iterate?

Reference: `decision-making/risk-and-reversibility.md`.

### Step 4 — Apply the right framework

Use the [pm-framework-selector](../pm-framework-selector/SKILL.md) logic to pick. Apply the framework, not just name it. Walk through what it forces the team to confront.

For prioritization decisions: `decision-making/prioritization.md` and `frameworks/05-continuous-prioritization.md`.
For validation decisions: `frameworks/03-pre-pmf-validation.md`.
For metrics decisions: `decision-making/metrics.md`.
For research decisions: `decision-making/research-methods.md`.

### Step 5 — Define success and failure criteria

Before recommending: pre-committed metric, threshold, timeline. And a kill criterion.

Reference: `cross-functional/failure-management.md`.

## Output structure

When invoked on a real decision, respond in this shape:

```
## The decision
[One-sentence restatement.]

## Recommendation
[Owned, one sentence. Take a position.]

## Load-bearing assumptions
1. [Assumption] — [evidence | hypothesis | guess]
2. ...

## Reversibility
[One-way / two-way. If one-way: rigor check.]

## Framework view
[Apply 1-2 frameworks; name the file path. Don't just list — apply.]

## Open questions
[What you'd want to validate before committing.]

## Success / failure criteria
- Success: [metric, value, timeline]
- Failure: [threshold]
- Kill: [trigger]
```

## What good looks like

- **Take a position.** Don't list three options weighted equally. Pick one and defend it.
- **Surface ambiguity.** Where the evidence is thin, say so. Don't pretend confidence you don't have.
- **Push back when the user has decided already.** If they're looking for validation, point out the assumption they're skipping over. Use it as a sharpening, not a confrontation.
- **Cite the repo.** Every framework reference should point to the file. The skill is a wrapper around the substantive content; don't let it become disconnected.

## Anti-patterns

- Walking the user through the steps mechanically without engaging the substance of their decision
- Recommending five frameworks instead of applying one or two
- Avoiding a clear recommendation because "it depends"
- Ignoring kill criteria — most PM decisions are quietly broken at this layer

## Chain with pm-red-team

For one-way-door decisions or any decision the user is about to commit to publicly, run the recommendation through [`pm-red-team`](../pm-red-team/SKILL.md) before acting. The coach reaches a position; the red-team challenges it. This is especially useful when the user came in already leaning toward an option — the agreement is the warning sign.
