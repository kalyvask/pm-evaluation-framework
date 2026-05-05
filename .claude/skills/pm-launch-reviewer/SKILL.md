---
name: pm-launch-reviewer
description: Review a launch plan against the repo's launch-criteria template and failure-management playbook. Use when the user is preparing a launch (closed beta, limited GA, full GA) and wants a pre-flight review, or is staring at a checklist of "ready" gates that all happen to be owned by the same person. Surfaces missing gates, unowned criteria, vague readiness bars, and the one or two failure modes most likely to show up post-launch. Returns a gate-by-gate verdict and a launch-or-defer recommendation.
---

# PM launch reviewer

Reviews a launch plan and returns a gate-by-gate verdict against `templates/launch-criteria.md`, plus a failure-mode pass against `cross-functional/failure-management.md`. The job is to catch the things that look fine on paper but cause incidents in week one — unowned gates, vague readiness criteria, missing rollback plans, and over-confidence about user behavior.

## When to use

Use this when:
- The user has a launch date set and wants a pre-flight review of the plan
- The user has a "go / no-go" meeting coming up and wants to pressure-test their readiness story
- The user is debating soft launch vs. limited GA vs. full GA and wants the tradeoff written down
- A launch slipped or failed recently and the team is preparing the next one — bring the failure-management lens

Don't use this when:
- The product hasn't been built yet — that's a PRD problem, use `pm-prd-drafter`
- The launch already shipped and the user wants a postmortem — use `templates/blameless-postmortem.md` directly
- The decision is whether to launch *at all* — that's a strategy decision, use `pm-decision-coach`

## How to apply

1. **Confirm the launch type.** Soft launch (closed cohort), limited GA (named segments), or full GA. The readiness bar differs by an order of magnitude. If the launch type is fuzzy, pin it before reviewing anything else.

2. **Walk every gate from `templates/launch-criteria.md`.** Technical, product, GTM, support, legal/compliance, executive sign-off. For each gate, check three things:
   - Is there a *named* owner (a person, not a team)?
   - Is the readiness criterion *measurable* (a threshold, not a vibe)?
   - Is the criterion currently *green*, *yellow*, or *red*?

3. **Flag any gate where the same person owns both the gate and the criterion.** That's a self-graded gate. Either split ownership or accept that the gate is decorative.

4. **Run the failure-management lens.** From `cross-functional/failure-management.md`: what's the most likely failure in week one? What's the rollback path? Who has the authority to pull the plug, and at what threshold? If "we'll figure it out" is the answer to any of these, the plan isn't ready.

5. **Apply the bundle/journey check.** Reference `rubrics/pm-evaluation-rubric.md` criterion 3. Does the launch plan account for procurement, admin onboarding, support staffing, and any downstream team that will field questions? Most launch failures are *adjacent* failures — the feature works, but the support team didn't know it was launching.

6. **Recommend a launch type or a defer.** Don't hedge. If three gates are red, the plan isn't ready — say so, and name what would have to change for the plan to be ready by the original date.

## Output structure

```
## TL;DR
[One-paragraph verdict: launch as planned / downscale to limited GA / defer. With reason.]

## Launch type and date
**Confirmed:** [Soft / Limited GA / Full GA] on [date]
**Recommended:** [Same / different — why]

## Gate-by-gate
| Gate | Owner | Criterion | Status |
|---|---|---|---|
| Technical readiness | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |
| Product readiness | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |
| GTM readiness | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |
| Support readiness | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |
| Legal / compliance | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |
| Exec sign-off | [name] | [specific threshold] | 🟢 / 🟡 / 🔴 |

## Self-graded gates
[Any gate where the owner also defined the criterion — flag these.]

## Most likely week-one failure
[One specific failure mode. What's the leading indicator? What's the rollback path? Who pulls the plug?]

## Adjacent / journey gaps
[Procurement, admin, support staffing, downstream teams. What's not on the plan?]

## What would have to change
[If the recommendation is defer or downscale: what specific changes would make the original plan viable.]
```

## What good looks like

- Every gate has a named human owner, not a team.
- Every readiness criterion is measurable. "Tested" is not a criterion. "Latency p95 < 200ms across last 7 days of staging traffic" is.
- The week-one failure mode is a specific scenario, not a category. "Login failures during onboarding spike on day-one Slack post" beats "performance issues."
- The rollback plan names a person, a threshold, and a mechanism. "Rollback to feature flag off if error rate exceeds 2% sustained for 10 minutes; on-call eng has the toggle."
- The recommendation is unambiguous. Hedged recommendations ("could go either way") are not useful at a go/no-go meeting.

## Anti-patterns

- Greenlighting on the basis of "the team feels ready." Feelings are not gates.
- Accepting a gate where the owner is "TBD" or a team name. Get a person.
- Letting "we'll handle support load with the existing team" pass without checking the existing team's capacity for the launch week.
- Skipping the failure-mode pass because the launch plan looks comprehensive. The most comprehensive plans have the most blind spots.
- Recommending "downscale to soft launch" when the team has already committed externally. If that's the recommendation, name the external commitments that need to be reset and who owns resetting them.
