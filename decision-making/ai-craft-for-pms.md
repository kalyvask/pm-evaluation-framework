# AI craft for working PMs

How a working PM actually uses AI in their day-to-day work. Distinct from [`../ai-and-pm.md`](../ai-and-pm.md) (which is about how AI is changing what PMs are hired for) and [`ai-integration.md`](ai-integration.md) (which is about designing AI surfaces in products). This file is about the PM's own AI use as part of their craft.

The current state, per Lenny Rachitsky's 2024 survey of ~1,750 PMs: 63% report saving 4+ hours per week with AI; 70%+ report better work quality. But the use cases are concentrated in *production* tasks (writing PRDs ~22%, mockups ~20%, internal communication ~19%) while *thinking* tasks lag far behind (user research ~5%, roadmap ideation ~1%). The same survey shows demand for AI on the thinking tasks is roughly 6x current use. The implication: most PMs are using AI to write the things they already know how to write, not to think the things they don't already know how to think.

The point of this file is to close that gap. The craft below is calibrated for strategic and discovery work, not just production.

---

## The production-vs-thinking gap

The default failure mode of AI in PM hands: it accelerates the writing of artifacts the PM already had clearly in their head. A PRD they could have written in three hours now takes one. That's real time saved. It is not the high-leverage use of AI.

The high-leverage uses sit upstream of the artifact:

- Stress-testing the problem framing before the PRD
- Synthesizing interview transcripts to find the unexpected pattern
- Exploring a strategic move by simulating the competitive response and the failure modes
- Drafting the kill criterion the team has been hedging on
- Pressure-testing a value hypothesis before the build cycle

These uses are harder because they require the PM to ask a question they don't already know the answer to. The reward is judgment that compounds, not output that piles up.

The discipline: before reaching for AI to write something, ask whether AI could be helping you *decide* something instead. If the answer is yes and you reach for the writing use case anyway, you're trading away the high-leverage use for the easy one.

---

## Eight principles for prompts that produce judgment, not just output

The principles below apply to any AI tool used as part of a PM workflow.

1. **Context before request.** The more context you give the model, the less it has to guess. Guessing produces generic output. Useful context: who you are, what you're trying to decide, what you've already tried, what's at stake. As a rule of thumb, the first half of the prompt should be context; the second half is the ask.

2. **Specify the output structure.** "Give me a strategy" produces a wall of text. "Give me a strategy as: 1) one-sentence thesis, 2) three load-bearing assumptions, 3) the falsifying test for each, 4) the kill criterion" produces a usable artifact. The structure is a forcing function on both the model and on you.

3. **Prime the role.** "Act as an industry analyst who spent six months on this category, writing for an exec audience that already knows the basics" primes the model to adopt expertise and skip introductory paragraphs. The role should be specific. "Act as a PM" is weak; "Act as a PM at a B2B SaaS who's optimizing checkout conversion under regulatory constraints" is calibrated.

4. **Iterate, don't one-shot.** Generate a draft, critique it (often by asking the model to red-team its own output), revise, polish. The first output is rarely the best. Three rounds is typical for anything load-bearing. Treating AI as a one-shot oracle leaves most of its value on the table.

5. **Chunk by section.** Don't ask for the whole artifact at once. Ask for one section, refine it, then move on. Section-by-section produces consistently better output and lets you correct course before drift compounds. Particularly important for PRDs, strategy memos, and any structured artifact.

6. **Attach the real source.** Transcripts, customer quotes, internal docs, raw data. Whenever possible, attach the actual source rather than describing it. Attached source prevents hallucination because the model can ground its output in real text instead of inventing plausible-sounding facts.

7. **Add verification instructions.** Tell the model what to do when uncertain. "If you're not sure, say so explicitly." "Mark inferences vs. facts." "List the questions I haven't asked that would change your answer." These instructions move the model from confident-and-wrong to honest-and-useful.

