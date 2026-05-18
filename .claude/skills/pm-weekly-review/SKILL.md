---
name: pm-weekly-review
description: Run the Friday PM weekly review — what got done, what slipped, what's worth renegotiating, what's on next week. Reads each active project's state, pulls the week's Granola transcripts and calendar, surfaces patterns across projects (stakeholders going cold, decisions deferred, todos rotting). Writes the review to `pm-state/inbox/YYYY-MM-DD-weekly-review.md`. Use late Friday afternoon before logging off.
---

# PM weekly review

The end-of-week version of `pm-morning-brief`. Pulls a week's worth of signal and produces a structured retrospective that the user reads in 10 minutes before logging off.

Surfaces patterns that don't show up at the daily level: stakeholders the user hasn't talked to in two weeks, decisions that keep getting punted, TODOs that have rotted, projects that lost momentum without anyone naming it.

Saves the review to `pm-state/inbox/YYYY-MM-DD-weekly-review.md` so the user can reference it next Monday.

## When to use

- Friday afternoon, before logging off
- Late on the last working day of a sprint or quarter
- Before a quarterly business review or board prep, as a "what happened this quarter" digest

Don't use when:
- It's earlier in the week (use `pm-morning-brief` instead)
- The user is asking about a specific project (run that project's status check directly)
- No pm-state exists. Surface that and stop.

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, the project list, cross-project stakeholders.

### 2. Pull the week's calendar

The last 7 days of calendar entries. For each meeting, identify:

- Whether it happened (cancelled meetings count differently)
- Whether it had a Granola transcript
- Whether the transcript got a debrief (cross-reference `pm-meeting-debrief` history)

Flag meetings that happened but never got debriefed — those are likely sources of uncaptured commitments.

### 3. Pull the week's transcripts

Use the Granola MCP. For each transcript, identify:

- The project it tied to
- Commitments made (yours and theirs)
- Decisions made
- Whether the commitments are captured in `todos.md`
- Whether the decisions are captured in `decisions.md`

Surface uncaptured commitments and decisions as Friday cleanup items.

### 4. Diff project state vs. last week

For each active project:

- Read current `todos.md`, `decisions.md`, `open-questions.md`
- Compare to last Friday's review (if it exists in `inbox/`)
- Identify: what closed this week, what's new, what's been hanging unchanged

If `todos.md` looks identical to last week's, the project may be stuck. Surface that.

### 5. Stakeholder cold-check

For each stakeholder in `stakeholders.md` (cross-project) and active projects:

- When was the last interaction?
- Are there open commitments owed to them?

Surface stakeholders the user hasn't spoken to in 14+ days, especially senior ones with open commitments. These are the relationships most at risk of going cold.

### 6. Slippage check

Across all projects:

- TODOs past their due date, not marked done
- Decisions that have been "to be made" for 3+ weeks
- Open questions in "Active" status that haven't moved

These are the patterns the daily brief misses. The weekly view catches them.

### 7. What worked this week

A short positive section. The wins, the closed loops, the meetings that landed. Important for two reasons: keeps the review balanced, and reinforces patterns to repeat.

### 8. What to renegotiate next week

Specific things to push back on. A commitment date that's no longer realistic. A scope that grew without re-approval. A decision that needs the user's input before Monday.

This is the action section. Each item gets an owner (almost always the user) and a specific next step.

### 9. Next week's setup

A one-paragraph forward look. Key meetings, decisions due, deliverables expected.

### 10. Write the review to disk

Save to `pm-state/inbox/YYYY-MM-DD-weekly-review.md` using the output structure below. Friday-dated.

If a review already exists for this week, surface that before overwriting.

## Output structure

```
# Weekly review — [Friday YYYY-MM-DD]

## TL;DR
[One paragraph honest take. Was this a productive week? What pattern stood out?]

## What worked

[2-4 bullets. Wins, closed loops, meetings that landed. Be specific.]

## What slipped

For each:
- [project] [item] — [N days overdue / N times deferred]
- ...

## Decisions that have been hanging

Decisions that have been "to be made" for 3+ weeks:
- [project] [decision] — first surfaced [date], not yet decided
- ...

## Stakeholders going cold

Stakeholders not interacted with in 14+ days:
- [name], [role] — last interaction [date], open commitments [list]
- ...

## Uncaptured commitments

Meetings this week with no debrief:
- [date] [meeting] — [N attendees]. Run `pm-meeting-debrief` before EOD?

## Project state diffs

For each active project, one paragraph: what moved, what didn't, what's the binding constraint right now.

**[Project A]**
- Moved: ...
- Didn't move: ...
- Binding constraint: ...

[Repeat for each project.]

## Patterns worth naming

Cross-project signal. *"Three different projects have stakeholders going cold — common cause?"* Or *"Two decisions have been deferred to 'next week' three weeks running — pattern."*

## What to renegotiate next week

For each:
- [item] — [why it's worth renegotiating] — [proposed action]
- ...

## Next week's setup

One paragraph. Key meetings, decisions due, deliverables expected. The "Monday morning prep" for next week.

---

*Review generated [HH:MM]. Update `pm-state/projects/<name>/status.md` files over the weekend if anything has shifted materially.*
```

## What good looks like

- **Catches patterns daily misses.** A todo overdue by one day is daily noise. A stakeholder cold for 14 days is weekly signal.
- **Names what's stuck, not just what's slipping.** "Decision X has been deferred 3 weeks running" is the move. The weekly view sees the rhythm.
- **Cross-project signal.** Patterns that show up in multiple projects — same kind of slip, same kind of stakeholder going cold — are worth naming.
- **Specific renegotiation moves.** "Push back on [X] before Monday" beats "consider whether to push back."
- **Includes wins.** A weekly review that's all complaints rots the user's morale. Name what worked. Calibrates the rest.

## Anti-patterns

- **Treating the weekly review as a longer morning brief.** Different time horizon, different patterns. The weekly view should NOT just be 5x the daily volume.
- **Long lists of everything.** Filter to the patterns that matter. If three TODOs slipped this week but five slipped each prior week, that's actually a positive trend — say so.
- **Skipping the "what worked" section.** Important for calibration and morale. Always include.
- **Generic "consider X" recommendations.** Renegotiation actions should be specific. Either propose the specific message or skip the recommendation.
- **Regenerating an existing weekly review without confirming.** If a review exists for this week, ask before overwriting.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-meeting-debrief`** — for uncaptured meetings flagged in the review.
- **`pm-stakeholder-tracker`** — for the cold-stakeholder section, especially if multiple stakeholders are going cold.
- **`pm-decision-coach`** — for decisions that have been hanging too long; chain to force resolution.

## How to invoke

Common invocation patterns:

- *"Run my weekly review."*
- *"What slipped this week?"*
- *"End-of-week brief."*
- *Scheduled task firing at 4pm Friday.*

If invoked early in the week, ask: *"It's only [day]. Want me to run a partial-week review, or do you mean morning brief / daily check-in?"*

If the same week already has a review, ask before regenerating: *"You already have a weekly review from [day]. Regenerate or refer to existing?"*
