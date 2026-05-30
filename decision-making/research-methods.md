# Research methods

Personas, JTBD, Kano — when to use each, and how not to misuse them.

> Method *selection* is in this file. *How to actually run* a customer-discovery interview without collecting false positives is in [`customer-interviews.md`](customer-interviews.md). The two are complementary: this file picks the instrument; that file teaches you to wield it.

---

## Personas vs. Jobs-to-be-Done

The most common research-method confusion in PM work. They are different tools for different stages.

### Personas

A **persona** is a synthesized profile of a user segment: demographics, goals, frustrations, behavior patterns. Useful for:

- Top-of-funnel ideation — *who are we even building for?*
- Stakeholder alignment — *when sales/marketing/eng say "user," do we mean the same thing?*
- Market segmentation — *which segments are large enough to be worth pursuing?*
- Storytelling — *making the user feel real to a leadership audience.*

Personas are a *framing* tool. They are too abstract to drive feature-level decisions.

### Jobs-to-be-Done

A **job** is what a user is hiring the product to do, in a specific situation, with a specific desired outcome. Useful for:

- Feature decisions — *which job is this feature serving, and how well?*
- Prioritization — *which jobs are most frequent, important, and under-served?*
- Workaround analysis — *what are users using today to get this job done? What's wrong with it?*
- Surfacing latent demand — *what jobs are users doing badly with duct-tape solutions?*

JTBD is a *decision* tool. It lets you score and choose.

### The hybrid approach

Use personas to define the *target segment(s)*. Then switch to JTBD to define the *features*.

> "Our target persona is the operations leader at a mid-market logistics company [persona work]. The top three jobs we're going to serve are reconciling carrier invoices, predicting freight delays, and generating end-of-quarter reporting [JTBD work]."

Without personas, JTBD work tends to drift across user types and lose focus. Without JTBD, persona work tends to produce features no one specifically asked for. The combination is stronger than either alone.

### Common mistake: writing JTBD as a persona

> "When I'm a busy professional, I want to feel productive."

That's a persona statement dressed as a job. A real JTBD statement is:

> "When my CRM updates aren't reflected in my email signatures, I want a single update flow so I don't have to remember to change three places when I change roles, so I avoid sending stale signatures to clients."

Specific situation. Specific motivation. Specific desired outcome. Specific cost of failure.

---

## Kano model

Plot features on two dimensions: *implementation* × *user satisfaction*. Three feature tiers:

| Tier | Behavior | Examples |
|---|---|---|
| **Must-be (basic)** | Absent → strong dissatisfaction. Present → no satisfaction boost. | Stability, security, governance, table-stakes integrations |
| **Performance** | Linear: more / better → more satisfaction. | Speed, accuracy, sharing, completeness |
| **Delighter (attractive)** | Absent → unfelt. Present → strong satisfaction boost. | Unexpected magic features, novel capabilities |

### Two implications most teams miss

**1. Failing on must-be is the most damaging.** Dissatisfaction compounds. No amount of delighter features compensates for broken basics. If your product has must-be failures (frequent crashes, lost work, broken auth), every other investment is leaking value.

**2. Delighters decay over time.** Today's surprise is tomorrow's expectation. A capability that was a delighter two years ago migrates to performance, then to must-be, as users come to expect it. AI-assisted features in many categories are mid-migration right now.

The decay-of-delight dynamic means **time is not neutral**. Delaying a feature that's drifting from delighter to must-be raises the cost of catching up every quarter you sit it out.

### How to use Kano in practice

For any feature, ask: *if this is missing, will users be dissatisfied? If it's present, will they be more satisfied? By how much?*

Then plot:

- **Must-be features** are launch criteria. Cannot ship without.
- **Performance features** are continuous-investment areas. Where most of the roadmap lives.
- **Delighters** are bets — high upside, low downside. Worth investing in 1–2 per release; not worth pretending the must-be tier is fine when it isn't.

A common failure: shipping delighters while must-be is broken. Users are not delighted by clever features when the basics fail.

---

## Conjoint analysis

When you need to know which features users *value most*, conjoint analysis is more reliable than asking them directly.

You present users with bundles of features at different prices and ask them to choose. Their choices reveal preferences they often can't articulate. This is **revealed preference** vs. **stated preference**, and the gap between the two is often huge.

Stated preferences are biased toward features users have seen elsewhere or features that sound impressive. Revealed preferences are biased toward what users would actually pay for.

When making pricing or packaging decisions — what to bundle, what to charge, where to break tiers — conjoint produces better answers than focus groups.

### When conjoint is overkill

For most early-stage product decisions, conjoint is too expensive (sample size, design complexity) and too slow. Use it when the decision is high-stakes (pricing, packaging, market entry) and the stated/revealed gap is likely large (B2B enterprise users, novel categories).

---

## The "right segment" trap

The most common research mistake is **researching with the convenient users instead of the strategically necessary ones**.

