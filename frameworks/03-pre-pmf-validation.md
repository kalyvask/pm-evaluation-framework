# Phase 3 — Pre-PMF Validation

**Focus:** Find signal to scale. You've shipped something. Before you pour growth dollars in, you need evidence that users actually want what you built — and that you can sell it.

---

## "10 Happy Users" Rule

Before measuring NPS or retention curves, find ten **non-friend** users who genuinely love the product. Not ten users who tried it. Ten who would be visibly upset if it disappeared.

If you cannot name them, you have a usage problem, not a metrics problem. No amount of funnel optimization fixes a product that ten strangers don't love.

This is also a useful counter to "free adoption ≠ PMF": ten people who took a free trial and never came back are not a signal of anything.

The rule has a second half that most teams skip: once you can name the ten, **ask what they have in common.** Ten lovers with nothing in common is ten lucky accidents. Ten lovers who all arrived from the same prior workaround, in the same role, using the same two features, is a segment definition — and it's the most valuable artifact this phase produces. The mechanic for extracting it is in "Lovers, likers, and the disinterested" below.

---

## Sean Ellis Test

Ask current users: *"How would you feel if you could no longer use this product?"*

Options: very disappointed / somewhat disappointed / not disappointed / N/A.

Below ~40% "very disappointed" is generally taken as a signal of weak PMF — though the threshold varies by category and segment, so use it as directional, not as a pass/fail. Slice the response by user segment; PMF often exists for a narrower group than you assumed.

The most useful data is in the open-ended follow-up: *"What would you use as a replacement?"* The answers reveal the actual competitive set, which is usually different (and often more dangerous) than the deck slide.

**Treat the result as a segmenter, not a score.** The percentage is the least useful output of the question. The useful output is the three *name lists* — who said very disappointed, who said somewhat, who said not. A team that reports "we're at 31%" has thrown away the data. A team that reports "our 31% are all ops leads who came in through the API" has the roadmap.

---

## Lovers, likers, and the disinterested

The single most common roadmap failure pre-PMF is building from the feedback of people who aren't interested in the product. Churn surveys, lost-deal reports, and support tickets all sample the same population by construction: users who already decided this isn't for them. Their feedback is articulate, specific, and almost always the wrong input.

The discipline is to aim at the other end. **Partition users by intensity, then build for the two bands that are already engaged — the ones who love it and the ones who kind of like it — around what those two bands have in common.** The disinterested are the only group you deliberately stop serving.

Both engaged bands matter, for different reasons. The lovers tell you what the product *is*: their commonality is the sharpest available description of who it's for, usually narrower and stranger than the one in the deck, and they're the only band that refers, so word of mouth scales with their count. The likers are the nearest available growth: they've already chosen to stay, they share most of the lovers' behavior, and the gap between the two bands is the shortest path to more lovers you will ever find. Chasing the disinterested means building for people who have to be convinced from zero; moving a liker up means removing one specific obstacle for someone already halfway there.

### The three bands

| Band | Behavioral signature | Survey signature | Role in the roadmap |
|---|---|---|---|
| **Lovers** | Retained on a flat curve, deep usage, returns unprompted, refers others, has tried to build a version themselves, absorbs price increases | "Very disappointed" | Define the segment, the shared core, and the positioning language. Depth investment goes here |
| **Likers** | Retained but shallow. Uses when reminded. Substitutable. Churns on a price increase or a competitor promo | "Somewhat disappointed" | The conversion population. What's blocking them is the highest-yield work on the board |
| **Disinterested** | Tried and stopped, or uses under duress (admin-mandated, bundled, free) | "Not disappointed" / N/A | Diagnosing acquisition mistargeting. Not roadmap input |

Two disciplines about the bands themselves:

- **Draw them from behavior first, survey second.** The default banding from analytics alone: not retained → disinterested; retained but shallow → liker; retained *and* deep (above the frequency threshold, using more than one distinct part of the product) → lover candidate. Where behavior and survey disagree, behavior wins; the survey's job is to explain the band, not define it.
- **Band at the right unit.** In B2B, an account can look like a lover while containing two lover users inside four hundred disinterested seats. That churns the moment one champion leaves. Band at both the account and the user level and keep both numbers. See `decision-making/user-vs-chooser.md` for the related buyer/user split.

One check before promoting a heavy user to lover: **depth can be thrash.** Forty clicks to do a five-click job looks like engagement and is actually friction. A power user of a frustrating product is not necessarily in love with it.

### Find the commonality on three axes

Run the analysis on the lover band and the liker band separately, with the disinterested held out as a contrast.

1. **Who they are** — role, seniority, company size, industry, technical sophistication, acquisition channel. In consumer: life stage, use context, occasion of use.
2. **What they were doing before** — the replaced behavior and the workaround. Engaged users arrive from a specific painful prior state, and that prior state predicts better than any demographic. "Was maintaining this in a spreadsheet and had already written a script for part of it" is a segment definition. "Mid-market" is not. This is the desperation signature from `decision-making/finding-pmf.md` § "Need is irrelevant" read backwards from the users you already have.
3. **What they do in the product** — which features, in what sequence, at what frequency, within what window of signup.

