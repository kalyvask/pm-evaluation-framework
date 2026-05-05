# PM evaluation rubric

A practical rubric for evaluating a PM's analysis, recommendation, or decision-making — whether on a written case, a strategy memo, or a live discussion.

The rubric scores along five dimensions, each with concrete examples of strong, adequate, and weak responses.

---

## The five evaluation criteria

| # | Criterion | Question |
|---|---|---|
| 1 | **Problem identification** | Did you identify the right problem before jumping to solutions? |
| 2 | **Framework discipline** | Did you apply a framework to remove bias and surface stakeholder perspectives? |
| 3 | **Bundle and journey awareness** | Did you account for bundle effects and the full user journey, including procurement and admin? |
| 4 | **Pre-committed success / failure criteria** | Did you define what success and failure look like upfront? |
| 5 | **Validation before commitment** | Did you prototype or validate before committing real resources? |

A strong analysis hits all five. A weak analysis hits one or two and assumes the others are obvious.

---

## Criterion 1 — Problem identification

> **Did you identify the right problem before jumping to solutions?**

### Strong (4–5)

- States the problem in concrete, specific terms (segment + job + blocker + cost), not in abstract feature-request terms
- Distinguishes between the *symptom* (what users complained about) and the *root cause* (what actually drives the behavior)
- Considers and rejects alternative diagnoses with reasoning
- Identifies whether the bottleneck is friction (designable around) or incentive (structural)
- For complex situations, applies the Five Whys or "what would have to be true" to stress-test the diagnosis

### Adequate (3)

- States the problem clearly but in somewhat generic terms
- Identifies one diagnosis without considering alternatives
- Doesn't explicitly distinguish symptom from cause but the analysis implicitly addresses the cause

### Weak (1–2)

- Jumps to a solution without articulating the problem
- States the problem as a feature request ("users want X")
- Confuses preference signals with rejection signals
- Treats stated user wants as ground truth without stress-testing

### Example: a strong vs. weak problem statement

**Weak:**
> "Users want better collaboration features in our live-streaming product."

**Strong:**
> "Solo creators running daily Talk shows are blocked from collaborating because today's workaround (private Discord) costs them 20–40 minutes of pre-stream prep, and bringing on viewers leads to poor-quality conversation 60–70% of the time. The tool problem is real, but it's not what's stopping top-tier creators from collaborating — for them, the structural cost (going offline on their own channel, losing subscribers and ad revenue) is the actual blocker."

---

## Criterion 2 — Framework discipline

> **Did you apply a framework to remove bias and surface stakeholder perspectives?**

### Strong (4–5)

- Uses an explicit framework appropriate to the question (RICE for prioritization, Kano for feature tier, JTBD for feature decisions, one-way/two-way doors for risk)
- Names tradeoffs the framework forces the team to confront, not just the score
- Identifies stakeholders who would view the decision differently and articulates their position fairly
- Knows when *not* to use a framework (one-way doors, strategic bets, existential decisions)
- Does not break ties with false precision (score 7.4 vs. 7.6)

### Adequate (3)

- Names a framework and applies it to the central decision
- Surfaces the major tradeoffs, possibly missing one or two stakeholder perspectives
- Uses the framework as a structuring tool, not a tiebreaker

### Weak (1–2)

- No explicit framework — analysis is purely intuition or anecdote
- Cites a framework but doesn't actually apply it (mentions Kano then ignores it)
- Treats the framework's score as the decision rather than as one input
- Misses obvious stakeholder perspectives (e.g., engineering, sales-rep economics, regulatory)

---

## Criterion 3 — Bundle and journey awareness

> **Did you account for bundle effects and the full user journey, including procurement and admin?**

### Strong (4–5)

- Explicitly considers how the decision interacts with adjacent products / features in a multi-product context
- Names cross-team dependencies (billing, support, marketing, legal, data pipelines) that affect feasibility
- For B2B: considers procurement, security review, IT signoff, admin onboarding
- Names downstream effects on the bundle (does this deepen or hollow it?)
- Considers sales-rep economics in B2B contexts
- Maps the user journey end-to-end, including discover → buy → onboard → habituate → renew

### Adequate (3)

