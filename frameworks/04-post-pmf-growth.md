# Phase 4 — Post-PMF Growth

**Focus:** Efficient, repeatable expansion. PMF is necessary but not sufficient. Once you have it, growth becomes an engineering problem of funnels, retention, and economics.

---

## AARRR (Pirate Metrics)

The canonical funnel:

- **Acquisition** — how do users find you? Channel mix, CAC by channel.
- **Activation** — do they hit *aha* on first use?
- **Retention** — do they come back? Day-1, Day-7, Day-30 cohorts.
- **Referral** — do they tell others? Viral coefficient (K), referral rate.
- **Revenue** — do they pay? ARPU, conversion rate, expansion.

Map drop-off at each stage. The biggest leverage is almost never where you think — most teams over-invest in acquisition when the leak is at activation or retention.

A useful sharpening: **define each stage as a binary user state**, not a metric. "Activated" is a label on a user account, not a number. Only after stages are clearly defined do the metrics make sense.

---

## HEART Metrics (Google's framework)

Five user-experience dimensions, designed for products where AARRR is too transactional:

- **Happiness** — how do users feel? NPS, satisfaction surveys, qualitative feedback.
- **Engagement** — how deeply are users using the product? Sessions per user, actions per session.
- **Adoption** — how many new users are reaching key features?
- **Retention** — do they keep using it? (Same as AARRR.)
- **Task success** — for any specific task, how often do users complete it without error?

HEART is most useful for *features* within a product — pick two or three dimensions per feature and track them. Trying to track all five for everything dilutes attention.

---

## Cohort Retention

For each cohort of new users (by week, month, or campaign), plot the retention curve over time.

A healthy product's retention curve **flattens** — initial drop-off, then a stable base of true users. An unhealthy curve **collapses to zero** — every cohort eventually churns out, and growth depends entirely on filling the top of the funnel.

Two specific signals to watch:

- **Compare cohorts over time.** If newer cohorts retain worse than older ones, the product is degrading or you're acquiring lower-quality users (often by spending too aggressively on paid channels).
- **Compare cohorts by source.** Organic users almost always retain better than paid. If paid retention is so weak that LTV doesn't cover CAC, you're buying losses.

---

## LTV / CAC Ratio

The fundamental unit economics check.

- **LTV** — total revenue from a user over their lifetime, minus variable costs to serve them.
- **CAC** — fully-loaded cost to acquire one user (including sales, marketing, onboarding, free-tier costs).

Rule of thumb: **LTV ≥ 3 × CAC** for a healthy SaaS. Below 3×, growth is buying revenue for less than it costs. CAC payback period (how many months until a customer pays back their acquisition cost) should be under 12–18 months in most software categories.

Common failure: optimizing CAC by channel without checking that the cheap-CAC channels produce comparable LTV. They almost never do.

---

## Viral Coefficient (K)

K = (invitations sent per user) × (conversion rate of invitations).

- **K > 1** = exponential viral growth. Rare, almost always temporary.
- **K = 0.3–1** = strong assisted growth. Each user brings a fraction of another, lengthening retention and lowering CAC.
- **K < 0.1** = nominal viral effect. Don't model it as a growth lever.

Most products have K << 1. That's fine. The point of measuring K is not to chase virality but to understand whether referral is contributing meaningfully or whether the team is investing in mechanisms that don't move the curve.

---

## Growth Accounting

Decompose net user growth into the underlying flows:

- **New** — first-time users this period
- **Resurrected** — previously-churned users who came back
- **Churned** — users who stopped this period
- **Net change** = New + Resurrected − Churned

A product can show "+5% MoM growth" while bleeding badly: 25% new, 22% churn, 2% resurrected. Headline growth obscures the leak. Growth accounting is the way to spot it.

This is also the right tool for diagnosing whether a product is "growing because it's growing" (compounding from a stable retained base) or "growing because we're spending more on acquisition" (treadmill).

---

## Bundle thinking (post-PMF)

In multi-product companies, a feature's success is rarely measured in isolation. A new product might pay for itself by deepening the bundle relationship — direct deposit, primary account, default integration — even if its standalone economics look weak.

Conversely, a feature with strong standalone metrics can destroy bundle value if it attracts users who only want that one feature, never expand, and never become the primary account holder. Free adoption, in this model, is sometimes negative-value adoption.

Always ask: **does this feature deepen the bundle, or hollow it out?**

---

## When this phase is done

You should be able to answer:

1. What does each AARRR stage look like, and where is the biggest leak?
2. What does cohort retention look like — flat or collapsing?
3. What's LTV / CAC by channel, and which channels are losing money?
4. Is growth coming from new acquisition, resurrection, or retention? What's the trend?

If retention is collapsing, do not invest in acquisition. Fix the leak first. Adding water to a bucket with a hole in the bottom is the most common — and most expensive — growth mistake.
