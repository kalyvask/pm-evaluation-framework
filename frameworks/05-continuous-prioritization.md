# Phase 5 — Continuous Prioritization

**Focus:** Improve the North Star via deliberate bets. Every PM eventually has a backlog longer than the team's capacity. The job is to choose well, repeatedly, in public.

---

## RICE Scoring

Score each proposed bet on four dimensions:

- **Reach** — how many users (or accounts, or revenue dollars) does this affect per period?
- **Impact** — how meaningful is the change for each affected user? Use a simple scale: 0.25 (minimal) / 0.5 / 1 (moderate) / 2 / 3 (massive).
- **Confidence** — how confident are we in our reach and impact estimates? 50% / 80% / 100%.
- **Effort** — person-months to ship.

`RICE = (Reach × Impact × Confidence) / Effort`

Two important cautions:

1. **Don't break ties with false precision.** A RICE of 7.4 vs. 7.6 is noise. Treat the score as an order-of-magnitude tool, not a ranking.
2. **Confidence is the most-gamed input.** Teams routinely overstate confidence on their favorite projects. Calibrate by going back to the last quarter's RICE scores and asking how often the high-confidence bets actually delivered.

---

## WSJF (Weighted Shortest Job First)

`WSJF = Cost of Delay / Job Size`

Cost of Delay combines:
- **User/business value** — what's gained when this ships?
- **Time criticality** — does the value decay over time? (e.g. seasonal, competitive window)
- **Risk reduction / opportunity enablement** — does shipping this unlock other work?

WSJF favors small, time-sensitive, unblock-other-work items. It's particularly useful when the team is debating whether to do one big strategic bet or several small unlocks. Often the small unlocks dominate.

---

## Opportunity Scoring

Survey users on two scales for each feature/job:

- **Importance** — "How important is this to you?" (1–10)
- **Satisfaction** — "How satisfied are you with how this is currently solved?" (1–10)

`Opportunity = Importance + max(Importance − Satisfaction, 0)`

The highest-opportunity items are **highly important AND under-served** today. This is more rigorous than asking "what features do you want?", which surfaces stated preferences (often features users have seen elsewhere) rather than revealed gaps.

Pair with the "what are you using as a workaround?" follow-up — users with painful workarounds (spreadsheets, copy-paste, separate tools) reveal genuine opportunity.

---

## Storytelling Narrative

Every major feature on the roadmap should connect to the **North Star story** in one sentence. If you can't draw the line, the feature is either out of scope or the strategy is wrong.

This serves two functions: it kills feature scope creep ("does this connect to the story?") and it forces the team to hold a coherent narrative for execs, sales, and customers.

A useful test: ask three people on the team to describe the product strategy in one sentence. If the answers diverge, the storytelling layer is broken — and prioritization arguments will keep recurring as proxy fights for the missing strategy.

---

## North Star Metric

A single metric that captures the core value the product delivers to users. Not revenue (that's an outcome), not engagement (that's too generic) — the *one thing* that, if it goes up, indicates the product is delivering more value to more users.

Examples by category:
- Communication tool → messages sent between users
- Marketplace → completed transactions
- Analytics tool → reports created and shared
- AI assistant → tasks completed end-to-end without retry

The North Star should be:
1. Reflective of *user value*, not internal effort
2. **Leading**, not lagging — moves before revenue does
3. Hard to game without actually serving users better
4. Shared across the org — same number on every dashboard

If two teams optimize for different North Stars, you don't have a North Star. You have local optima.

---

## Match metrics to strategy assumptions

A common mistake: tracking metrics that don't reflect what you're betting on.

If your strategy assumes top-tier creators will adopt and drive smaller-creator imitation, then *adoption among the top tier* is your key metric — not aggregate adoption. If your strategy assumes enterprise customers will switch from a competitor, then *switching events* matter — not new sign-ups.

Before locking in a metrics dashboard, list your strategic assumptions and ask: which metric, if it moved, would falsify that assumption? **That's the metric to track.**

---

## When NOT to RICE

Some decisions are not amenable to scoring:

- **One-way doors.** Score-and-rank logic is for two-way doors. One-way doors require explicit hypothesis testing, pre-mortems, and named risk-owners — not a number.
- **Strategic bets.** A bet to enter a new market, build a new platform, or change the business model is not a "score this against feature X" exercise. It needs a strategic rationale, not a RICE row.
- **Existential decisions.** Whether to kill a flagship product, whether to do a major rewrite, whether to fire an executive — none of these belong in the prioritization framework. They belong in a memo.

Use the prioritization frameworks for the everyday backlog. Use the strategy frameworks for the bets that change the company.

---

## When this phase is done

This phase is never done. That's the point. Continuous prioritization means:

1. Every quarter, the top 5–10 bets are explicit and connect to the North Star
2. Each bet has a kill criterion — what would we see that makes us stop?
3. Last quarter's bets are reviewed honestly: which ones moved the metric we said they would?
4. The team has a written narrative — not just a list — of why these bets, in this order, now.

If any of those is missing, the prioritization layer is failing, even if the team is shipping a lot.
