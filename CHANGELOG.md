# Changelog

Notable additions to this repo, newest first. Loosely follows the [Keep a Changelog](https://keepachangelog.com) format.

## 2026-08-13

### Added

- **`decision-making/agentic-product-design.md`** — new doc covering the design discipline for products that *act* rather than suggest. Why the deterministic-design assumption breaks, designing the constraint system instead of the screens, deciding the agent's persona before its scope, the inversion of the model-invisibility rule into explicit human-vs-agent attribution, calibrating transparency to who is accountable for the output, the three properties of visible failure (easy to see / fix / forgive), four trust mechanisms (inherited permissions, produce-vs-publish gate, stakes-based routing, autonomy earned on a measured override rate with deliberate over-gating at launch), familiar patterns, why the interface still matters (valued friction; chat as session log and guardrail rather than primary interaction; approvals next to the object they change), shipping to learn from real usage, and a 13-item agentic design checklist. Sourced from Figma's *Writing the rules of agentic design* (Expedia, Accor, Google, Capital One, Superhuman, Atlassian practice).
- **`decision-making/ai-integration.md`** — scope note distinguishing produce-then-user-acts AI from agentic AI, an inversion clause on Rule 4 (make the model invisible), an extension of the shape question for agents, and checklist item 10 routing agentic products to the new doc.
- **`.claude/skills/pm-design-critic/SKILL.md`** — new step 3b, an agentic checklist (attribution, transparency calibration, failure visibility, produce-vs-publish, permissions, stakes routing, constraint spec, approval placement, valued friction) that runs when the design has AI taking actions rather than making suggestions.
- **`.claude/skills/pm-framework-selector/SKILL.md`** — routing row for agentic product design questions.

## 2026-08-13 (later)

### Added

- **`decision-making/agentic-product-design.md`** — new "How many agents does the user see?" section on whether internal multi-agent topology should surface to the user. Internal decomposition is an engineering and governance decision; the user should still get one conversation and one resolution. Reconciles this with the attribution rule (attribute by system, not by internal boundary) and with named persistent agents. Checklist gains a topology-leakage item (now 14).

## 2026-06-02

### Added

- **`decision-making/first-principles-thinking.md`** — new framework doc. Five sections covering the narrow right use of first-principles reasoning (three regimes that justify it; default to the pattern otherwise), innovating on one or two axes (borrow the rest), the four hidden costs of throwing out an established pattern, combining first-principles with calling people who've solved the adjacent problem, and a decision checklist.
- README "How to use this repo" table restructured by lifecycle phase (Frame & Decide / Discover & Validate / Build & Ship / Measure & Grow / Cross-functional / AI and the PM / PM craft and career / Rubrics, review, and operate).
- README "Reading paths" section consolidating the existing PMF path with two new paths: "If you're a working PM at a fast-growing company" and "If you're prepping for AI PM interviews."
- CHANGELOG.md (this file).

## 2026-05-30

### Added

- **`decision-making/activation.md`** — new "Day-1 / day-10 / day-30 sticky-moment tension" section. The sequencing problem most teams under-handle: day-1 features have to keep users alive long enough to discover the day-10 features that trigger word of mouth.
- **`decision-making/research-methods.md`** — two new sections: "Right-sizing exploration to stakes" (calibration table 3 vs 30 vs 300 users by stakes and reversibility) and "Map the full journey, not just your surface" (upstream/downstream questions).
- **`what-makes-a-good-pm.md`** — new "Career craft" section. Six sub-sections covering the graduated-ask networking pattern, the back-channel effect, breaking in via wedges and side doors, three interview signals (communication / agency / authentic enthusiasm), company-over-title for early career, earn-the-right-then-ask for internal moves.

## 2026-05-29

### Added

- **`decision-making/ai-craft-for-pms.md`** — new doc on how a working PM personally uses AI. Production-vs-thinking gap, eight prompt principles, anti-patterns table, AI/human decision matrix, hallucination types, four verification practices.
- **`templates/pm-prompt-library.md`** — new template with reusable prompts for common PM artifacts: discovery interview prep, transcript synthesis, PRD section-by-section, Amazon-style PR/FAQ working-backwards exercise, competitive monitoring setup and weekly synthesis.

## 2026-05-28

### Added

- **`decision-making/finding-pmf.md`** — new posture doc on finding product-market fit. Execution-doesn't-matter as the load-bearing claim, right-and-non-consensus, leap of faith vs. value hypothesis, need vs. desperation, iterate on the who not the what, savor the surprise, built to learn vs. built to execute, canonical distractions list.
- **`.claude/skills/pm-pmf-coach/SKILL.md`** — new skill. Walks a founder or early-stage PM through finding PMF on a specific bet, end-to-end: surface leap of faith → build value hypothesis → design smallest falsifying experiment → interpret result → decide pivot/restart/savor → distractions check.
- README "If you're finding PMF" reading-path section.

## 2026-05-27

### Added

- **`frameworks/06-product-process-for-pmf.md`** — new framework. The head-of-product decision framework. Eight-step spine, ten-principle counterintuitive doctrine, build-to-learn vs. build-to-execute culture, financing milestones mapped to PMF stages, decision checklist. Each step later expanded with why-of-each-step and skip-cost explanations.

## 2026-05-26

### Added

- **`ai-and-pm.md`** — two new sections: "Evals replace the PRD for model work" and "When to ship before the model is ready" (five-question framework).
- **`what-makes-a-good-pm.md`** — new pattern #8: "They stay personally close to the raw user signal." Existing AI-prototype pattern renumbered to #9.

## 2026-05-25

### Added

- **`decision-making/positioning-and-value-prop.md`** — new doc. The first-ten-touches alignment principle, the drop-in-but-worse reframe trap, killer demo as positioning North Star, three signals of broken positioning.
- **`pm-design-critic` SKILL.md** — new anti-pattern: "Missing the org pattern" for surfaces that look like the visible compromise between competing internal teams.
- **`frameworks/02-defining-the-mvp.md`** — added "Hack track vs. polished track for developer products."
- **`decision-making/prioritization.md`** — added "When user-demand ranking is wrong" section (override-axis sequencing: diagnose the bleed, map features to axes, apply three cross-cutting filters, sequence with parallelism).
