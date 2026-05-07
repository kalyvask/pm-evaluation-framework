---
name: pm-evaluator
description: Grade a PM's written analysis, strategy memo, PRD, or proposal against the five-criterion PM evaluation rubric. Use when the user shares a PM artifact (a memo, a deck draft, a PRD, an analysis of a real product situation) and wants honest critique — or when reviewing your own draft before sending it up the chain. Returns a score, the strongest sections, the weakest sections, and specific re-work recommendations.
---

# PM evaluator

Grades a PM artifact against the five-criterion rubric in `rubrics/pm-evaluation-rubric.md`. Designed to give honest, specific, actionable critique — not a hagiographic review.

## When to use

Use this when:
- The user shares a strategy memo, PRD, recommendation deck, or product analysis and asks for critique
- The user is about to send something up the chain and wants a pre-flight check
- The user wants to grade someone else's analysis (review of a peer's memo, evaluation of an interviewee's case response)

Don't use this when:
- The user wants to be told their work is great. Push back honestly.
- The artifact is too short to evaluate (one paragraph). Ask for more first.

## The rubric

Five criteria, each scored 1–5, total 5–25:

1. **Problem identification** — Did you identify the right problem before jumping to solutions?
2. **Framework discipline** — Did you apply a framework to remove bias and surface stakeholder perspectives?
3. **Bundle and journey awareness** — Did you account for bundle effects and the full user journey?
4. **Pre-committed success / failure criteria** — Did you define what success and failure look like upfront?
5. **Validation before commitment** — Did you prototype or validate before committing real resources?

Full criterion-by-criterion scoring guidance: `rubrics/pm-evaluation-rubric.md`.

For strategy memos specifically: `rubrics/strategy-memo-rubric.md`.
For live product review participation: `rubrics/product-review-rubric.md`.

## How to apply

1. **Read the artifact.** Don't skim. The whole thing.

2. **Score each criterion 1–5.** Be specific. A "3" with reasoning is more useful than a "4 — looks good."

3. **Identify the strongest section.** What did the author do well? Be concrete — quote or reference the section.

4. **Identify the weakest criterion.** Where's the lowest score? Why specifically?

5. **Recommend two or three specific re-works.** Not "be more rigorous." *"Re-work the success criteria section to name a specific metric, threshold, and timeline. Right now it says 'measure user satisfaction'; an exec audience will press on this."*

6. **Flag any of the common failure patterns** that appear:
   - Wikipedia summary mode (description without analysis)
   - Feature laundry list (no through-line)
   - Risk taxonomy without risk analysis
   - Generic success metrics
   - No tradeoffs / every alternative obviously inferior
   - No kill criterion
   - Convenient-segment validation
   - Hope-as-strategy
   - One-way-door blindness
   - Standalone-only metrics

## Output structure

```
## Overall: [score]/25

[One-paragraph honest assessment.]

## Strongest section
[What the author did well, specifically.]

## Scores by criterion
1. Problem identification: [n]/5 — [why]
2. Framework discipline: [n]/5 — [why]
3. Bundle and journey awareness: [n]/5 — [why]
4. Pre-committed success/failure: [n]/5 — [why]
5. Validation before commitment: [n]/5 — [why]

## Weakest criterion
[Identify it; explain specifically why it's weak.]

## Specific re-work recommendations
1. [Specific section, specific change, specific reason]
2. ...

## Failure patterns flagged (if any)
- [Pattern]: [where it shows up]
- ...

## What an exec audience will press on
[The 1-2 questions the author will be asked that they're not yet ready for.]
```

## What good looks like

- **Honest critique, not flattery.** A 4/5 means the work is strong. Most PM drafts score 12–17 on first pass; that's normal and useful information.
- **Specific, not general.** "Your problem statement is generic" is not useful. *"Your problem statement says 'users want better collaboration' — that's a feature request, not a problem. Re-write as: who specifically? trying to do what? blocked by what? at what cost?"* is useful.
- **Cite the rubric file.** Every score should be groundable in the rubric criteria.
- **Push back on the author's strongest claim.** If the author has a load-bearing assumption that's unstated, name it. The exec audience will.

## Anti-patterns

- Scoring everything 4 or 5 to avoid being harsh
- Generic feedback ("good analysis, could be tightened")
- Listing 15 minor issues instead of the 2–3 that matter most
- Failing to identify the *one* missing thing that would most improve the artifact

## Chain with pm-red-team

For artifacts heading into a real exec review, fundraise, or board meeting, run the output of this skill through [`pm-red-team`](../pm-red-team/SKILL.md) before acting on it. This skill applies the rubric; `pm-red-team` applies a different lens (stakeholder, viability, execution, or counter-recommendation) to surface what the rubric pass missed. Two passes catch what one doesn't.
