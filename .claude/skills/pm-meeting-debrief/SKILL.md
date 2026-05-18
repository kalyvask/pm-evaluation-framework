---
name: pm-meeting-debrief
description: Given a Granola meeting transcript, extract commitments (yours and theirs), identify decisions made, draft follow-up messages, and update the relevant project's `todos.md` and `stakeholders.md`. Use right after a meeting to close the loop before the context fades. Surfaces commitments that need to be captured into the project state, drafts the follow-ups, and asks the user to approve writes.
---

# PM meeting debrief

The most underused PM workflow. After every meeting, most teams lose 20 to 40 percent of the value because commitments aren't captured, decisions aren't logged, and follow-ups don't happen. This skill closes that loop.

Given a Granola transcript, the skill extracts commitments, surfaces decisions, drafts follow-up messages, and proposes updates to the project state files. The user approves writes; the agent never writes to `pm-state/` without confirmation.

## When to use

- Right after a meeting (within an hour), when context is fresh
- At end-of-day, against all of today's transcripts
- As part of `pm-morning-brief`'s "yesterday's loose threads" handling

Don't use when:
- The meeting has no Granola transcript (the skill needs the transcript as input)
- The transcript is purely social or social-only (no work content)
- A debrief has already been run on the same transcript (don't duplicate)

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, the project list, cross-project stakeholders.

### 2. Identify the transcript

If the user named a specific meeting, pull that transcript. Otherwise:

- Pull recent transcripts via the Granola MCP
- Identify the most recent one not yet debriefed (look for absence in the relevant project's recent decisions or todos with the meeting date)
- If ambiguous, ask: *"You have [N] recent transcripts. Which one — [list]?"*

### 3. Identify the project

Most meetings map to a project. Determine which:

- Cross-reference attendees with project stakeholders files
- Use the meeting title and content
- If unclear, ask the user

If the meeting is cross-project, skip project-specific state and operate against `pm-state/stakeholders.md` and `pm-state/decisions-log.md`.

### 4. Extract commitments

Read the transcript. For each commitment, capture:

- **Who owns it** — the user, a named attendee, or "the team"
- **What the commitment is** — specific action
- **Due date** — explicit if stated, inferred if implied, "TBD" if unknown
- **Confidence** — was this a firm commitment ("I'll send the PRD by Friday") or a softer one ("we should probably look into that")

Be conservative on the soft ones. Mark them clearly so the user can decide what to keep.

### 5. Identify decisions made

A decision is different from a commitment. Decisions get logged in `decisions.md`; commitments get logged in `todos.md`.

For each decision, capture:

- **What was decided**
- **Context** — what triggered it
- **Reasoning** — why this over alternatives
- **Reversibility** — one-way or two-way
- **Who agreed** — explicit consent vs. acquiescence vs. unclear

Surface decisions that the meeting made without explicit consent — those are common, and they often unwind later when someone in the room realizes they didn't agree.

### 6. Draft follow-up messages

For commitments where the user owes a deliverable to a named person, draft the follow-up message:

- Subject line that names the commitment
- One-paragraph body in the user's voice (refer to `you.md` for style)
- Specific date for the deliverable

Do NOT auto-send. Surface the draft for the user to approve and send.

For commitments where someone else owes the user, draft a polite follow-up confirming the commitment in writing — that's how soft commitments become firm ones.

### 7. Propose state updates

Show the user what should be written where:

- **`pm-state/projects/<name>/todos.md`** — new commitments as TODO items
- **`pm-state/projects/<name>/decisions.md`** — new decisions with the four-line shape
- **`pm-state/projects/<name>/stakeholders.md`** — update "last interaction" date and any new context on attendees
- **`pm-state/projects/<name>/open-questions.md`** — questions raised in the meeting that didn't get answered

For each proposed write, show the user the exact diff and ask: *"Write this update? [yes / edit / skip]"*

Apply each write only after explicit approval.

### 8. Surface what was NOT covered

A useful section: what was on the agenda but didn't get discussed. Often the most important items get squeezed off. Surface them so the user can decide whether to schedule a follow-up.

## Output structure

```
# Meeting debrief: [Meeting title] — [Date]

## TL;DR
[One paragraph honest take. Did this meeting close the loop on what it was supposed to? What got decided, what got punted?]

## Commitments

**From [the user]:**
- [item] — due [date], to [name]. [Confidence: firm / soft.]
- ...

**From [others]:**
- [name]: [item] — due [date], to you. [Confidence: firm / soft.]
- ...

## Decisions made

For each decision:

**[Decision title]**
- Context: ...
- Choice: ...
- Reasoning: ...
- Reversibility: one-way / two-way
- Agreement: explicit / acquiescent / unclear
- Proposed write: `pm-state/projects/<name>/decisions.md`

## Draft follow-up messages

**To [name] re: [commitment]:**
```
[Draft message body in the user's voice]
```

[Repeat for each follow-up.]

## Proposed state updates

For each proposed write, show:
- File path
- The exact lines to add
- Ask: write this? [yes / edit / skip]

## What didn't get covered

[Items that were on the agenda or implied but didn't get discussed. Recommend whether to schedule a follow-up.]

## Loose ends to watch

[Things said in the meeting that don't fit cleanly into commitments or decisions but might matter later. Surfaced for awareness, not action.]

---

*Run `pm-stakeholder-tracker` if the meeting changed open commitments across multiple stakeholders.*
```

## What good looks like

- **Catches the soft commitments.** Most debriefs catch the firm ones. The soft "we should look at that" commitments are where work gets lost. Surface them, mark them clearly, let the user decide.
- **Distinguishes commitments from decisions.** They go to different files and have different shapes. Confusing them creates a TODO list that's actually a decision log, or vice versa.
- **Drafts in the user's voice.** Refer to `you.md` for style. No "I wanted to circle back to..." if the user is direct.
- **Asks before writing.** Every write to a state file gets explicit user approval. The agent never updates the user's memory unilaterally.
- **Surfaces what wasn't said.** What was on the agenda but didn't happen is often more important than what did.

## Anti-patterns

- **Auto-sending follow-ups.** Never. Drafts only. The user reviews and sends.
- **Auto-writing to state files.** Never. Proposes writes, asks for approval, then applies.
- **Treating every utterance as a commitment.** Most aren't. Filter aggressively. Better to miss a soft commitment than to fill the user's todos.md with noise.
- **Forgetting to mark confidence on soft commitments.** A "maybe" commitment in the TODO list will rot and become noise. Mark it clearly so the user knows it needs follow-up to firm up.
- **Skipping the "what didn't get covered" section.** The misses are signal. Always include this section, even if it's empty.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-stakeholder-tracker`** — after debriefing, if open commitments changed for multiple stakeholders.
- **`pm-morning-brief`** — calls this skill (implicitly) to surface yesterday's loose threads.
- **`pm-prd-drafter`** or **`pm-decision-coach`** — if the meeting raised a decision that needs more work, chain to the relevant skill afterward.

## How to invoke

Common invocation patterns:

- *"Debrief my 10am with Sarah."*
- *"Pull the most recent Granola transcript and run a debrief."*
- *"Close the loop on yesterday's meetings."*
- *Used implicitly by `pm-morning-brief` to surface yesterday's loose threads.*

If invoked with no transcript available, respond: *"I can't find a Granola transcript for that meeting. Did the meeting have Granola running? If yes, want me to wait and try again in a few minutes? If no, you can manually paste notes here and I'll run the debrief on those."*
