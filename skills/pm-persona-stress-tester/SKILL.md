---
name: pm-persona-stress-tester
description: Stress-test a design, flow, or PRD section by simulating how a specific persona would walk through it step by step. Takes the design plus a target persona (defined inline or pulled from pm-state stakeholders) and outputs a walkthrough from the persona's point of view — what they see, what they think, where they get stuck, the first failure mode that would make them bounce. Designed to surface obvious failures in 10 minutes before committing engineering time or scheduling real user research. Distinct from pm-design-critic (which applies behavioral principles to the artifact) and pm-customer-interview-coach (which helps run interviews with real users); this skill simulates the user.
---

# PM persona stress tester

Walks a persona through a design, in character, and reports what breaks.

Most usability failures are obvious in retrospect. Half of them would have been obvious in advance if the team had walked through the design as the actual target user, not as themselves. This skill does that walkthrough. The persona is named, the design is parsed into steps, and the simulation goes through each step asking: *what does this user see, what do they expect, what do they do, and where does the design lose them?*

Doesn't replace real user research. Filters out the embarrassing failures before you put a real user in front of the design.

Adapted from the practice of using AI as a "Persona Agent" to stress-test flows pre-launch, surfaced by design leaders at enterprise products where the cost of putting a broken flow in front of an enterprise admin is high.

## When to use

Use this when:
- A new design or flow is drafted and you want a usability audit before testing with real users
- A PRD section needs to be pressure-tested against how a specific user type would actually react
- You're comparing how two different personas experience the same design (e.g., new user vs. power user, marketing manager vs. data scientist)
- The persona is one you don't yet have rich customer data on, so AI simulation is the best stand-in until interviews land
- You want to chain with `pm-design-critic` for a complete review (principles + simulation)

Don't use when:
- Real user research is already scheduled and will land before this would be useful
- The persona is generic ("users will..."); the simulation requires a specific persona to produce specific output
- The design has no user-facing surface (backend service, API change)
- The artifact is too high-level for a step-by-step walkthrough (a strategy memo, not a design spec)

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md`, the active project, and stakeholders. If the user has named a persona that matches an entry in `pm-state/projects/<name>/stakeholders.md` or `pm-state/stakeholders.md`, use that file as the source of truth for the persona's goals, constraints, and prior context.

### 2. Identify the design artifact

What's being stress-tested:
- A PRD section (specifically the user-facing surface part)
- A flow description (a sequence of screens or actions)
- A described mockup (text description of the design, since this skill works without images)
- An onboarding spec
- A specific decision point in an existing product (e.g., a paywall, a confirmation modal)

If the artifact is too vague to walk through step by step, surface that and ask for a tighter description before proceeding.

### 3. Identify the persona

Three ways to source the persona:

- **From pm-state.** If the user named a stakeholder or persona that exists in their state files, load it. This is the strongest version because the persona's prior context, goals, and constraints are already documented.
- **From an inline description.** The user describes the persona ("a marketing manager at a series-B startup, mid-tech-fluency, time-pressured"). Use that, but note the gap in detail.
- **Synthesized.** Only if the user explicitly asks. Construct a representative persona for the segment from generic patterns. Clearly mark the output as based on a synthesized persona, with reduced confidence.

For each persona, capture before starting:
- Name and role (named, not generic)
- Tech fluency
- Goals at the moment they're using this design
- Constraints (time pressure, attention, organizational politics, technical limits)
- Vocabulary they would use (their own words, not the team's words)
- What would make them say yes vs. give up

### 4. Map the design into steps

Break the design into discrete user-facing moments. A moment is anywhere the user has to decide, act, or absorb information. Typical moments: landing on a screen, seeing a notification, encountering an empty state, hitting a decision point, completing an action, seeing the result.

Cap the walkthrough at 8 to 12 moments. More than that and the simulation loses focus. Less than 3 and the design is probably too small to stress-test.

### 5. Simulate the persona at each moment

For each moment, produce four things:

- **What they see.** From the persona's perspective, not the team's. *"I see a screen with a chart and a sidebar with three icons I don't recognize."* Not *"the dashboard renders with the navigation pane."*
- **What they think.** First reaction in their own vocabulary. *"Wait, am I in the right place? I came here to do X."* Not *"the user might be confused about the IA."*
- **What they expect.** What they think is supposed to happen next. *"I expect to click the green button to continue."* This surfaces the mental model mismatch when the design works differently from the expectation.
- **What they do.** Their actual action. *"I click the chart, expecting it to expand. Nothing happens. I scroll down looking for an obvious next step."* The action is what produces the next state, not the expectation.

Stay in character. The persona has their vocabulary, their patience level, their tolerance for friction. If they would not read the tooltip, they would not read the tooltip. If they would skim the modal and click Continue, that's what they do.

### 6. Identify the first failure mode

Across the walkthrough, name the first moment the persona would *bounce, get confused, or escalate to support*. The first failure mode matters more than later ones because most users do not reach later moments.

The bar: would the persona, in real life, give up here? Or would they push through? If they would push through, name the cost (cognitive load, frustration, lost trust) and continue.

### 7. Calibrate with what works

Not every moment is a failure. Name two or three moments where the design genuinely serves this persona well. Calibration matters: a walkthrough that's all complaints either describes a uniformly broken design (rare) or a biased simulation (common). Acknowledging what works keeps the critique honest.

### 8. Recommend specific changes

For each surfaced failure mode, propose a specific design change. Not "rethink the onboarding" — "replace the three-icon sidebar with one labeled button on the first action, defer the secondary affordances to a second visit."

The recommendation should be something a designer can implement without re-asking what was meant.

### 9. (Optional) Run a second persona for comparison

If the design is meant to serve multiple user types, run the walkthrough a second time with a different persona and surface where the two diverge. This catches designs that serve one persona at the expense of another.

## Output structure

```
# Persona stress test: [Design name]