If your GTM strategy depends on top-tier creators / enterprise customers / regulated buyers, then your research must include them. If you only test with the smaller, easier-to-reach segment, you will design a product the easy segment loves and the necessary segment ignores.

When this happens, the team's research is sound but applied to the wrong cohort. The product launches, the easy segment adopts, and the necessary segment never shows up — because they were never asked.

Test: before any UXR study, ask *which segment, if it doesn't adopt this, kills the strategy?* That segment must be in the study, even if they're harder to recruit.

---

## Stress-tests for any user research signal

Before treating UXR as a tiebreaker:

1. **Segment size** — how many users feel this way? What % of revenue / target?
2. **Switching cost** — would they actually switch, or just say they would?
3. **Stated vs. revealed** — have any users *done* this thing, or just said they would?
4. **Strategic segment included?** Did we research with the segment that defines whether the strategy works?
5. **Workaround analysis** — what are users using today? How painful is the workaround?

UXR signals that pass these stress tests are usable as decision inputs. Signals that don't pass are interesting; they're not yet decisional.

---

## Right-sizing exploration to stakes

The most common research-scope failure: the default scope (often "talk to 30 users and synthesize") that gets applied regardless of the question.

The right scope is a function of the cost of being wrong, not of how thorough the PM wants to feel. Reversible software two-way doors justify smaller samples and faster iteration. Hardware, public commitments, brand-defining promises, and one-way doors justify larger samples and more upfront validation.

A rough calibration:

| Stakes | Reversibility | Right-sized exploration |
|---|---|---|
| Small reversible (a feature in a fast-iterating product) | Two-way | 3-5 users, iterate weekly |
| Medium reversible (a major feature, a market launch) | Two-way | 8-15 users, segmented by hypothesis |
| Large reversible (a strategic redirect inside the same market) | Two-way with cost | 20-40 users, both qualitative and quantitative |
| Irreversible / expensive (hardware, public API, brand-defining promise, multi-year platform) | One-way | 50+ users, longitudinal, plus structural validation |

The PM who always wants 300 users before any decision over-validates and slows the team. The PM who always wants 3 under-validates and gets it wrong on the bets where being wrong is expensive. The discipline is to *name the stakes explicitly* before picking the scope.

Two specific traps:

- **Hedging by sample size.** When the team is uncertain about the bet, the PM proposes more research to defer the decision. More research often produces no clearer answer; the team needs a sharper hypothesis, not more data. A useful test: if the same study at half the sample would produce the same conclusion, the sample is too large.
- **Under-validating one-way doors.** Reversibility is the most underweighted variable in research-scope decisions. A decision that is hard to walk back deserves disproportionate research, even if it feels slow. The cost of slow validation is much smaller than the cost of an irrecoverable wrong bet.

Before approving a research plan, ask the team to name (a) the falsifying outcome that would change the decision, and (b) the reversibility of the underlying bet. If the answers aren't both crisp, the scope is being chosen by anxiety rather than by stakes.

See [`risk-and-reversibility.md`](risk-and-reversibility.md) for the underlying reversibility framing.

---

## Map the full journey, not just your surface

A common research blind spot: studying only the surface you own. PMs map the funnel inside their product and miss that the drop-off is being driven by something seven steps upstream, where users came from, what they were doing before, what they expect.

The discipline is to map the *full* user journey, even the parts you don't control.

The upstream questions:

- Where are users when they first decide they need a product like yours? Search, a competitor, a friend, a TV show, a job change.
- What were they doing before? A manual workaround, a different product, nothing.
- What expectations do they arrive with from the upstream experience?

The downstream questions:

- Where do they go after using your product? A downstream tool, a meeting, a purchase, a share.
- What is the next decision they have to make, and does your product set them up to make it well?
- Do they tell anyone? Who? In what context?

The reason this matters: most PM funnel analysis treats users as if they appear at the signup screen with no history and disappear when they close the tab. Real user behavior is conditioned by a long chain of context the funnel can't see. When activation rates collapse without an obvious cause, the cause is often outside the funnel.

Two practical patterns:

- **The "what were you doing before you opened our product?" interview question.** Run it on five users. The answer often surprises the team and reveals an upstream assumption no one had named.
- **The "who do you tell about this?" question.** When users churn, ask not just why they churned but what they replaced it with. The substitution pattern often points at a different competitive frame than the team had assumed.

A useful default: any time the funnel data is producing answers that don't match the team's mental model, the model is missing something upstream or downstream of the surface. Map the missing parts before designing the next experiment.

---

## Decision checklist

Before committing to a research-driven product decision:

1. Is this a *segmentation* question (use personas) or a *feature* question (use JTBD)?
2. Have we tested with the strategically necessary segment, not just the convenient one?
3. For Kano analysis: which tier are we in? Are the basics actually working before we invest in delighters?
4. Have we stress-tested the signal — segment size, switching cost, revealed vs. stated?
5. Is there a workaround users currently use? How well does it work? What's wrong with it?

If the answer to any of these is "we haven't checked," the research is not yet ready to drive the decision.