- Considers the immediate user experience well
- Mentions one or two cross-functional dependencies
- Misses some of the bundle/procurement/admin nuance

### Weak (1–2)

- Treats the feature as standalone, ignoring bundle effects
- Ignores cross-team dependencies
- Skips procurement / admin / onboarding considerations in B2B contexts
- Doesn't consider how the decision affects sales motion or rep incentives

---

## Criterion 4 — Pre-committed success and failure criteria

> **Did you define what success and failure look like upfront?**

### Strong (4–5)

- Names a specific success metric, threshold, and timeline
- Names a specific failure metric, threshold, and timeline
- Names an acceptable failure range (what's a learning vs. what forces a kill)
- Identifies which strategic assumptions, if falsified, would force a strategy change
- Names guardrail metrics that should *not* go down while the primary metric goes up

### Adequate (3)

- Names a primary success metric with a target value
- Acknowledges what underperformance might look like, but doesn't formalize a kill threshold
- Identifies the headline metric but not the guardrails

### Weak (1–2)

- Generic success criteria ("we want users to love it")
- No quantitative threshold
- No kill criterion — failure is implicitly defined as "it didn't work" (subjective)
- No guardrails — open to optimization at expense of unmeasured things

---

## Criterion 5 — Validation before commitment

> **Did you prototype or validate before committing real resources?**

### Strong (4–5)

- Names specific validation steps (concierge MVP, technical spike, lighthouse customer co-design, conjoint analysis, A/B test) before commitment
- Uses validation to test the *hard* assumptions, not just the easy ones
- Validates with the *strategically necessary* segment, not just the convenient one
- Distinguishes revealed vs. stated preferences in the validation design
- For irreversible decisions (one-way doors), the validation rigor matches the irreversibility

### Adequate (3)

- Acknowledges the need for validation
- Names a general approach ("we'll do user research") without specifics
- Validates the central hypothesis but may miss adjacent assumptions

### Weak (1–2)

- No validation step before commitment
- Treats stakeholder approval as validation
- Validates with the convenient segment, not the strategic one
- Ignores the difference between stated and revealed preference
- Treats irreversible decisions as if they were two-way doors (low rigor)

---

## Scoring

Each criterion is scored 1–5. Total: 5–25.

| Total | Interpretation |
|---|---|
| 22–25 | Strong PM analysis. Ready for exec review. |
| 17–21 | Solid analysis with one or two gaps to close. |
| 12–16 | Functional but missing material elements. Re-work before recommending. |
| 5–11 | Weak. The analysis is closer to opinion than recommendation. |

A useful follow-up question for any 3-or-below score: *what specific evidence would move this to a 4 or 5?* Frame the gap as a missing input, not a personal critique.

---

## Common failure patterns

A non-exhaustive list of patterns that show up in weak PM analyses:

- **Solution-first thinking.** Jumps to "we should build X" without articulating which user problem and why now.
- **Persona theater.** Heavy persona work with no JTBD application — the personas don't actually drive feature decisions.
- **NPS as PMF.** Confuses user love with business viability.
- **Free adoption as PMF.** Confuses "people are using it" with "people would pay for this."
- **No kill criteria.** Every result becomes negotiable; the team rationalizes shipping the thing they already built.
- **Convenient-segment validation.** Tests with users it's easy to reach, not users the strategy depends on.
- **Hope-as-strategy.** GTM plan depends on a specific behavior from a specific segment, with no plan for that behavior.
- **Friction-fixation.** Treats every adoption problem as a friction problem when many are incentive problems.
- **One-way-door blindness.** Treats irreversible decisions with the rigor of reversible ones.
- **Standalone-only metrics.** Measures the feature without considering bundle or cross-product effects.

When any two of these show up in a single analysis, the work needs another pass.

---

## How to use this rubric

For self-assessment: score your own analysis, then identify the lowest score and re-work it specifically.

For peer review: walk through the five criteria with a colleague. The conversation about *why* a score is what it is, is more valuable than the score itself.

For coaching: use it to give specific feedback. *"Your problem identification is a 4 — strong. Your validation plan is a 2 — you're missing a way to test the assumption that top-tier creators will adopt. Specifically, what's the four-week alpha that proves it?"*