## Persona
**Name, role**
- Goals at this moment: [...]
- Constraints: [...]
- Vocabulary: [...]
- Confidence in this persona: high (from stakeholders.md) / medium (from inline description) / low (synthesized)

## TL;DR
[One paragraph honest take. Does this design work for this persona? What's the first thing to fix?]

## Walkthrough

### Moment 1: [name of the step]
- What they see: [...]
- What they think: [...]
- What they expect: [...]
- What they do: [...]

[Repeat for each moment, capped at 8-12.]

## First failure mode

**[The specific moment the persona would lose patience]**
- What happens: [...]
- Why it fails for this persona: [...]
- What would they do in real life: [bounce / escalate to support / push through with reduced trust]

## What works for this persona

[Two or three moments where the design genuinely serves them. Be specific.]

## Recommended changes

For each failure mode, a specific design change a designer can implement:
1. [Where in the design] [the specific change] — [why it would work for this persona]
2. ...

## Comparison with [alternate persona]
[Optional. Where do the two personas diverge in their walkthrough? What design choice serves one at the expense of the other?]

---

*Run `pm-design-critic` for principle-based critique on the same artifact. Schedule real user research for the failure modes that matter most.*
```

## What good looks like

- **Specific behaviors, not generic statements.** "She would not read the three-paragraph onboarding modal" beats "users might find the onboarding too long."
- **Stays in the persona's vocabulary.** If they would call it "the report thing" rather than "the analytics dashboard," that's what the simulation says.
- **Names the moment of failure, not just the area.** "She bounces at the cohort-selection step because there are 7 cohorts and she came here to do one thing" beats "the cohort selection is confusing."
- **Distinguishes friction from failure.** Not every confusion is a bounce. Some are tolerable, some are fatal. The simulation should say which.
- **Cites the persona file.** When pulling from `pm-state/projects/<name>/stakeholders.md`, reference it so the user can update the persona file if the simulation surfaces gaps in the persona definition.
- **Calls out where the persona is doing the work the design should be doing.** Workarounds the persona invents in the walkthrough are signs the design is asking the user to compensate for missing affordances.

## Anti-patterns

- **Generic "users" simulation.** Must have a specific named persona. Without one, the output is the same as a generic principle critique and doesn't add value.
- **Letting the persona become sympathetic to the design.** If the persona is "patient and methodical," the simulation will absorb friction and never surface failure. Bias the persona toward realistic impatience.
- **Inventing persona details that contradict stakeholders.md.** If the file says they hate notifications, the simulation cannot have them embrace notifications mid-walkthrough. Stay consistent with the source.
- **Stopping at "this is confusing" without naming what specifically would confuse them.** The simulation should produce specific observations, not summary judgments.
- **Walking through too many moments.** More than 12 dilutes attention. Cap aggressively.
- **Forgetting to surface what works.** A walkthrough that's all complaints is biased. Two or three "this part lands for this persona" observations keep the critique credible.
- **Auto-acting on the recommendations.** This skill drafts critique and proposed changes. It does not modify the design artifact directly.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-design-critic`** — run before or after for principle-based critique (defaults, choice architecture, peak-end, etc.). The two skills surface different things: design-critic catches what violates principles, persona stress tester catches what fails for a specific user.
- **`pm-customer-interview-coach`** — after, when scheduling real user research. The failure modes surfaced here become the things to validate with real customers.
- **`pm-prd-drafter`** — if the simulation surfaces a load-bearing gap in the PRD's user-experience section, chain to update the PRD.

## How to invoke

Common invocation patterns:

- *"Run a persona stress test on this onboarding flow for our Striver segment."*
- *"Walk through this PRD as a marketing manager at a series-B startup."*
- *"Compare how a power user and a new user experience this paywall."*
- *"Stress-test this flow against my [persona name] from `stakeholders.md`."*

If the user doesn't name a persona, ask: *"Which persona should I walk through this as? Options from your stakeholders.md: [...]. Or describe one inline."*

If the artifact is too vague, ask: *"I need a step-by-step description of what the user encounters. Walk me through the design moment by moment, and I'll run the simulation against it."*
