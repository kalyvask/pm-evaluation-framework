---
name: pm-morning-brief
description: Run the morning PM briefing. Pulls today's calendar, identifies meetings needing prep, surfaces commitments due today across projects, surfaces inbox threads needing attention, and identifies anything that slipped from yesterday's commitments. Writes the brief to `pm-state/inbox/YYYY-MM-DD-morning-brief.md`. Use first thing in the morning, before opening email or calendar.
---

# PM morning brief

The first thing the agent does each day. Pulls signal from multiple sources (calendar, email, pm-state TODOs, Granola transcripts from yesterday) and surfaces what needs attention today.

The brief is written to `pm-state/inbox/YYYY-MM-DD-morning-brief.md` so it persists and the user can refer back. The user reads it in five minutes, decides what to act on, and moves into the day.

This skill can be run manually or on a scheduled task (typically 7:30 to 8:00 weekdays).

## When to use

- First thing in the morning, before opening calendar or email
- After being out for a few days, as a "what happened while I was out" digest
- Before a high-stakes day where context loading matters

Don't use when:
- It's already late in the day. Use `pm-weekly-review` or just ask what's outstanding.
- The user already has today's brief loaded. Don't regenerate; refer to the existing one.
- No pm-state folder exists. Surface that and stop.

## How to apply

### 1. Chain to `pm-context-loader`

First step. Load `you.md`, the active project list, cross-project stakeholders.

### 2. Pull today's calendar

Use the calendar MCP to fetch today's events. For each event, capture:

- Time
- Title
- Attendees (named, not just count)
- Location or video link
- Whether the user owns the meeting or is a guest
- Any meeting description / agenda

### 3. Flag meetings needing prep

A meeting needs prep if any of:

- The user owns the meeting and there's no agenda written
- A senior stakeholder is on the invite (from `you.md` or stakeholders.md)
- The user has open commitments to someone in the meeting
- It's the first interaction with someone you don't have stakeholder context for
- The meeting is about a topic the user has open questions on (cross-reference `open-questions.md`)

For each meeting needing prep, note the specific reason. Don't flag every meeting — internal team standups usually don't need prep.

### 4. Surface commitments due today

Read each active project's `todos.md`. Identify items:

- Due today
- Owned by the user (`[me]` entries)
- Status not yet "Done"

List them with project tag: `[project] item due today`.

Also surface commitments others owe the user that are due today. These are different — the action is "follow up" rather than "do it."

### 5. Surface slippage (overdue items)

Items in `todos.md` with dates before today and not marked done. These are the highest-priority signal in the brief — most projects slip silently, and the morning brief is where the slip gets named.

Group slipped items by project. For each, note how many days overdue.

### 6. Inbox check

Pull recent Gmail threads via the Gmail MCP. Focus on:

- Threads received in the last 24 hours
- Threads where the user is the primary recipient (not just CC'd)
- Threads with attached deadlines mentioned in the body
- Threads from named stakeholders (cross-reference stakeholders.md)

Don't classify or draft replies in the morning brief — that's `pm-inbox-triage`. Just count and surface the high-attention ones.

### 7. Yesterday's loose threads

Read Granola transcripts from yesterday (use the Granola MCP). For each transcript:

- Identify commitments made (yours and theirs) — chain to `pm-meeting-debrief` patterns
- Check if they've been captured in the relevant project's `todos.md`
- Surface any commitments that haven't been captured

This catches the most common slippage: a verbal commitment made in a meeting that never made it to a written list.

### 8. Identify the top 3 today

Across all the signals above, name the three things that matter most today. Be opinionated. The user has limited attention; the brief should prioritize, not just list.

Criteria for "top 3":

- High-stakes meetings (exec review, customer call, decision point)
- Overdue commitments to senior stakeholders
- Open questions that block other work

If everything looks fine and nothing is urgent, say so. A clean brief is a useful signal too.

### 9. Write the brief to disk

Save to `pm-state/inbox/YYYY-MM-DD-morning-brief.md` using the output structure below. Use the user's local date.

If a brief for today already exists, surface that to the user before overwriting: *"You already have a brief for today. Regenerate or refer to existing?"*

## Output structure

```
# Morning brief — YYYY-MM-DD (weekday)

## Top 3 today
1. [the most important thing, with the why]
2. ...
3. ...

## Meetings (N today)

For each meeting:

**HH:MM — Meeting title**
- Attendees: [named list]
- Owner: [me / them]
- Prep needed: [yes — reason / no]
- Prior context: [last interaction with these people, if relevant]

## Commitments due today

[project tag] item — owed by [me / name]
...

## Slipped (overdue commitments)

[project tag] item — [N days overdue], owed to [name]
...

## Inbox attention

[N threads received yesterday, M from named stakeholders]
- [sender]: [subject] — [why it matters, if not obvious]
...

## Yesterday's loose threads

From [meeting]: [commitment that wasn't captured in any project's todos.md]
...

## Notes for context

[Any one-line context: tomorrow is a holiday, you're traveling Thursday, etc.]

---

*Brief generated [HH:MM]. Update `pm-state/projects/<name>/todos.md` as items get done.*
```

## What good looks like

- **Five-minute scan.** The brief should be readable in under five minutes. If it's longer, the agent is including noise.
- **Opinionated top 3.** Not a list of every meeting and every TODO. A genuine prioritization.
- **Cites sources.** Every commitment links to which project. Every meeting cites the calendar event. Every inbox item names the sender.
- **Catches the slip.** If the user committed to something verbally and didn't write it down, the brief catches it via the Granola read. This is the highest-leverage thing the brief does.
- **Stays out of the way when nothing's urgent.** A clean brief is short and ends with "nothing urgent."

## Anti-patterns

- **Listing everything.** A brief that lists every meeting, every TODO, every email is not a brief. It's a dashboard. Filter aggressively.
- **Soft "consider" language.** *"You might want to think about..."* is useless. Either it's a top-3 item or it isn't.
- **Inventing context.** If the agent doesn't know why a stakeholder matters, it should say so rather than guess. Fake context corrodes trust.
- **Drafting replies in the morning brief.** That's `pm-inbox-triage`. The morning brief surfaces what needs attention; it doesn't do the work yet.
- **Regenerating an existing brief without asking.** If today's brief already exists, the user has probably read it. Confirm before overwriting.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-meeting-prep`** — if a meeting needs prep, the user can invoke this skill against the specific meeting after the brief.
- **`pm-inbox-triage`** — if inbox attention is non-trivial, the user can invoke this for the drafting work.
- **`pm-meeting-debrief`** — if yesterday's loose threads are substantial, the user can invoke this on yesterday's transcripts to close the loop.

## How to invoke

Common invocation patterns:

- *"Run my morning brief."*
- *"What does today look like?"*
- *"Morning brief, please."*
- *Scheduled task firing at 7:30am weekdays.*

If invoked outside of morning hours, ask: *"This is the morning brief skill. It's already [HH:MM] — do you want to regenerate the morning brief, or would you rather run `pm-weekly-review` or just check what's outstanding?"*

If pm-state doesn't exist, defer to `pm-context-loader`'s handling of that case.
