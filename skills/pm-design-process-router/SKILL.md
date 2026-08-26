---
name: pm-design-process-router
description: Given a feature scope description, recommend the appropriate design-process intensity. Routes large features (M/L/XL) through the full Research → PRD → Design Concept → Detailed Design → Working Code pipeline; routes small features and bug fixes (XS/S) through an Express Lane (verbal sign-off, no Figma) that skips stages without value. Catches both over-processing of small work and under-processing of large work. Use at kickoff when scoping a new feature, or when triaging a backlog where the design team is over-loaded and you need to decide where to invest the process.
---

# PM design process router

Most PM teams have one design process, and they run every feature through it. The team that ships a bug fix the same way it ships a new product line wastes the small work, and the team that ships a new product line on Express Lane ships something half-baked.

This skill takes a feature scope description and recommends which lane it belongs in. The router applies a scope estimate (XS, S, M, L, XL), accounts for moderating factors (user novelty, reversibility, public visibility), and outputs a specific recommended process with named stages and owners.

The two-lane pattern is borrowed from enterprise design organizations that have separately optimized their pipeline for big-features-with-real-uncertainty vs. small-fixes-with-known-shape. Most PM teams don't formalize this and pay the cost in both directions.

## When to use

Use this when:
- Kickoff for a new feature, before committing design and engineering time
- The design team is over-loaded and the PM needs to decide which features get the full process
- A feature feels small but is taking weeks to review — surface whether it should be on Express Lane
- The team is debating whether something needs a Figma or not
- Estimating timelines across a backlog with mixed scope

