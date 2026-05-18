---
name: pm-context-loader
description: Load the PM agent's persistent context — personal style and preferences from `you.md`, the active project list, cross-project stakeholders, and the relevant project's state. Use as the first step in any PM workflow when you need the agent to understand the user's current work before doing anything else. The other operate-stage skills (pm-morning-brief, pm-meeting-prep, pm-meeting-debrief, pm-weekly-review, pm-stakeholder-tracker) chain to this skill first.
---

# PM context loader

Loads the user's PM state from `pm-state/` so subsequent work has the right context. This is a utility skill, not a workflow skill — its job is to prepare the agent for whatever workflow comes next.

Without this loader, every PM session starts cold. The agent has frameworks (the rest of this repo) but no knowledge of the user's actual projects, stakeholders, or open commitments. With it, every session boots with the user's current state in scope.

## When to use

Use this as the first step when:
- The user asks for help with a PM workflow that needs personal context (any of the operate-stage skills)
- The user says "what's my morning look like" or "what should I be working on"
- The user mentions a project by name and you don't have its state in scope
- A different skill (`pm-prd-drafter`, `pm-decision-coach`, `pm-evaluator`) is about to run on a real artifact and would benefit from project context

Don't use this when:
- The user is asking a generic framework question that doesn't need personal context
- The user is running a critique on a hypothetical example
- The pm-state folder doesn't exist yet — surface that and ask the user to set it up

## How to apply

### 1. Locate the pm-state folder

Default location: `C:/Users/alexa/OneDrive/Documents/GSB/pm-state/` (user's installation).

If the folder doesn't exist or is empty:

- Surface this to the user: *"I can't find your pm-state folder at the expected location. Have you set it up? If not, I can scaffold it from `pm-state/_template`."*
- Don't proceed with the workflow that called this skill — context loading failed.

### 2. Read the core files in order

Read these files at the start of every load:

1. **`pm-state/you.md`** — personal context. Style, current role, active project list, cross-project stakeholders, what "good" looks like for this user.
2. **`pm-state/stakeholders.md`** — global stakeholder list (cross-project).
3. **`pm-state/decisions-log.md`** — cross-project decision history. Useful for spotting patterns.
4. **`pm-state/lessons.md`** — lessons learned that should shape current work.

These four files are stable across sessions and define the user's frame.

### 3. Identify the active project (if any)

Determine which project the current workflow is about:

- If the user mentioned a project by name, use that.
- If the calling skill knows the project (e.g., `pm-meeting-prep` figured it out from the meeting's attendees), use that.
- If unclear, ask the user: *"Which project is this about? Options from your active list: [...]"*

If the work isn't project-specific (e.g., a cross-project weekly review), skip this step.

### 4. Read the project state

If a project is identified, read its full state:

- `pm-state/projects/<project>/status.md`
- `pm-state/projects/<project>/decisions.md`
- `pm-state/projects/<project>/open-questions.md`
- `pm-state/projects/<project>/stakeholders.md`
- `pm-state/projects/<project>/todos.md`

### 5. Summarize what was loaded (one line)

Before handing off to the calling skill, emit a one-line confirmation:

> *Loaded context: you.md (last updated [date]), [N] active projects, project `<name>` in scope.*

This is for the user's visibility, not the agent's. The full context is now in scope for the rest of the conversation.

## Output structure

This skill produces context, not artifacts. The output is a single confirmation line plus loaded state available to the rest of the session.

```
Context loaded.
- Personal style: from you.md (updated [date])
- Active projects: [list]
- Project in scope: [name] (or "none — cross-project workflow")
- Cross-project stakeholders: [N] entries
- Lessons file last updated: [date]
```

## What good looks like

- **Fast.** Should take seconds. Reading 5 to 8 short markdown files is the entire job.
- **Silent unless something is missing.** If the pm-state folder is well-maintained, the loader emits the one-line confirmation and stops. If something is stale or missing, it surfaces that.
- **Specific about staleness.** If `you.md` was last updated 90 days ago, mention it. The user should know when their context is going dry.
- **Refuses to fabricate.** If a project folder doesn't exist, the loader says so. It does not infer state from project names or repo contents.

## Anti-patterns

- **Reading every file in pm-state on every call.** Unscoped reads are slow and dilute attention. Read the core files always; read project state only when a project is in scope.
- **Inferring context from filenames or partial reads.** The state files are short; read them fully. Halfway-read state produces confidently wrong outputs downstream.
- **Treating an empty or missing pm-state as a normal session.** It isn't. Surface the gap and stop until the user sets up the folder.
- **Forgetting to surface staleness.** If the user's `you.md` is months old or `todos.md` hasn't been touched in two weeks, mention it. The maintenance contract is what makes the agent useful.

## Chain with other skills

Almost all the operate-stage skills start by calling this one:

- **`pm-morning-brief`** — loads context, then pulls calendar and inbox
- **`pm-meeting-prep`** — loads context, then pulls the calendar event
- **`pm-meeting-debrief`** — loads context, then pulls the Granola transcript
- **`pm-weekly-review`** — loads context, then runs the weekly diff
- **`pm-stakeholder-tracker`** — loads context, then runs the cross-stakeholder check
- **`pm-inbox-triage`** — loads context, then pulls Gmail

You can also chain this skill before reactive skills (`pm-evaluator`, `pm-prd-drafter`, `pm-decision-coach`) when the user is critiquing or drafting a real artifact and the project context would inform the critique.

## How to invoke

Common invocation patterns:

- *"Load my PM context."*
- *"What am I working on today?"* (the agent loads context first, then answers)
- *Used implicitly when another operate-stage skill runs.*

If invoked when no pm-state folder exists, respond:

> *"You don't have a pm-state folder set up yet. I can scaffold one at `C:/Users/alexa/OneDrive/Documents/GSB/pm-state/` from the template in this repo, or you can point me at a different location. Want me to set it up?"*

If invoked when the folder exists but is empty:

> *"pm-state exists but `you.md` is missing or empty. Without it, the agent can't reason about your specific work. Let me know if you want help filling it in."*
