# PRD template

A working PRD template. Use only the sections that earn their keep on the specific decision in front of you. A PRD is a forcing function for clarity — not a checklist.

---

## Title

[Short, specific, user-outcome-flavored. Not "AI Sharing v2." Better: "Single-click sharing for project artifacts."]

## TL;DR

One paragraph. Who it's for, what it does, why now, what success looks like.

## Problem

[Specific user] is trying to [specific job] but [specific blocker], which costs them [specific cost].

- **Who specifically?** Named segment. Not "users."
- **What job?** What are they trying to do *the moment before* they reach for the product?
- **What's blocking them today?** Including current workarounds (spreadsheets, Discord, email, copy-paste).
- **What's the cost of not solving it?** Time, money, missed outcomes, churn.

## Why now

What changed that makes this worth doing in this quarter, vs. last quarter or next?

- New capability we have / didn't have before
- New user behavior or market shift
- New competitive threat
- New regulatory or partner constraint

If "why now" is unclear, the PRD probably isn't ready. Save it for later.

## Solution

Described in **user-outcome terms**, not feature lists.

> "When [user] tries to [job], they will [new experience], which produces [new outcome]."

Then, only after the outcome is clear, list the components / features.

### Out of scope

What this PRD is *not* trying to do. The most valuable section.

- [Item 1] — explicitly out
- [Item 2] — explicitly out, deferred to [later release / different team]
- [Item 3] — won't address this; we believe [reason].

## Tradeoffs

The 2–3 most important tradeoffs. For each:

- What's gained
- What's lost
- Why we made this call

Not "all the things we considered." The most important ones, explored in depth.

## Success criteria

Pre-committed, falsifiable.

- **Primary metric:** [specific metric, specific target value, specific timeline]
- **Guardrails:** [metrics that should NOT regress while the primary moves]
- **Failure threshold:** [if primary metric is below X by date Y, we kill or pivot]
- **Acceptable failure range:** [what's a learning vs. what forces a stop]

## Risks

Real risk analysis, not a generic taxonomy.

For each risk:
- The load-bearing assumption it depends on
- The signal that would falsify it
- What we'd do if it materializes

Categorize: **tigers** (will bite — design around), **paper tigers** (manageable with scoping), **elephants** (small-looking but structurally large — over-weight these).

## Reversibility

- Is this a **one-way door** or a **two-way door**?
- If wrong, what does the unwind look like?
- Has rigor matched reversibility?

## Open questions

What we don't yet know. Better to surface than hide.

For each: who's responsible for resolving, by when.

## Implementation overview

Selected roadmap elements. Not a project plan. Just the load-bearing milestones.

- Milestone 1 — [date, owner, what's delivered]
- Milestone 2 — ...

## Dependencies

Other teams whose work this depends on (or that depend on this).

For each: named owner, status, deadline.

---

## Appendices, if useful

- User research summary
- Data sources
- Competitive analysis
- Related cases / patterns