A commonality is only worth acting on if it's **findable** (you can go acquire more people who match it) or **buildable** (you can create the condition in-product). "Our engaged users all have a colleague who also uses the product" is buildable — it becomes an invite flow. "They're all unusually patient" is neither; it's a survivorship artifact, and it means onboarding is filtering rather than converting.

### Three cuts of the same data

Axis 3 is where most teams stop too early, usually by pulling the lovers' top features by usage volume. That list will be login, home, search, and the primary object view — because those are everyone's top features. It contains no information.

Cut the feature data three ways instead. Each cut answers a different question and feeds a different part of the roadmap.

| Feature | Lovers | Likers | Disinterested | Read |
|---|---|---|---|---|
| Search | 98% | 95% | 34% | **Shared core.** Both engaged bands live here |
| Project timeline | 89% | 81% | 12% | **Shared core.** The reason both bands stay |
| Shared workspace | 74% | 12% | 2% | **Separator.** The gap between liking and loving |
| Keyboard shortcuts | 61% | 9% | 1% | **Separator** |
| Custom reports | 22% | 19% | 15% | Neutral. Used by everyone a little, load-bearing for no one |
| Legacy importer | 8% | 11% | 41% | **Disinterested-only.** Serving a band that never engages |

**Cut 1 — what the two engaged bands share.** Features with high adoption in both lovers and likers, and low adoption among the disinterested. This is the **shared core**: the actual product, the thing that made anyone stay. It gets the steady investment. Teams routinely under-fund it because it doesn't look like a differentiator in the lift analysis — but it's what both of your real bands use every day, and letting it rot is how you lose likers before you ever convert them.

**Cut 2 — what only the lovers do.** Features with high lover adoption and low liker adoption. These are the **separators**, and they're the most actionable thing in the table: they describe, concretely, the difference between someone who likes the product and someone who can't work without it. The separator is your conversion hypothesis. "Lovers collaborate in a shared workspace; likers work alone in it" turns into "get the second person into the workspace" — a specific, buildable intervention on the middle band.

The separating threshold is also your activation target. For each separator, find the usage count and time window that best splits the bands — "used the shared workspace with a second person within seven days." That threshold *is* the activation event, not a proxy for it. See `decision-making/activation.md`.

**Cut 3 — what only the disinterested do.** Features used mainly by the band that never engages. These are the cut and de-investment candidates. Not automatically a kill (a legacy importer may be a necessary migration path), but a reason to stop putting roadmap capacity into a surface that no engaged user touches.

### Pulling the middle up

The likers are the largest source of new lovers you have, and they're the band most teams neglect — first by ignoring them in favor of the tail, then by over-correcting and building whatever they ask for. Neither is right. The work is to identify what's holding them at "kind of like it" and remove it.

Three inputs, in descending order of reliability:

1. **The separator gap.** Cut 2 already told you which behavior lovers have and likers don't. Start there — it's behavioral, it's specific, and it doesn't depend on anyone accurately reporting their own motivation. Most of the time the liker isn't rejecting the separator feature; they never got to it, or hit friction the lovers pushed through.
2. **The blocked-benefit request.** A liker who says "I'd use this more if the collaboration were faster" — where collaboration is the shared core or a separator — is naming a removable obstacle on the path you already know works. High-yield, straightforward to act on.
3. **The different-benefit request.** A liker who says "I'd use this more if it also did invoicing" is asking for an adjacent product. Weigh these carefully rather than reflexively: one or two of them may be a real surprise worth savoring (see `decision-making/finding-pmf.md`), but a roadmap built mostly from them drifts the product toward the average of everyone's requests, which is the flat-smile-curve failure. The test is whether the request keeps the shared core load-bearing or routes around it.

The band you *don't* build for is the disinterested: the users who tried it and left, the mandated seats who never engaged, the lost deals that wanted a different category of product. That decision needs to be written down explicitly with the reasoning, or it leaks back in through escalation three weeks later. The prioritization consequences are in `decision-making/prioritization.md` § "Route requests by band before scoring them."

### Traps

- **The friend trap.** Friends, investors, and design partners with a relationship stake are not evidence. This is why the ten-happy-users bar specifies *non-friend*.
- **The free-rider trap.** Enthusiasm at $0 is not love. Test the band with a price change or a straight willingness-to-pay conversation. Love that evaporates at the first invoice is a hobby.
- **The n-of-3 trap.** Any three users have something in common. The question is never "what do lovers share?" but "what do lovers share *that likers don't*?" Commonality without a control group is astrology.
- **The unmonetizable lover.** A segment can be genuinely desperate and structurally unable to pay. The answer is the adjacent segment with the same job and a budget, not monetizing the lovers harder.
- **The shrinking niche.** The lover segment is real, desperate, and getting smaller every year. Check the direction of the segment before committing the roadmap to it.
- **Aggregating the bands away.** "Our NPS is 42" instead of "our lovers are 8% of users and they're all ops leads at logistics companies with an existing spreadsheet workflow" discards the only actionable information.
- **Treating the middle as a lost cause.** The opposite failure to roadmapping from churn, and a real one. Likers already chose to stay; writing them off as "not our user" throws away the cheapest conversion population you have and leaves the shared core under-funded.

