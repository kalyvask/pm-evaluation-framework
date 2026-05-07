# Decision log entry

A short record of a decision *after it's been made*. Companion to [`decision-memo.md`](decision-memo.md): the memo is for *making* the decision, the log is for *remembering* it.

The point of a log entry is to keep teams from re-litigating settled questions every two months. New people join, context fades, the rationale gets forgotten — and someone re-opens "should we kill X?" in a leadership review without realizing it was decided in March. A two-paragraph log entry, searchable, prevents that.

Save log entries as `docs/decisions/YYYY-MM-DD-<short-slug>.md` so chronology is visible from the file name.

---

## Title

[One line. The decision in plain language. *"Pause the SSO migration until Q3."* Not *"SSO migration update."*]

## Date

[YYYY-MM-DD when the decision was made.]

## Category

One of:

- **Strategic** — direction, positioning, scope of the bet, kill / continue / pivot
- **Tactical** — execution approach, which framework, which tool, how to ship
- **Operational** — process, cadence, ownership, day-to-day mechanics

## Context

What prompted the decision? (2–4 sentences.) New evidence, missed milestone, leadership ask, customer escalation, market change.

## Decision

The decision itself, one sentence. What's now true that wasn't yesterday.

## Alternatives considered

Minimum two. *No alternatives means it wasn't a decision — it was a default.*

For each:

- **Option A:** [...]
- **Option B:** [...]
- **Option C (chosen):** [...]

## Rationale

Why this option, in two or three sentences. The argument that won.

## Trade-offs accepted

What's now harder, slower, or worse because of this decision. Be honest. *"We're accepting <X> in exchange for <Y>."* Future-you will thank present-you for naming the cost.

## Decision-maker and consulted

- **Decision:** [Name, role]
- **Consulted:** [Names, roles]

## Linked artifacts

- [ ] Decision memo (if any)
- [ ] Strategy doc this connects to
- [ ] Pre-mortem / risk analysis
- [ ] Customer / data evidence

## Revisit when

A specific trigger — a date, a metric threshold, a milestone. *"Revisit at end of Q3 when migration is complete"* or *"Revisit if churn in segment X exceeds 8% in any quarter."*

If the decision is strategic and you can't write a revisit trigger, name that gap explicitly. Strategic decisions without revisit triggers tend to ossify into "the way we do things" long after the conditions that motivated them have changed.

---

## How to use

- **Write at the time of decision, not later.** Memory degrades within days.
- **Keep entries short — half a page is plenty.** A long log entry signals the decision wasn't actually made.
- **One entry per decision, not one per meeting.** A meeting can produce several decisions or zero. Log the decisions, not the meetings.
- **Search before you debate.** When a settled question gets re-opened, the first move is *"is this in the log?"* If yes, link to the entry and ask whether anything has changed enough to revisit. Often nothing has.

The log is institutional memory. Treat it that way: contributors should be able to read it cold and understand why the team is where it is.
