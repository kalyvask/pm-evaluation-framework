---
name: pm-progress-auditor
description: Audit a status update, exec review, board email, all-hands talking point, or dashboard callout for credibility leaks before sending. Flags claims that overstate ("shipped" when 5 users are in beta), cherry-picked windows ("+15% w/w" off a holiday), vanity metrics used as validation, attribution claims with obvious uncontrolled counterfactuals, and "on track" forecasts without a threshold. Use when a PM is about to communicate progress upward and wants every claim pressure-tested. Built on the principle that goodwill is a finite budget — every overclaim debits the account, and once drained the real wins stop being believed.
---

# PM progress auditor

Audits any artifact that communicates progress — status update, exec review slide, board email, all-hands line, dashboard headline — for credibility leaks. Most PMs don't lose credibility in one big lie; they lose it one small overclaim at a time. A metric framed too generously. A "shipped" that meant beta to five users. A "users love it" with twelve datapoints from one segment. A "we're on track" with no threshold. The audit's job is to catch each one before it goes up.

## When to use

Use this when:
- You're about to send a status update, exec review, or board note and want it pressure-tested
- You've drafted talking points for a leadership meeting and want the claims checked
- A teammate sent you a draft and asked "is this OK to send up?"
- You're locking the headline number on a dashboard leadership will see

Don't use this when:
- The user wants a *full* dashboard reviewed for strategic alignment — use [`pm-metrics-critic`](../pm-metrics-critic/SKILL.md)
- The user wants to *pick* a North Star — use [`pm-north-star-selector`](../pm-north-star-selector/SKILL.md)
- The user wants a launch readiness check — use [`pm-launch-reviewer`](../pm-launch-reviewer/SKILL.md)
- The artifact is internal team notes where overclaim cost is low — audit overhead isn't worth it

## The core principle: goodwill is a finite budget

Every claim a PM communicates upward debits or credits a credibility account.

- **Claims that hold under scrutiny credit it.** "Activation among the strategic segment is up 4pp, here's the cohort cut."
- **Claims that don't hold debit it.** "Engagement is up 15%" (in a week with a marketing push). "We shipped X" (beta to 5 users). "Users love it" (12 datapoints, one segment, no counter-evidence shown).
- **Vanity metrics used as validation debit hardest.** A vanity metric implicitly claims something it doesn't measure. When the audience figures that out, the cost compounds — not just this claim, but the next three.

The account is finite. When it's drained, the next time you bring up a *real* bet — even one with hard evidence — the audience discounts it. PMs who keep their account in the black get the yes on the hard asks. PMs who don't, don't.

The audit flags every claim that debits the account without being load-bearing.

## How to apply

1. **List every claim verbatim.** Pull every claim that asserts a fact about progress, status, or impact. Don't paraphrase — quote it. Include numbers, verbs ("shipped," "launched," "validated," "scaled"), and forecasts ("on track for Q3"). Subjective claims ("team is excited," "users love it") count too.

2. **For each claim, run the six honesty checks.** Mark 🟢 / 🟡 / 🔴.

   - **Metric honesty.** Does the metric actually measure what the claim asserts? "Engagement is up" — what's engagement here? Sessions? Actions per session? Time? If it's a proxy, is the claim narrow enough to match the proxy?
   - **Window honesty.** Is the time window honestly chosen, or cherry-picked? "+15% week-over-week" when the prior week was a holiday is a cherry pick. The honest framing is the 4-week trend.
   - **Verb honesty.** "Shipped" should mean GA, or at least general availability to the named segment. "Launched" should mean external. "Validated" should mean the assumption was falsifiable and survived — not "we got some good feedback." If the verb is stronger than the underlying state, downgrade it.
   - **Segment honesty.** "Users love it" — which users, how many, what was the comparison? If the evidence is a few datapoints from one segment, the claim has to name them.
   - **Counterfactual honesty.** "The launch drove +X" — what was the obvious counterfactual? Marketing push, seasonality, competitor outage, price change. If those aren't ruled out, the attribution is overclaimed.
   - **Forecast honesty.** "On track for Q3" — on track to what threshold? If the threshold isn't named, "on track" is hand-waving. The honest version names the threshold and the current pace.

