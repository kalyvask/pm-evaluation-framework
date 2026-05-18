---
name: pm-stakeholder-tracker
description: Cross-project stakeholder tracking — who you owe responses to, who owes you, last interaction date, open commitments per person. Reads cross-project and per-project stakeholder files plus recent Granola and Gmail signal. Surfaces relationships drifting toward neglect and commitments hanging in the gap between meetings. Use weekly or before any big stakeholder push (board prep, exec review, customer escalation cycle).
---

# PM stakeholder tracker

Stakeholder relationships are the load-bearing structure of PM work, and they fail silently. A senior stakeholder you haven't spoken to in three weeks is not yet a problem; in seven weeks they're a problem you can't easily fix.

This skill maintains the cross-cutting view of every stakeholder, surfacing who's at risk of going cold, who has open commitments hanging, and who needs proactive attention.

## When to use

- Weekly, as part of or following `pm-weekly-review`
- Before any high-stakes period (board prep, fundraise, exec review, customer escalation)
- When the user notices a relationship feels off and wants the full picture
- Implicitly chained from `pm-meeting-debrief` when a meeting changes commitments across multiple stakeholders

Don't use when:
- The user is asking about a single project (project's `stakeholders.md` is the right unit)
- The user wants to draft for a specific stakeholder (use `pm-inbox-triage` instead)
- No stakeholders.md files exist yet — surface that and ask the user to populate

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, all project state, and cross-project stakeholders.

### 2. Build the full stakeholder list

Aggregate:

- `pm-state/stakeholders.md` (cross-project)
- `pm-state/projects/<project>/stakeholders.md` for each active project
- De-duplicate (people who appear across projects).

For each unique stakeholder, capture:

- Name, role, org
- All projects they touch
- Cross-project priority (from `you.md`)
- What they care about
- Comms preferences

### 3. Pull recent interaction signal

For each stakeholder:

- Last interaction date from stakeholder files
- Recent Granola transcripts they appeared in (last 30 days)
- Recent Gmail threads they were on (last 30 days, if accessible)
- Open commitments (you to them, them to you) across projects

### 4. Categorize each stakeholder

Four categories:

- **Hot.** Recent interaction (within 7 days), no slipped commitments. Maintaining well.
- **Warm.** Recent interaction (within 14 days), maybe a small slip or a soft commitment hanging. Acceptable but watch.
- **Cooling.** No interaction in 14-30 days, or a firm commitment past its date. Needs attention this week.
- **Cold.** No interaction in 30+ days, or a multi-week commitment slip. Relationship is at risk.

Senior stakeholders (per `you.md` priorities) get a tighter threshold: cooling at 10 days, cold at 21 days.

### 5. Identify hidden risks

A few patterns to flag specifically:

- **Stakeholders cooling at the same time across multiple projects.** Often means the user is overloaded somewhere upstream, not just neglecting one relationship.
- **One-sided commitment pattern.** You always owe them; they never owe you. Or vice versa. Both signal an imbalanced relationship worth naming.
- **Stakeholders who haven't been added to any project file but appear in recent Granola or Gmail signal.** Likely missing from the stakeholder list and need to be added.
- **Multiple stale "they owe you" commitments from the same person.** This person has a pattern of not delivering; the user should consider what to do about it (cadence, escalation, or accepting it).

### 6. Recommend specific actions

For each cooling or cold stakeholder, propose a specific action:

- A check-in message draft (in the user's voice)
- A specific meeting to schedule
- A follow-up on a hanging commitment

Cap the action list at 5 to 7 across all stakeholders. Forcing the user to act on 20 cold stakeholders is unrealistic; the goal is to surface the ones that most need attention this week.

### 7. Output the tracker report

Use the structure below. Optimize for "what do I act on this week" rather than "here's a complete dashboard."

## Output structure

```
# Stakeholder tracker — YYYY-MM-DD

## Summary

- [N] hot, [N] warm, [N] cooling, [N] cold
- [N] hidden risks flagged
- [N] specific actions recommended this week

## Cold (urgent attention)

For each:

**[Name], [role]**
- Last interaction: [date, what]
- Open commitments: [list]
- Why this matters: [their priority level, relationship risk]
- Recommended action: [draft message / schedule meeting / specific follow-up]
- Draft message (if applicable):
  ```
  [body in user's voice]
  ```

## Cooling (this week)

For each:
**[Name], [role]** — last interaction [date], [open commitments]. Suggested action: [...]

## Warm and hot (just for visibility)

[Short list, no action needed.]

## Hidden risks

For each pattern flagged:
- [pattern description]
- Affected stakeholders: [list]
- Likely cause: [your read]
- Suggested check: [...]

## Stakeholders to add

People appearing in recent Granola/Gmail but not in any stakeholders file:
- [name] — appeared in [N] meetings/threads, projects: [list]
- Propose adding to: `pm-state/projects/<name>/stakeholders.md` (or cross-project file)
- [Add / skip / let me decide]

## Open commitments — summary

**You owe (top items):**
- [name]: [item] — due [date]
- ...

**They owe you (top items):**
- [name]: [item] — due [date]
- ...

---

*If multiple stakeholders are cooling at once, run `pm-weekly-review` for the bigger picture.*
```

## What good looks like

- **Tight action list.** 5 to 7 specific actions, not 20. The bar is "what would actually get done this week."
- **Senior-stakeholder weighting.** A senior stakeholder cooling at 12 days is more urgent than a junior one cooling at 28 days. The threshold isn't symmetric.
- **Specific drafts, not generic check-ins.** "Hey, hope you're well, just checking in" is a waste of everyone's time. Reference the actual hanging commitment or context.
- **Catches the patterns.** Multiple stakeholders cooling at once often means the user is upstream-overloaded. Naming the pattern is more useful than naming each instance.
- **Surfaces missing stakeholders.** The agent should flag people who showed up in Granola/Gmail but aren't in any stakeholders file. The user can decide whether to add them.

## Anti-patterns

- **Listing every stakeholder every time.** A useful tracker filters to the people who need action. A complete dashboard of all 40 stakeholders is unread.
- **Generic check-in messages.** Reference the actual context: the last conversation, the hanging commitment, the upcoming decision. Generic messages are worse than no message.
- **Treating all stakeholders symmetrically.** Senior stakeholders, customers, and team leads need tighter cadences than peripheral peers. Weight accordingly.
- **Adding stakeholders to files without asking.** Surface the gap; let the user decide whether to capture.
- **Drafting messages that auto-send.** Never. Drafts only.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-weekly-review`** — runs this skill (implicitly) for the stakeholder cold-check section.
- **`pm-inbox-triage`** — stale threads from this skill often turn into substantive-response items there.
- **`pm-meeting-debrief`** — when a debrief changes commitments across multiple stakeholders, chain to this skill to update the cross-cutting view.

## How to invoke

Common invocation patterns:

- *"Run stakeholder tracker."*
- *"Who am I about to lose?"*
- *"Show me my cold stakeholders."*
- *Used implicitly by `pm-weekly-review`.*

If invoked when no stakeholders files exist, respond: *"You don't have stakeholders captured in pm-state yet. To use this skill, populate at least `pm-state/stakeholders.md` with your cross-project stakeholders. Want me to scaffold from your Granola attendees and Gmail correspondents over the last 30 days?"*

If the user asks to actually send any of the drafted messages, refuse: *"Drafts only. Copy and send from your email client so you can edit one last time before it lands."*
