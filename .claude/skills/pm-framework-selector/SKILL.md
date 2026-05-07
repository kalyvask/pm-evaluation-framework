---
name: pm-framework-selector
description: Recommend which product-management framework(s) to apply to a specific decision. Use when the user describes a product decision and asks "what framework should I use?" / "how should I think about this?" / "which lens applies?" — or when you spot a PM decision in a conversation that would benefit from explicit framework grounding (prioritization, MVP scoping, validation, growth, risk, problem-framing). Anchored in the lifecycle-phase frameworks library in this repo.
---

# PM framework selector

This skill helps a PM (or someone helping a PM) pick the right framework for the decision in front of them. The repo's frameworks are organized by lifecycle phase, so framework selection starts by identifying what *kind* of decision is being made.

## How to apply

1. **Diagnose the question, not the symptom.** The user's surface question ("how do I prioritize these features?") may not be the real question ("we don't know what problem we're solving"). Ask one or two clarifying questions before recommending a framework.

2. **Map the decision to a lifecycle phase**, using the table below. Frameworks live in `frameworks/01-strategy-and-discovery.md` through `frameworks/05-continuous-prioritization.md`.

3. **Recommend 1–2 frameworks, not 5.** Cite the specific file in the repo. Explain *why* this framework, not just *what*.

4. **Note when not to use a framework.** One-way doors, strategic bets, and existential decisions usually need a memo, not a score. Flag this.

| If the question is about... | The phase is... | Likely framework(s) |
|---|---|---|
| What problem to solve, why now, who for | Strategy & Discovery | PMF Narrative, Working Backwards, Pre-Mortem |
| Whether the decision is reversible / how much rigor it deserves | Strategy & Discovery | One-Way / Two-Way Doors |
| Risk surfacing before launch | Strategy & Discovery | Pre-Mortem (tigers / paper tigers / elephants), Sensitivity Analysis |
| What to ship in V1 | Defining the MVP | JTBD Ranking, MoSCoW, Cupcake Model |
| Which features are basics / performance / delighters | Defining the MVP | Kano Model |
| End-to-end thin-slice scoping | Defining the MVP | Story Mapping |
| Whether the underlying value-hypothesis bet (what / who / how) holds together | Pre-PMF Validation | Rachleff value hypothesis, Christensen disruption, bowling-pin / chasm — see `decision-making/value-hypothesis.md` |
| Whether we have PMF | Pre-PMF Validation | "10 Happy Users", Sean Ellis Test, Smile Curve, ARC |
| Activation / TTV health | Pre-PMF Validation | Activation Rate / TTV |
| Whether GTM is actually ready | Pre-PMF Validation | GTM Strategy Checklist |
| How to actually run a customer-discovery interview without collecting false positives | Strategy & Discovery / Pre-PMF | Mom Test rules — see `decision-making/customer-interviews.md` |
| Funnel diagnostics post-PMF | Post-PMF Growth | AARRR (Pirate Metrics) |
| Feature-level UX measurement | Post-PMF Growth | HEART |
| Retention diagnosis | Post-PMF Growth | Cohort Retention, Growth Accounting |
| Unit economics check | Post-PMF Growth | LTV / CAC |
| Backlog ranking | Continuous Prioritization | RICE, WSJF, Opportunity Scoring |
| One metric for the whole org | Continuous Prioritization | North Star Metric |
| Connecting features to strategy narrative | Continuous Prioritization | Storytelling Narrative |

For decisions that don't fit a phase cleanly (problem framing, research methods, cross-functional disputes), look in `decision-making/` and `cross-functional/`:


| Question | File |
|---|---|
| Am I solving the right problem? | `decision-making/problem-framing.md` |
| Personas vs. JTBD vs. Kano | `decision-making/research-methods.md` |
| How to run a customer-discovery interview that actually produces signal | `decision-making/customer-interviews.md` |
| What's the underlying value-hypothesis bet, and how do I test it? | `decision-making/value-hypothesis.md` |
| Is this product actually defensible, and against which competitor move? | `decision-making/competitive-moat.md` |
| One-way vs. two-way doors, pre-mortem | `decision-making/risk-and-reversibility.md` |
| Backlog prioritization | `decision-making/prioritization.md` |
| What to measure | `decision-making/metrics.md` |
| PM/engineering tension | `cross-functional/engineering-partnership.md` |
| Project failure / kill / postmortem | `cross-functional/failure-management.md` |
| Bundle effects, exec credibility, B2B distribution | `cross-functional/stakeholder-alignment.md` |

## Output structure

When invoked, respond with:

1. **One-line restatement** of the decision the PM is actually making
2. **Recommended framework(s)** — name, file path, one-line "why"
3. **Sharpening questions** — 2–3 questions the framework will force the PM to answer
4. **When NOT to use this** — flag if a framework is the wrong tool here

Keep responses tight. The point is to point them at the right page, not to summarize the page.

## Common diagnostic mistakes to flag

- "How do I prioritize?" — often the upstream problem is *strategy unclear*, not prioritization. Surface this if it applies.
- "Should we ship this AI feature?" — usually the question is unit economics + differentiation + trust UX, not "is the feature good?"
- "Users want X" — stress-test: is this stated preference or revealed? Strategic segment or convenient one? Friction problem or incentive problem?
- "We need to refactor / rebuild" — almost always a reversibility question first, then a credibility-with-leadership question.
- "Should we kill it?" — almost always answered by pre-committed kill criteria. If those don't exist, that's the upstream issue.
