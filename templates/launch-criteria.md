# Launch criteria template

A one-page artifact for cross-functional launches. Resolves the most common dispute: *what does "ready to launch" actually mean, and who decides?*

The pattern: decompose readiness into separate gates with separate owners, with measurable criteria for each. Require all gates to be green before launch.

---

## Product / launch name

[What we're launching, in one line.]

## Target launch date

[Date]

## Launch type

- [ ] Soft launch / closed beta — small named cohort
- [ ] Limited GA — broader rollout, named segment(s) only
- [ ] Full GA — generally available

---

## Gate 1: Technical readiness

**Owner:** [Engineering lead, named]

**Criteria:**

- [ ] Stability — error rate below [threshold] over [time window]
- [ ] Scale — load-tested at [N×] expected peak
- [ ] Supportability — runbooks documented, on-call rotation in place
- [ ] Rollback — rollback procedure tested, [time-to-rollback estimate]
- [ ] Monitoring — production alerts configured for [specific signals]
- [ ] Security review — [completed / in progress / not required], by [team]
- [ ] Data — backups, retention, deletion policies in place

## Gate 2: Product readiness

**Owner:** [PM, named]

**Criteria:**

- [ ] Activation flow — % of test users hitting *aha* moment ≥ [target]
- [ ] Time to value — median [target time]
- [ ] Must-have features — all in place, tested
- [ ] Onboarding — UX tested with [n] users from target segment
- [ ] Documentation — user-facing help center pages live for top [n] use cases
- [ ] Pricing — final pricing in place; billing system updated
- [ ] Out-of-scope features — explicit list, communicated

## Gate 3: GTM readiness

**Owner:** [GTM / Marketing / Sales lead, named]

**Criteria:**

- [ ] ICP defined — specifically, not "SMB" / "enterprise"
- [ ] Sales enablement — [n] reps trained, demo certified
- [ ] Sales-rep economics — commission / SPIF structure in place if needed
- [ ] Marketing — launch materials ready, channels lined up
- [ ] Partner enablement — partners notified, partner training complete (if applicable)
- [ ] Customer success — playbook in place for first [n] customers
- [ ] Support — support team trained, escalation paths defined

## Gate 4: Quality readiness

**Owner:** [QA / Product, shared]

**Criteria:**

- [ ] Internal dogfooding — used by [n] internal teams for [time window]
- [ ] External pilot / lighthouse — [n] external customers in active use
- [ ] Quality bar — [specific outcome metric for the customer experience]
- [ ] Accessibility — [specific accessibility requirements met]
- [ ] Internationalization — [scope of language / region support]

## Gate 5: Risk and contingency

**Owner:** [PM, with cross-functional input]

**Criteria:**

- [ ] Pre-mortem completed — major risks named, owners assigned
- [ ] Rollback plan — what we do if the launch goes badly, who decides
- [ ] Comms plan — what we say to customers if there's a problem
- [ ] Kill criteria — pre-committed metric thresholds that would force us to halt or roll back
- [ ] Legal / compliance — [completed / in progress / not required], by [team]

---

## Sign-offs

Each gate owner signs off when their gate is green. Launch happens only when all gates have signed off.

| Gate | Owner | Status | Sign-off date |
|---|---|---|---|
| 1. Technical | [Name] | ☐ | |
| 2. Product | [Name] | ☐ | |
| 3. GTM | [Name] | ☐ | |
| 4. Quality | [Name] | ☐ | |
| 5. Risk | [Name] | ☐ | |

## Open issues

Things that aren't yet green. For each:
- The issue
- The owner
- The expected resolution date
- Whether this is a launch-blocker or a fast-follow

---

## How to use

Write this *before* the launch is in sight, not after. The act of writing forces the team to make readiness criteria explicit, which surfaces disagreements early.

Update it weekly during the run-up to launch. The status changes provide a real-time picture of how launch-ready the product actually is — usually more honest than verbal status updates in standup.

If a gate is *not* green at the planned launch date, the launch slips. The criteria do the work of saying no, so the PM doesn't have to.
