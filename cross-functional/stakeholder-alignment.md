# Stakeholder alignment

The PM sits at the intersection of engineering, design, sales, support, marketing, finance, legal, and leadership. The job is to keep them aligned on the right thing without becoming a meeting-coordination function.

---

## Bundle thinking

In multi-product companies, decisions are rarely made in isolation. A new feature, a new product, a new pricing change — each interacts with the *bundle* of products and the cross-team dependencies that exist around it.

Three implications:

### 1. Standalone metrics undersell good bundle moves

A new product might pay for itself by deepening the bundle relationship — primary account, default integration, share of wallet — even if its standalone metrics look weak. Conversely, a standalone "winner" can hollow out the bundle by attracting users who only want that one feature, never expand, and never become primary-account holders.

When evaluating a feature in a multi-product company, always include both:

- **Standalone metric** (adoption, retention, engagement of the feature itself)
- **Bundle metric** (impact on primary-product retention, on share of wallet, on cross-product usage, on direct relationship)

### 2. Cross-team dependencies are the real coordination cost

Most teams under-estimate how much of the work is in *other* teams. A feature that requires changes from billing, support, marketing, legal, and a data pipeline team is a 5x coordination problem disguised as a feature.

Surface dependencies early, with named owners and timelines. The default failure mode: PM identifies the dependencies in the spec, doesn't get explicit commitments from each team, assumes everyone will do their part, ships a feature where one of the five missing pieces breaks the experience.

### 3. Procurement and admin are part of the user journey

Especially in B2B. Even if the end user loves the product, if the procurement process is hostile (long approvals, custom contracts, security reviews, IT signoff), the product doesn't get adopted. A clean end-user experience is necessary but not sufficient.

When story-mapping the user journey, include the *buying* journey — discovery, evaluation, procurement, deployment, admin onboarding, support. Most B2B products lose more deals here than in the actual user experience.

---

## Acquisition integration: think two steps ahead

When a company acquires a product/team, the PM running the integration faces a forking decision:

**Option A — Quick value demonstration.** Hack adapters and bridges to get the acquired product showing value inside the acquiring company's stack within 1–2 quarters. Looks fast. Builds momentum. Defers the architectural work.

**Option B — Proper platform integration.** Take 12–18 months to integrate the acquired product into the acquirer's governance, permissions, data, and platform stack. Slow. Painful. Sets up the next 5 years of feature velocity.

Both are sometimes right. The wrong move is *picking one without thinking two steps ahead*. Specifically:

- If you pick Option A and never plan for Option B, every new feature on the acquired product will require workarounds. Four-week features stretch to twelve. Bugs cascade. The team eventually faces a refactor-vs-rebuild decision under worse conditions than today.
- If you pick Option B and don't ship anything for 18 months, customer trust erodes. Sales loses its near-term answer. Competitors ship while you platform.

The right move is usually a *combination*: a small, time-boxed Option A to maintain momentum, with a credible commitment to Option B that engineering and leadership both believe.

(See `case-patterns/refactor-vs-rebuild.md` for the canonical example, anonymized.)

---

## Leadership credibility is a precondition, not an outcome

When you walk into an exec review with a recommendation, the credibility you've built before that meeting determines whether the recommendation gets heard.

Things that build leadership credibility:

- Pre-committing kill criteria, then honoring them
- Telling leadership about problems before they hear from elsewhere
- Public ownership when things go wrong
- Concrete asks (headcount, air cover, narrative alignment) — not vague support requests
- Postmortems that surface real learning, not defensive narratives

Things that destroy it:

- Walking in with "we failed, what now?" framing
- Asking for resources without a clear theory of how they'll be used
- Repeated re-litigation of decisions previously thought settled
- Surprising leadership with bad news
- Inflating projections to justify investment, then missing them

If credibility is eroded, the right move is not to wait for it to recover. It's to stage a series of small, concrete, deliverable wins that visibly close the gap between what was promised and what was delivered. Credibility is rebuilt by under-promising and over-delivering, repeatedly, in public.

---

## How to walk into a hard exec conversation

Three things to bring:

1. **A blameless postmortem of what didn't work.** This establishes that your judgment is still trustworthy — that you can see clearly even when the news is bad.
2. **A clear recommendation.** Not three options weighted equally. *This* is what we should do, *here's why*, *here's what I'm willing to bet.* Strong opinions, openly held.
3. **A specific ask.** Headcount, exec air cover for sales conversations, public internal narrative alignment, runway, deadline relief. Vague support is not actionable; vague asks signal that you don't know what you need.

Avoid:

- Walking in with "what should we do?" (your job is to recommend, not survey)
- Walking in with "everything's fine" when it isn't (leadership senses dishonesty)
- Walking in without owning the parts that went wrong (kills credibility)

---

## When the team disagrees with leadership

It happens. Two failure modes:

- **Capitulate.** Team disagrees, PM caves to leadership, team disengages. Leadership gets bad work because the team has stopped believing.
- **Open dissent.** Team and PM publicly fight leadership. Leadership doubles down. Team and PM lose credibility.

The healthier path:

1. **Surface the disagreement to leadership directly, in private.** Specifically. "Here's what you're asking for. Here's what we believe will happen. Here's the evidence. Here's the alternative we propose."
2. **Negotiate a small experiment.** "We can run a 4-week test of our approach with a defined cohort. If we don't see X, we go your way."
3. **If leadership still says no, commit fully.** No grumbling to the team, no "well, leadership made us." Take the call. If it goes wrong, own it.

The asymmetry: you don't have to win every disagreement. You have to be *willing to disagree*, *willing to stake credibility on it*, and *willing to commit when you lose*.

---

## Sales and customer success: managing for renewal, not first contract

A common PM blind spot in B2B: optimizing the product for the buyer (the procurement / executive who signed the contract) when the people who renew are the *users* (the team that has to actually use it day-to-day).

The buyer evaluates on slides and demos. The users evaluate on whether the product works for them on Wednesday at 3pm.

Two specific moves:

1. **Build the product the users will renew on.** Even if it makes the demo less impressive, the renewal-rate impact is larger.
2. **Talk to users, not just buyers.** Sales will introduce you to the buyer (the relationship they manage). You have to push for access to the users (the relationship that determines renewal).

In SaaS, retention is more valuable than acquisition. The product earns retention, not the contract.

---

## Decision checklist

Before any major cross-functional commitment:

1. Have I surfaced cross-team dependencies with named owners and timelines?
2. For multi-product cos: have I identified the bundle effect — positive or negative?
3. For B2B: have I mapped the procurement journey, not just the user journey?
4. For exec reviews: am I bringing a blameless postmortem, a clear recommendation, and a specific ask?
5. If I disagree with leadership: have I made the disagreement explicit and proposed a small experiment to resolve it?
6. For SaaS retention: am I building for the user who renews, not just the buyer who signs?

If two of these are weak, the alignment is fragile.
