# Positioning and value-prop alignment

Most positioning failures aren't marketing problems. They are product problems with marketing symptoms — the marketing landing page, the sales deck, the API docs first page, and the in-product onboarding are all hitting different value points, so the customer never lands on the one thing the product is actually good at.

This file is the working-PM reference for keeping the value proposition aligned across the customer's first ten touches with the product.

---

## The first ten touches must align on one value point

When a customer first encounters a product, they hit several surfaces in rapid succession: a landing page, a demo, a sales call, an API doc, a getting-started guide, the first screen after signup. If those surfaces hit different value points (cost, speed, accuracy, integration depth, ease of use), the customer absorbs none of them.

Common misalignment pattern:

- **Marketing** has been convinced by the latest investor feedback that the value prop is "10x faster"
- **Sales** is selling on "100x cheaper" because that's what wins deals
- **API docs first page** lead with "drop-in replacement"
- **In-product onboarding** highlights "agentic compatibility"

Each is true. None of them lands. The customer walks away unsure what the product is for.

The discipline: once the team picks the load-bearing value point, *every* touch in the first ten has to repeat it. Not adjacent points. The same one.

**Evaluation question:** for the load-bearing value point, can you point to its visible expression on the landing page, the sales deck, the API docs first page, the demo, and the first in-product screen? If any of the five is missing or off-message, the alignment is broken — and that's a product problem to fix internally before any additional marketing investment pays off.

---

## The drop-in-but-worse reframe trap

If your product is a drop-in replacement for an existing solution and it's even slightly worse on the existing metric, every one-to-one comparison kills the deal. The buyer thinks: *the boss is asking me to switch to something cheaper but worse. I can't take that risk.*

The fix is not to make the product less-worse on the existing metric. The fix is to reframe the conversation to a dimension where you win.

Example (paraphrasing a real case): a search infrastructure startup is 100x cheaper and 10x faster than incumbents, but a touch worse on accuracy. Every accuracy-on-the-same-query comparison kills the deal. The reframe: stop comparing one-to-one. Compare what the customer can newly do with the cost and speed budget — run 50 searches instead of 1, get 5x the accuracy through ensembling, build agentic loops that weren't economically possible before.

The reframe is a product positioning move, not a marketing trick. It has to show up in the demo (the customer sees the new use case running, not a one-to-one bake-off), the API docs (the first example shows the new pattern), and the sales motion (the discovery question is "what would you do with 100x the search budget" instead of "are you happy with your current search").

**Evaluation question:** is the product being sold as a better X, or as a path to a Y the customer didn't have before? If it's "better X" and the underlying metric isn't actually better, the positioning is broken.

---

## Killer demo as positioning North Star

Work backwards from the moment a customer says *"I want that."*

The killer demo is the single experience that makes someone reach for their wallet, or at least open the doc and start trying. It's not the full product. It's the one moment that compresses the whole value prop into something the customer can feel.

Two rules:

- **The killer demo must be experienceable live in the product**, not just in the sales deck. If the customer signs up to try and can't get to the killer demo in the first session, the positioning has a delivery gap.
- **Every product decision should be testable against the killer demo.** "Does this change make the killer demo more impressive, less impressive, or the same?" If the answer is "less," the change is suspect.

The killer demo is also the right anchor for roadmap conversations. When the team is debating priorities, the question "which of these gets us closer to the killer demo being unmissable?" cuts through more politics than RICE or MoSCoW.

**Evaluation question:** can the team name the one moment in the product that makes a first-time user go *"I want that"*? Is that moment live in the product today, or only in the deck? If only in the deck, that's the first roadmap item.

---

## The three signals of broken positioning

Quick diagnostic. If two of these are true, the positioning needs work before more growth investment:

1. Sales motion and marketing landing page lead on different value points.
2. The team can't name the killer demo in one sentence.
3. Customers consistently describe the product to other customers in different language than the team uses internally.

Each one signals that the work isn't a marketing campaign — it's an internal alignment pass on what the product is actually for.
