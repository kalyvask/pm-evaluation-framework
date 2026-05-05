---
name: pm-prd-drafter
description: Draft or critique a PRD against the repo's PRD template and problem-framing rubric. Use when the user is starting a PRD, sharing a PRD draft for review, or stuck on a specific PRD section (problem statement, success metrics, scope, kill criteria). Pushes back on vague problem statements, generic success metrics, and feature-laundry-list scope. Returns either a structured PRD draft or a section-by-section critique with specific re-writes.
---

# PM PRD drafter

Helps a PM produce a PRD that holds up under exec review. The PRD template at `templates/prd-template.md` is the substrate. The job of this skill is to make sure each section earns its keep — and to push back hard when sections are filler.

## When to use

Use this when:
- The user is starting a new PRD and has the problem in their head but not on the page
- The user shares a PRD draft and wants critique before circulating it
- The user is stuck on a specific section (most often: problem statement, success metrics, or scope)
- The user is converting a vague idea ("we should do AI sharing") into a real artifact

Don't use this when:
- The decision hasn't been framed yet — send to `pm-decision-coach` or `frameworks/01-strategy-and-discovery.md` first
- The artifact already exists and the user wants a full evaluation, not a re-write — use `pm-evaluator`
- The user wants a launch plan, not a PRD — use `pm-launch-reviewer`

## How to apply

1. **Pin the problem before anything else.** Use the problem template from `decision-making/problem-framing.md`: *[specific user] is trying to [specific job] but [specific blocker], which costs them [specific cost].* If any of the four slots is generic ("users", "better experience", "blocked", "frustration"), stop and re-write before any other section. A weak problem statement makes every later section meaningless.

2. **Force a real "why now."** Reference `templates/prd-template.md` § Why now. If the user can't name what changed (new capability, behavior shift, competitive threat, regulatory event), the PRD isn't ready. Say so and recommend deferring.

3. **Translate solution into user-outcome language.** "When [user] tries to [job], they will [new experience], which produces [new outcome]." Reject feature-list scope. If the user types "ship X, Y, Z," ask what outcome each one produces.

4. **Demand pre-committed success and kill criteria.** Pull from `decision-making/metrics.md` — every load-bearing strategic assumption needs a falsifying metric. "Increase engagement" is not a success metric. A specific metric, threshold, segment, and timeline is.

5. **Stress-test scope with the bundle/journey lens.** Reference `rubrics/pm-evaluation-rubric.md` criterion 3. What's upstream (procurement, admin, onboarding)? What's downstream (support, billing, downstream teams)? If the PRD is silent on these, name the gap.

6. **Flag the load-bearing assumption.** Every PRD has one — the thing that, if false, makes the rest fall apart. Surface it explicitly. The exec audience will.

## Output structure

For a **fresh draft**, produce the full PRD using `templates/prd-template.md` headings, with the problem and success-criteria sections fully concrete.

For a **critique**, use:

```
## TL;DR
[One-paragraph honest take. Is this PRD ready to circulate? Yes / no / not yet, why.]

## Problem statement
**Verdict:** [Specific / generic / wrong-problem]
[Quote the current problem statement, then re-write it concretely.]

## Why now
**Verdict:** [Real / forced / missing]
[What changed, or why this section is empty.]

## Solution
**Verdict:** [User-outcome / feature-list]
[Translate any feature-list lines into outcome language.]

## Success / kill criteria
**Verdict:** [Falsifiable / generic / missing]
[For each criterion: name the metric, threshold, segment, timeline. Re-write any that fail this bar.]

## Scope and bundle
**Verdict:** [Journey-aware / surface-only]
[Name what's missing from the journey: procurement, admin, downstream.]

## Load-bearing assumption
[The one belief this PRD depends on. State it explicitly so the exec audience can attack it directly.]

## Two or three specific re-writes
1. [Section, current line, replacement line, reason.]
2. ...
```

## What good looks like

- The problem statement is specific enough that someone outside the team could repeat it back accurately.
- Every success metric is segment-specific and threshold-specific. Aggregate metrics ("DAU up") do not pass.
- The "why now" survives the question "what would have to be true for us to do this *next* quarter instead?"
- The scope section names what's *not* in scope and why — not just what is.
- The load-bearing assumption is named in the PRD itself, not buried in the appendix.

## Anti-patterns

- Letting a vague problem statement pass because the rest of the PRD is well-written. The problem statement is load-bearing.
- Accepting "we'll measure user satisfaction" as a success metric. Push for a specific metric, threshold, segment, timeline.
- Writing the solution as a feature list. Re-write into user-outcome language even if it's awkward at first.
- Skipping the bundle/journey check because the PRD is "just a feature." Most PRD failures live in the procurement/admin/downstream sections that weren't written.
- Critiquing 15 minor issues. Surface the 2–3 that, if fixed, would make the PRD substantially stronger.