### When the lovers aren't who you targeted

The most valuable outcome here is also the most disruptive: the commonality names a segment you didn't aim at. This is the savor-the-surprise case from `decision-making/finding-pmf.md`. The response is to re-aim at the lovers, which usually shrinks the addressable market on paper and grows it in reality — Moore's beachhead logic, *provided the beachhead has an adjacency path* to the next segment.

The honest counter-question before re-aiming: is the lover segment large enough, and growing, to be the business you intend to build? Love is necessary and not sufficient.

---

## Activation Rate / Time to Value (TTV)

Two paired metrics:

- **Activation rate** — % of new users who reach the *aha* moment in their first session (or first N days, depending on category).
- **Time to value** — median elapsed time from sign-up to that *aha*.

Define *aha* concretely. "Sent first message" is concrete. "Engaged with the product" is not.

Bad activation kills good acquisition. If 60% of sign-ups never hit *aha*, doubling acquisition spend doubles the wasted users, not the active ones. Fix activation before scaling acquisition.

---

## GTM Strategy Checklist

Before claiming PMF, validate the *go-to-market* plan, not just the product:

- **ICP** — who is the ideal customer profile, named specifically? "SMB" is not an ICP; "operations leader at 50–200-person logistics company in North America" is.
- **Sales motion** — PLG, sales-assist, or sales-led? Does the price point support that motion?
- **Distribution** — what channel(s) reach the ICP repeatably? Have you proven any of them work?
- **Pricing** — what value metric, what willingness to pay, what packaging? How much friction does the price create at the point of sale?
- **Sales-rep economics** (in B2B) — does the rep make enough commission per deal to prioritize this product? **Coin-optimized reps will not push a product without commission upside, no matter how good it is.**

In B2B, **distribution is product**. A technically superior product that doesn't get in front of buyers has zero value. If your launch strategy assumes reps will carry the product without an incentive, that is a launch-blocker, not a launch-detail.

---

## Smile Curve

Plot a histogram of user engagement frequency over the last 30 days. The healthy shape is a *smile*: a tall left bar (users who churned), a short middle (occasional users), and a tall right bar (users who use it heavily).

A flat or frowning shape (most users in the middle) usually indicates a product that's *nice to have* — useful enough to keep around, not useful enough to commit to. Flat-shape products typically don't survive contact with a competitive market.

A smile shape is a sign that the product has true believers, even if many users churn. PMF often lives on the right tail.

The smile curve is the three bands plotted: the right-hand bar is the lovers, the middle is the likers, the left bar is the disinterested. A frowning curve — mass in the middle, nothing at either end — usually means the roadmap has been built from undifferentiated request volume: every band served a little, none served well enough to move up. The fix is upstream of the curve, in whose feedback drives the backlog and whether the middle is being pulled toward the tail or just maintained where it is.

---

## ARC PMF Framework

Three dimensions:

- **Acquisition** — can you get users efficiently? Are CAC and channel economics defensible?
- **Retention** — do users stay? Cohort curves should flatten, not collapse.
- **Consumption** — once retained, do users use it deeply? More accounts? More seats? More usage per session?

PMF requires evidence on all three. Strong acquisition with collapsing retention is a viral curiosity. Strong retention with no consumption growth is a niche tool. Strong consumption with no acquisition path is a nice-to-have for a small group.

---

## What "PMF" actually means

Three things that are easy to confuse:

- **Free adoption ≠ PMF.** People will try anything that's free. PMF requires evidence that people would *pay*, *renew*, or *switch from an existing solution*.
- **Strong NPS ≠ PMF.** A product can have unusually high NPS and still fail to find a sustainable economic model. NPS measures love, not viability. See `decision-making/value-hypothesis.md` § "The inclusion vs. control tension" for the version of this that shows up in regulated categories.
- **Usage ≠ PMF.** Free trials, internal employee usage, and "I tried it once" all count as usage. PMF requires retained, growing, willing-to-pay usage from your ICP.

The hardest question in this phase is honest: *would users still use this if it cost what it should cost to run?*

---

## When this phase is done

You should be able to answer:

1. Who are the ten happy users? What do they have in common on all three axes — who they are, what they did before, what they do in the product?
2. What do the lovers and the likers have in common — the shared core — and what separates them?
3. What's the activation rate, time to value, and Sean Ellis "very disappointed" %? Who specifically is in each band?
4. What does the smile curve look like?
5. What's holding the likers at "kind of like it," and what's the specific intervention to move them up?
6. Which band have we explicitly decided not to serve, and is that decision written down?
7. What's the GTM motion that gets us from here to scale, and have we proven any of its core assumptions?

If you can't answer these with real data — not aspirational projections — you do not have PMF, regardless of how the deck reads.