Don't use this when:
- The feature is research-only with no shipping artifact (use `pm-decision-coach` instead)
- The organization has its own mandatory design-intake process that supersedes this routing
- The scope is genuinely unknown (the router needs a description to work; if the user can't describe the scope, the issue is upstream)

## How to apply

### 1. Chain to `pm-context-loader`

Load `you.md` and the active project. The project's `status.md` and `decisions.md` often contain the scope context that informs routing.

### 2. Get the feature description

The user needs to provide:

- What is changing (the surface area)
- Who the user is (one segment, several, all)
- Whether the user has seen this kind of thing before (familiar pattern vs. new behavior)
- What gets shipped (new screen, new flow, new product, modified existing surface, bug fix)
- Any deadline pressure or external constraints

If the description is vague, ask one or two specific questions to tighten it. The router only produces useful output when the inputs are concrete.

### 3. Estimate scope

Use this rubric, in priority order. A feature gets the largest size for which any dimension applies:

- **XS** — Bug fix or copy change, no UI structural change, no new flow, single team. *"Change the button label," "fix the timeout error message."*
- **S** — Small UI change within an existing flow, one screen affected, no new behavior the user has to learn. *"Add a sort option to the existing list view," "fix the broken validation on the existing form."*
- **M** — New screen or new flow within an existing product, modifies how an existing user behavior works. Users will notice and may need to relearn one thing. *"Replace the existing onboarding flow," "add a new tab to the dashboard."*
- **L** — Multi-screen feature, new user behavior, multi-team involvement, modifies the user's mental model of the product. *"Add collaboration to an isolated tool," "introduce a paid tier."*
- **XL** — New product area, new user segment, or change that affects the company's strategic positioning. *"Launch the enterprise version," "introduce a brand-new product."*

Then apply moderators that can push the scope up (not down):

- **User novelty.** The feature targets a user type the team has little research on. Push scope up one level — the design needs more discovery, not less.
- **One-way doors.** The feature involves a public commitment, regulatory filing, brand promise, or architectural choice that's hard to reverse. Push scope up.
- **Cross-team dependencies.** The feature changes a shared component or affects multiple teams' surfaces. Push scope up.
- **External visibility.** The feature ships to a launch event, conference, or press cycle. Push scope up, even if the underlying change is small.

### 4. Route based on the final scope

**XS and S (Express Lane):** Skip Figma. Verbal sign-off after a whiteboard or quick wireframe. The roles are:

- Develop stage: DEV (owner), Product Designer (reviews), PM, UX Writer optional review in code, Design Systems optional review in code.
- Working Code stage: DEV (owner), Technical Writer, UX Writer optional, Design Systems optional, Product Designer optional, PM.

The point of Express Lane is to ship small work without spending weeks getting design review on a button label. Default to verbal sign-off, written confirmation only if the change touches a shared component.

**M, L, XL (Full pipeline):** Run the five-stage pipeline:

- **Research** — UX Researcher (owner) and PM (owner), Product Designer involved. Output: user-need documented, key insights captured.
- **PRD** — PM (owner), Product Designer, DEV, Technical Writer, UX Writer, UX Researcher involved. Output: problem statement, success criteria, scope, kill criteria. (Chain to `pm-prd-drafter`.)
- **Design Concept** — Product Designer (owner), PM, DEV (developing backend), UX Researcher (optional). Output: concept-level design that captures the intended user experience.
- **Detailed Design** — Product Designer (owner), UX Writer (reviews UX copy), Design Systems (basic visual review), PM, Technical Writer, DEV (developing front end). Output: specced design ready for implementation. (Chain to `pm-design-critic` and `pm-persona-stress-tester` here.)
- **Working Code** — DEV (owner), Tech Writer optional, UX Writer optional, Design Systems optional, PM, Product Designer optional. Usability testing with real code by PM and Product Designer.

For M, all stages apply but the depth is moderate. For L and XL, each stage gets serious investment, and the pre-launch review (`pm-launch-reviewer`) is required.

### 5. Surface what to skip vs. insist on

For the chosen route, identify two things:

- **What to skip.** The stages or roles that don't add value for *this* feature. *"This M feature doesn't need UX Research because the team has six recent interviews with the target persona."*
- **What to insist on.** The stages or roles the team will be tempted to skip but shouldn't. *"Insist on the Design Concept stage even though engineering is pushing to start, because the user mental model is novel."*

### 6. Surface watch-outs

Things that could change the routing if discovered later:

- Scope creep (S becomes M)
- Discovery of one-way doors (the change is more permanent than originally thought)
- Cross-team dependencies surfacing late
- External commitments (conference launch, customer contract)

## Output structure

```
# Design process routing: [Feature name]

## TL;DR
[Recommended process: Express Lane or full pipeline, with one-sentence reasoning.]

## Scope estimate

**[XS / S / M / L / XL]**

- Surface area: [...]
- Users affected: [...]
- Novelty of user behavior: [...]
- Reversibility: [one-way / two-way]
- Cross-team dependencies: [yes / no]
- External visibility: [yes / no]

Moderators applied: [list, with rationale]

## Recommended process

**[Express Lane / Full pipeline]**

For each stage in the route:

- **[Stage name]** — Owner: [role]. Involved: [list of roles]. Output: [what comes out of this stage]. Skip if: [conditions under which this stage adds no value for this feature].

## What to skip

For this specific feature, the stages or roles that don't earn their keep:
- [stage / role] — [why it doesn't apply here]

## What to insist on

The stages or roles the team will be tempted to skip but shouldn't:
- [stage / role] — [why it's load-bearing for this specific feature]

## Watch-outs

Conditions that would change the routing if you discover them later:
- [condition] — [what to re-route to if it happens]

## Recommended chained skills

- [If full pipeline] Chain to `pm-prd-drafter` at the PRD stage
- [If full pipeline] Chain to `pm-design-critic` and `pm-persona-stress-tester` at the Detailed Design stage
- [If L or XL] Chain to `pm-launch-reviewer` before Working Code ships

---

*Routing is a starting point. The team can override based on context, but the override should be deliberate and named.*
```

## What good looks like

- **Honest scope estimate, not anchored to what the user wants.** If the user wants this to be Express Lane because of deadline pressure, but the scope is M, the routing says M. The deadline is a separate conversation.
- **Specific stages and owners, not generic "go through the design process."** The router's value is in naming who does what and which stages to skip.
- **Calls out moderators explicitly.** "This would normally be S, but it's a one-way door, so route as M" beats "I think this is M."
- **Names what to skip.** Not every stage adds value for every feature. Calling out the skips makes the recommendation usable.
- **Names what to insist on.** The team will be tempted to skip stages. Naming the ones that matter makes the skip-or-not decision deliberate.

## Anti-patterns

- **Routing every feature into the full pipeline.** The pipeline is a tool, not a default. Small work belongs on Express Lane.
- **Routing every feature into Express Lane because the team is over-loaded.** Under-processing M and L work is more expensive than over-processing S work. The fix for over-load is fewer features in flight, not less rigor per feature.
- **Treating the scope estimate as immovable.** Scope changes as you learn more. The router output is a starting point for re-routing if conditions change.
- **Generic recommendations.** "Run the design process" is not a recommendation. Named stages, owners, and skips are.
- **Skipping the moderator check.** A feature that looks S can be a one-way door masquerading as a button change. The moderators catch this.
- **Forgetting to surface watch-outs.** The watch-outs are how the team catches re-routing triggers in flight.

## Chain with other skills

- **`pm-context-loader`** — always first.
- **`pm-prd-drafter`** — at the PRD stage of the full pipeline.
- **`pm-design-critic`** and **`pm-persona-stress-tester`** — at the Detailed Design stage.
- **`pm-launch-reviewer`** — before Working Code ships, for L and XL features.
- **`pm-red-team`** — for XL features, after the PRD is drafted, to stress-test before committing.

## How to invoke

Common invocation patterns:

- *"Route this feature through the right design process."*
- *"Should this be Express Lane or full design pipeline?"*
- *"Help me scope this feature."*
- *"I have ten features in the backlog — help me decide which ones need full design vs. which can go on Express Lane."*

If invoked without a feature description, ask: *"What's changing in this feature? Who's the user? Has the user seen this kind of pattern before, or is it new behavior?"*

If invoked on a feature where the user clearly wants Express Lane regardless ("this needs to ship in two weeks"), surface the routing honestly first, then separately address the timeline: *"This is M, which normally runs the full pipeline. If the timeline is genuinely fixed, the question is what stages to compress, not whether to skip them. Here's what to compress vs. insist on."*