8. **Specify format and length.** "Bullets for insights, table for comparison, verbatim quotes in blockquotes, under 400 words" gets you what you can paste into the next artifact. "Write a comprehensive analysis" gets you a wall of text you have to re-structure.

---

## Anti-patterns

The five common failure modes when PMs use AI:

| Anti-pattern | What it produces | The fix |
|---|---|---|
| **Vague questions.** "What should I know about AI?" | Generic answer that adds nothing | Add context: "I'm a senior PM at a B2B SaaS, weighing whether to invest engineering capacity in adding AI to our existing analytics product. Help me think through the trade-off." |
| **Asking AI to predict.** "Will X be big in five years?" | Hallucinated forecast presented as analysis | Reframe: "Based on current trends, what factors would need to be true for X to be meaningful in five years, and how would I monitor each one?" |
| **Treating output as final.** Paste, send, done. | Public artifacts with errors, hedged claims, generic phrasing | Always review and edit. For external use, run an adversarial pass (`pm-red-team`) and a credibility audit (`pm-progress-auditor`). |
| **No verification.** "The AI said the market is $X." | Misleading inputs into real decisions | Ask for sources. Cross-check with a research-focused tool. If the claim is load-bearing, verify with a domain expert. |
| **Wrong tool for the job.** Using AI for things it can't do well. | Confident-wrong output on tasks AI is structurally bad at | AI is weak at: predicting specific futures, accessing proprietary data, replacing domain expertise on novel categories. Don't ask it to. |

---

## AI-vs-human decision matrix

Not every decision should be made by AI even when AI can. The matrix:

| AI should decide | Humans must decide |
|---|---|
| Formatting and structure of an artifact | Strategic direction |
| First drafts of any prose | Anything involving people's livelihoods (hiring, firing, performance) |
| Routine analysis patterns (cohort cuts, simple comparisons) | Final approval on external comms (board updates, investor decks, customer-facing posts) |
| Summarization of long inputs | Ethical gray areas |
| Tone and style adjustments | Kill / continue decisions on major bets |
| Format conversion (transcript to action items, table to bullets) | Decisions where the cost of being wrong is unrecoverable |

The principle: AI handles the work where being wrong is cheap and recoverable. Humans handle the work where being wrong is costly or irreversible.

---

## Hallucination types and verification

AI confidently hallucinates. The four common types:

1. **Citations that don't exist.** The model produces a credible-looking source that isn't real, or attributes a quote to the wrong author.
2. **Plausible but wrong facts.** A market-size number, a company history detail, an academic finding. Sounds right; isn't.
3. **Outdated information.** The model's training data ends before a recent event the user cares about.
4. **Logical-sounding nonsense.** A chain of reasoning that sounds internally consistent but rests on a false premise the model never flagged.

The four verification practices:

- **Triangulation.** Ask the same question of two different models and look for divergence. Divergence flags uncertainty the original model didn't surface.
- **Source checking.** Click the citation. Read the source. If the model didn't provide a source, ask for one. If it can't provide one, lower the confidence on the claim.
- **Domain expert review.** For high-stakes claims, ask a human who knows the space. Especially for novel or specialized categories where the model's training data is sparse.
- **Consistency testing.** Ask the same question three different ways. If the answers contradict each other, the model doesn't actually know.

The discipline: verify any claim that, if wrong, would move a real decision. Skip verification only for low-stakes output where the cost of being wrong is cheap.

---

## When this file applies

Use this file when:

- You're about to use AI for a strategic or discovery task and want to do it well
- You're drafting prompts and want them to produce judgment-grade output, not just generic text
- You're reviewing an AI-generated artifact for credibility before circulating it
- A teammate is using AI in a way that produces shallow output and you want a shared reference

Don't use this file when:

- The question is about *designing AI into a product* — that's [`ai-integration.md`](ai-integration.md)
- The question is about how the PM role itself is changing — that's [`../ai-and-pm.md`](../ai-and-pm.md)
- You want concrete reusable prompts for specific PM artifacts — that's [`../templates/pm-prompt-library.md`](../templates/pm-prompt-library.md)
