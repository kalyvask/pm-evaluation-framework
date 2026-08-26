---
name: pm-inbox-triage
description: Pull recent Gmail threads, classify them into action categories (substantive response needed / quick reply / FYI / can ignore), and draft replies for the substantive ones. Surfaces stale threads where the user is awaiting a response and stale threads where someone is awaiting them. Used as part of pm-morning-brief or invoked directly when the inbox feels out of control. Drafts only — never auto-sends.
---

# PM inbox triage

The inbox is where stakeholder relationships live or die. Most PMs let it become noise; this skill turns it back into signal.

The skill reads recent threads, classifies them, drafts replies for the ones that need substantive responses, and surfaces the threads going stale. The user reviews, edits drafts, and decides what to send. Nothing leaves the agent.

## When to use

- As part of `pm-morning-brief`'s inbox section (called implicitly)
- When the inbox has grown past 20 unread and the user feels backed up
- After being out for a few days
- At end-of-day to clear the slate before tomorrow

Don't use when:
- The inbox is mostly social / personal (this skill is for work threads)
- The user wants the agent to auto-send replies (the skill refuses)
- The Gmail MCP server is not connected — surface that and stop

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, the active project list, cross-project stakeholders.

### 2. Pull recent threads

Use the Gmail MCP to pull threads:

- Inbox folder, unread or recent (last 48 hours by default)
- Filter out automated newsletters, GitHub notifications, calendar invites, and other non-work noise
- Group by thread (a thread of replies is one item, not many)

For each thread, capture:

- Sender(s)
- Subject
- Last message date
- Body of the most recent message (the agent's classifier needs the content)
- Whether the user is on the To: line or just CC'd

### 3. Classify each thread

Four categories:

- **Substantive response needed.** The thread asks the user for something specific (a decision, an answer, a deliverable, an opinion). The user has to actually respond.
- **Quick reply.** A two-line acknowledgment closes the thread. Confirmations, scheduling, "noted, will do."
- **FYI.** No action required; just keep in scope. Often CC threads.
- **Can ignore.** Newsletters that made it through filters, threads that resolved without the user, threads where the user is no longer relevant.

Be conservative on "ignore." When in doubt, classify as FYI.

### 4. For substantive threads, draft replies

For each thread in the "substantive response" category:

- Match the user's voice (refer to `you.md` style preferences)
- Address what the sender actually asked
- Be concrete: dates, numbers, specific commitments
- If the user genuinely doesn't have the answer, draft "*I don't have an answer yet, will respond by [date]*"
- If the user owes a decision and the decision isn't made, surface that as a separate flag rather than drafting hedging language

Critical: drafts only. Never auto-send.

### 5. For quick-reply threads, draft a one-liner

A two-line acknowledgment. Bulk-draft these together so the user can approve them in a single pass.

### 6. Surface stale threads

Two stale-thread patterns to surface:

- **You're awaiting a response.** You sent something 5+ days ago and got no reply. Most need a polite follow-up.
- **They're awaiting your response.** A thread where someone sent you something 7+ days ago and you haven't replied. These are relationship-corroding silences.

For each stale thread, propose either a follow-up draft (case 1) or surface to the substantive-response queue (case 2).

### 7. Identify commitments

Read through the substantive threads. Identify commitments the user made in those threads — these often don't make it to project todos. Cross-reference the relevant project's `todos.md`. Surface any commitments that aren't captured. Propose adding them (with explicit user approval, same pattern as `pm-meeting-debrief`).

### 8. Output the triage report

Use the structure below. Optimize for review-and-decide speed: the user should be able to act on the whole triage in 15 minutes or less.

## Output structure

```
# Inbox triage — [HH:MM]

## Summary
- [N] threads reviewed
- [N] need substantive response
- [N] need quick reply
- [N] FYI
- [N] can ignore
- [N] stale (you awaiting), [N] stale (they awaiting)

## Substantive responses needed

For each:

**From [sender] — [subject]**
- The ask: [what they want]
- Draft reply:
  ```
  [draft body in user's voice]
  ```
- [Approve / edit / defer]

## Quick replies (batch)

**To [sender] re [subject]:**
```
[two-line acknowledgment]
```

[Repeat. Approve all at once or individually.]

## Stale threads — you awaiting reply

For each:
- [name], [subject], sent [N days ago]
- Draft follow-up: [optional one-line nudge]

## Stale threads — they awaiting your reply

For each:
- [name], [subject], you've been silent [N days]
- Why this is uncomfortable: [the relationship risk]
- Suggested: respond now, or set a deadline to respond by

## Commitments found that aren't in project state

For each:
- [project] — [commitment] — found in email thread [subject]
- Propose adding to: `pm-state/projects/<name>/todos.md`
- [Write / skip]

## FYI — keeping in scope

Short list. Just senders and subjects. No drafts needed.

## Threads you can ignore

Even shorter list. Just count or representative samples.
```

## What good looks like

- **Honest classification.** Most threads are FYI or ignore. If the agent classifies 80 percent of threads as needing substantive response, the classifier is wrong. The bar for "substantive" is high.
- **Drafts that sound like the user.** If the user is direct, the drafts are direct. No "I wanted to circle back to..." filler unless that's the user's style (per `you.md`).
- **Specific stale-thread flags.** "Sarah sent you the PRD review on Tuesday, you haven't replied in 6 days, this is a senior stakeholder" is signal. "You have 4 stale threads" is not.
- **Surfaces commitments.** The inbox is where commitments leak from project state. Catching them in triage is the highest-leverage move.
- **15-minute review.** The whole triage should be reviewable in 15 minutes max. If it's longer, the agent is including noise.

## Anti-patterns

- **Auto-sending replies.** Never. Drafts only.
- **Drafting hedging language when the user doesn't have an answer.** Better to draft *"I don't have an answer yet, will respond by [date]"* than to hedge with vague language. The hedge is worse than the honest no.
- **Treating every CC as substantive.** Most CCs are FYI. Don't draft replies for threads where the user isn't the primary recipient unless the sender actually asked them something specific.
- **Inventing context.** If the agent doesn't know who a sender is or what the thread context is, classify as FYI and surface the gap. Don't fake stakeholder context.
- **Reading more than 48 hours of inbox without a reason.** The default scope should be tight. Expand only when the user explicitly asks (e.g., "after I was away last week").

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-morning-brief`** — calls this skill (implicitly) for the inbox section.
- **`pm-meeting-debrief`** — if a thread is a follow-up to a recent meeting, cross-reference the debrief.
- **`pm-stakeholder-tracker`** — stale threads where the user is silent are often a stakeholder-tracking issue. Chain to surface those across the whole stakeholder list.

## How to invoke

Common invocation patterns:

- *"Triage my inbox."*
- *"What in my inbox needs attention?"*
- *"I've been out for 3 days, run inbox triage on the last 72 hours."*
- *Used implicitly by `pm-morning-brief` to surface inbox attention.*

If invoked with no Gmail MCP available, respond: *"I can't reach Gmail. Make sure the MCP server is connected. If it's intentional that I can't see your inbox, you can paste the threads here for triage."*

If the user asks the skill to auto-send a draft, refuse: *"I draft, you send. The asymmetric downside of an auto-sent wrong reply is too large to take. Want me to draft and you send from your client?"*
