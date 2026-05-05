# PM Evaluation Framework

A working library of frameworks, rubrics, and Claude skills for thinking like a Product Manager.

The material is organized around one question: **what does a good PM actually do, and how do we know?**

It pulls together decision frameworks, evaluation rubrics, and reusable templates that hold up under cold-call pressure on hard product decisions: when to kill a feature, how to read user research that contradicts your strategy, what "MVP" really means, how to run a launch when failure is likely.

---

## How to use this repo

| If you want to... | Start here |
|---|---|
| Pick the right framework for the decision in front of you | [`frameworks/00-overview.md`](frameworks/00-overview.md) |
| Sharpen how you frame a problem before jumping to solutions | [`decision-making/problem-framing.md`](decision-making/problem-framing.md) |
| Think clearly about reversibility before committing | [`decision-making/risk-and-reversibility.md`](decision-making/risk-and-reversibility.md) |
| Decide between user research methods (personas vs. JTBD vs. Kano) | [`decision-making/research-methods.md`](decision-making/research-methods.md) |
| Prioritize a backlog | [`decision-making/prioritization.md`](decision-making/prioritization.md) |
| Define what to measure | [`decision-making/metrics.md`](decision-making/metrics.md) |
| Work better with engineering | [`cross-functional/engineering-partnership.md`](cross-functional/engineering-partnership.md) |
| Run a launch where some failure is expected | [`cross-functional/failure-management.md`](cross-functional/failure-management.md) |
| Understand how AI is changing the PM role | [`ai-and-pm.md`](ai-and-pm.md) |
| See recurring product-decision patterns (anonymized) | [`case-patterns/`](case-patterns/) |
| Evaluate a PM's reasoning on a case | [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md) |
| Evaluate a strategy memo before it goes up the chain | [`rubrics/strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md) |
| Show up well in a product / exec review | [`rubrics/product-review-rubric.md`](rubrics/product-review-rubric.md) |
| Use a PRD / decision-memo / postmortem template | [`templates/`](templates/) |

---

## Claude skills

The repo ships with four [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills) under `.claude/skills/`. They use the frameworks in this repo as their substrate.

| Skill | What it does |
|---|---|
| [`pm-framework-selector`](.claude/skills/pm-framework-selector/SKILL.md) | Given a decision context, recommends which framework(s) to apply and why |
| [`pm-decision-coach`](.claude/skills/pm-decision-coach/SKILL.md) | Walks you through any product decision using the framing → research → prioritization → risk loop |
| [`pm-evaluator`](.claude/skills/pm-evaluator/SKILL.md) | Grades a PM's written analysis or recommendation against the evaluation rubric |
| [`pm-case-discussion`](.claude/skills/pm-case-discussion/SKILL.md) | Runs a cold-call style case discussion: asks you the hard questions, pushes back, and surfaces what you missed |

To use them locally, drop the repo in a directory Claude Code can see — the skills will appear automatically.

---

## The five evaluation criteria

Every framework in this repo ladders up to five questions that travel with you across any product decision:

1. **Did you identify the right problem before jumping to solutions?**
2. **Did you apply a framework to remove bias and surface stakeholder perspectives?**
3. **Did you account for bundle effects and the full user journey** — including procurement, admin, and downstream teams?
4. **Did you define what success and failure look like upfront?**
5. **Did you prototype or validate before committing real resources?**

The full rubric is in [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md).

---

## License

MIT. Use it, fork it, ship better products.
