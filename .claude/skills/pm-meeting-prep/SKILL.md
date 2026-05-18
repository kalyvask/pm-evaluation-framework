---
name: pm-meeting-prep
description: Given a calendar event (or upcoming meeting context), draft a one-page meeting brief. Identifies attendees, pulls relevant project state and stakeholder context, surfaces last interaction and open commitments, and drafts an opinionated prep doc. Use 15-30 minutes before any meeting that matters — exec review, stakeholder check-in, customer call, decision point.
---

# PM meeting prep

Drafts a one-page brief for an upcoming meeting. Pulls signal from calendar (time, attendees, topic, prior thread), stakeholders.md (who they are, what they care about), the relevant project's state (open questions, current focus, recent decisions), and recent Granola transcripts (what was last discussed with these people).

The output is structured, opinionated, and short. The PM walks in knowing what's at stake, what they want, what the other side likely wants, and what they don't yet have an answer to.

## When to use

- 15 to 30 minutes before any meeting where the stakes are non-trivial
- Before an exec review or 1:1 with a senior stakeholder
- Before a first interaction with someone new
- Before a meeting on a decision the user is wrestling with

Don't use when:
- The meeting is a recurring internal standup with no specific agenda
- The user has already prepped manually (don't duplicate)
- The meeting is purely social

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, the project list, cross-project stakeholders.

### 2. Identify the meeting

If the user named a specific meeting, use that. Otherwise:

- Pull today's calendar (and tomorrow's, if it's evening)
- Identify the next meeting that matches the user's prep description
- If ambiguous, ask: *"You have [N] meetings in the next 24 hours. Which one — [list with times]?"*

### 3. Pull meeting context from calendar

For the chosen meeting, extract:

- Time, length, location/video link
- Title and description
- Attendees (names, organizations if external)
- Whether the user owns or attends
- Any meeting notes or attached docs in the calendar entry
- Prior occurrences in the same recurring series, if applicable

### 4. Identify the project

Most meetings tie to a specific project. Determine which:

- If the meeting title or description names a project, use that
- If attendees match a project's stakeholders.md, use that project
- If unclear, ask the user

If the meeting is cross-project (e.g., a 1:1 with a senior manager), skip the project step and rely on cross-project stakeholders.md.

### 5. Pull stakeholder context

For each named attendee:

- Read their entry in `pm-state/stakeholders.md` and/or `pm-state/projects/<name>/stakeholders.md`
- Identify: what they care about, what their constraints are, comms preferences
- Note: last interaction date and what happened
- Note: open commitments (you to them, them to you)

If a stakeholder isn't in any stakeholders.md file, surface that gap: *"I don't have stakeholder context for [name]. Want me to flag this as 'first interaction' and capture their notes after the meeting?"*

### 6. Pull recent transcripts with these people

Query Granola for transcripts that include these attendees in the last 30 days. Read the summaries (not full transcripts). Extract:

- The thread of the conversation
- Decisions made
- Open questions left hanging
- Commitments not yet captured

### 7. Pull relevant project state

If the meeting is project-specific, read the project's:

- `status.md` — current focus, north star, kill criterion
- `open-questions.md` — questions you might raise
- `decisions.md` — recent decisions the other side might ask about
- `todos.md` — items you owe them, items they owe you

### 8. Draft the brief

Use the output structure below. Be opinionated — name what you want, name what the other side likely wants, name what you don't have an answer to.

The brief is NOT just a context dump. It is a structured prep doc with a point of view.

### 9. Surface the unanswered question

The single most useful section of the brief: **what's the question you don't have an answer to but might be asked?** Surface it explicitly. Either prep an answer, or pre-commit to *"I don't have an answer yet, here's when I will."* Walking into a meeting unprepared for the obvious question is the most common avoidable failure.

## Output structure

```
# Meeting prep: [Meeting title] — [Date HH:MM]

## TL;DR
[One paragraph. The stake, your ask, the likely friction.]

## Attendees and context

For each attendee:
**Name, role** — [cares about: X. Last interaction: [date, what]. Open commitments: [list or none].]

## Your three asks

What you want to walk out with:
1. ...
2. ...
3. ...

## What they likely want

What you predict the other side wants from the meeting:
- ...

## The question you don't have an answer to

[The specific question that, if asked, would be hardest. Either pre-commit to an answer or pre-commit to "not yet, by [date]".]

## Recent context with these people

- [date] — [what was discussed, key decision or commitment]
- [date] — ...

## Open project context (if applicable)

From `projects/<name>/`:
- Current focus: [...]
- Open questions you might raise: [...]
- Recent decisions they might ask about: [...]

## Suggested opener

One line you can lead with that respects their time. Optional.

## After the meeting

Reminder to run `pm-meeting-debrief` against the Granola transcript to close the loop.

---

*Brief generated [HH:MM]. Edit your project's `todos.md` and `stakeholders.md` after the meeting based on what was discussed.*
```

## What good looks like

- **Specific, not generic.** Generic "discuss roadmap" briefs are useless. Specific "they will ask about the Q3 launch date you said was 'late September,' but the latest engineering estimate is October 15. Prep an answer." is the bar.
- **Names the question you don't want asked.** The most useful section. PMs avoid this in their own prep because it's uncomfortable. The agent shouldn't.
- **Cites the prior context.** Last meeting was [date], you committed to [X], status is [Y]. The other side will remember; you should too.
- **Short.** One page. If it's longer, the agent is including noise.
- **Stays in the user's voice when drafting an opener.** No "I wanted to circle back to discuss..." If the user is direct, the opener is direct.

## Anti-patterns

- **Dumping all known context into the brief.** A meeting prep is not a stakeholder dossier. Filter to what matters for *this* meeting.
- **Soft "consider preparing for..." language.** Either pre-commit to an answer or pre-commit to saying you don't have one.
- **Inventing stakeholder context.** If you don't know what they care about, surface the gap rather than guess. A wrong guess in a prep doc produces a wrong answer in the meeting.
- **Skipping the question-you-don't-want-asked section.** This is the single most useful part. Always include it, even when it's uncomfortable.
- **Drafting a prep brief that the user could have written without the agent.** If the brief is just a restatement of public meeting info, the agent isn't adding value. The value is the cross-referenced context.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-meeting-debrief`** — after the meeting, to close the loop on commitments and update project state.
- **`pm-decision-coach`** — if the meeting is about a specific decision and the user wants help framing the conversation.
- **`pm-red-team`** — if the meeting is high-stakes (board, exec review, customer escalation), chain to pm-red-team on the brief to stress-test what could go wrong.

## How to invoke

Common invocation patterns:

- *"Prep me for my 10am with Sarah."*
- *"Meeting prep for the Stanford check-in."*
- *"What do I need to know for my next meeting?"*

If invoked when the user has no meetings in the next 24 hours, respond: *"You don't have any meetings on the calendar in the next 24 hours. Did you mean a specific meeting later this week?"*

If invoked on an internal recurring meeting (e.g., a daily standup) where there's no specific stake, ask: *"This looks like a recurring standup with no specific agenda. Want me to run a short version, or skip the prep?"*