3. **Score the artifact's net credibility impact.** For each claim, mark: credit, neutral, or debit. Total it. An artifact with three debits and two credits is a net loss — even if every claim is technically defensible, the cumulative impression burns goodwill.

4. **Rewrite the debits.** For every 🔴, write the honest version. Most claims don't need to be removed — just sharpened. "Engagement up 15%" → "Sessions per active user up 4% on the 4-week average; last week was +15% but included a marketing push, so I'm using the 4-week."

5. **Flag what's missing.** Sometimes the credibility leak is what's *not* in the artifact: the metric that went down, the segment that didn't move, the assumption that didn't hold. Ask: what would the smart skeptic in the room ask, and is it answered here? Reference `decision-making/metrics.md` § "When the metrics are lying" — guardrail and counter-metric absence is a credibility leak too.

6. **Recommend send / hold-and-rewrite / kill-and-restart.** If the rewrites are small, send. If the artifact materially overclaims, hold it. If the underlying state doesn't support an upward update at all, kill the artifact and tell the real story instead — a clear "we hit X, didn't hit Y, here's what we're doing about it" credits the account in a way a dressed-up update never can.

## Output structure

```
## Net credibility verdict
[Credit / neutral / debit. One sentence on why.]

## Claim-by-claim audit
| Claim (quoted) | Metric | Window | Verb | Segment | Counter | Forecast | Verdict |
|---|---|---|---|---|---|---|---|
| "[claim 1]" | 🟢/🟡/🔴 | ... | ... | ... | ... | ... | credit / neutral / **debit** |
| "[claim 2]" | ... | ... | ... | ... | ... | ... | ... |

## Debits — rewrite these
1. **Original:** "[overclaim]"
   **Honest version:** "[narrower claim that still says something]"
   **Why it leaked:** [Which honesty check failed and what the sharp reader would ask.]
2. ...

## Missing
- [What a sharp reader would ask that the artifact doesn't address — the metric that went down, the segment that didn't move, the unvalidated assumption.]
- ...

## Recommendation
Send / hold-and-rewrite / kill-and-restart. One sentence on why.
```

## What good looks like

- Honest rewrites are *narrower*, not weaker. "Engagement up 15%" → "Sessions per active user up 4% on the 4-week average" — narrower but more defensible. Narrower beats louder.
- Verbs match underlying state. "Shipped" only if it actually shipped. "Validated" only if the assumption was falsifiable and survived.
- Every numeric claim has a window. "+15%" without a window is hand-waving.
- Every subjective claim ("users love it," "team is excited") either gets backed by datapoints or comes out. Subjective claims don't credit credibility; they only debit.
- The audit names what's *missing*, not just what's wrong. The credibility leak from an absent metric (the one that went down) is often bigger than the leak from a present one that's slightly overstated.

## Anti-patterns

- **Auditing only the numbers, not the verbs.** "Engagement is up 15%" gets checked. "We've validated the hypothesis" does not. The verbs leak more credibility than the numbers, because they're harder to verify and easier to misuse.
- **Letting "directionally positive" pass.** It's a hand-wave. If the direction matters, name the magnitude and the window. If neither is presentable, the claim shouldn't be there.
- **Cherry-picking the window without flagging it.** "Up 25% week-over-week" with no 4-week context is a flag, not a fact.
- **Approving an artifact because no individual claim is wrong.** Three small overclaims in one artifact cost more than one big one — they signal a pattern. Audit the cumulative impression, not just each claim in isolation.
- **Forgetting the audience compounds.** A claim that survives this week's review will be remembered next quarter when the underlying number doesn't hold. Credibility loss is delayed; you pay it later, often on a bet that matters more.
- **Treating the audit as adversarial to the team.** It isn't. The audit protects the PM's ability to *get a yes on the next hard ask*. A team with a clean account gets resources; a team with a drained one gets second-guessed.

## Chain with pm-red-team

Once the audit is done and the debits are rewritten, run the artifact through [`pm-red-team`](../pm-red-team/SKILL.md) and ask: which of these claims will not survive a sharp question in the room? The red team plays the skeptic. If a rewritten claim still doesn't hold, narrow it again. The North Star, the dashboard, and the status update are all high-leverage communication artifacts — an adversarial second pass before lock-in is cheap.
