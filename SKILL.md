---
name: stop-slop
description: Comprehensive anti-slop standard for autonomous coding agents (agy, Claude Code, Cursor, Codex, Cline, Pi). Eliminates AI writing tells, visual/UI artifact clutter, and superficial code stubs.
metadata:
  trigger: Writing prose, creating or editing UI artifacts, dashboards, slides, writing code, refactoring, or reviewing outputs
  author: Ken Huang (https://github.com/kenhuangus/stop-slop), based on work by Hardik Pandya and Ruben Hassid
---

# Stop Slop

A universal anti-slop standard for coding agents and language models. Eliminates predictable AI patterns across three domains:
1. **Prose and Documentation**: Throat-clearing, filler phrases, structural clichés, passive voice, empty intensifiers, and metaphors/analogies.
2. **Visual Artifacts and User Interfaces**: Cluttered layouts, fake buttons, emoji badges, unanchored metrics, and walls of text.
3. **Source Code and Engineering**: Syntax-restating comments, placeholder stubs, fake mock objects in production paths, and unnecessary boilerplate.

## Operational Workflow

Apply the core rules directly. They are self-contained and resolve most outputs without loading external files. Load references only when addressing specific or complex tasks:

* **Prose work**: Consult [references/phrases.md](references/phrases.md) and [references/structures.md](references/structures.md). For vocabulary audits, use [references/slop-words.md](references/slop-words.md).
* **Artifact and UI generation**: Consult [references/artifacts.md](references/artifacts.md) and review clean templates in [examples/](examples/).
* **Code generation and refactoring**: Consult [references/code.md](references/code.md).
* **Before/After comparisons**: Review [references/examples.md](references/examples.md).

---

## Domain 1: Prose Anti-Slop Standards

1. **Cut throat-clearing and filler phrases.** State the point immediately. Delete openers like "Here's the thing", "In today's fast-paced world", "It turns out that", "Let's dive in", and "At its core". Remove all adverbs.
2. **Eliminate structural clichés.** Avoid artificial binary contrasts ("Not X, but Y", "The issue isn't X, it's Y"), negative listings ("Not this, not that, but Z"), and dramatic sentence fragmentation. State assertions directly.
3. **Enforce active voice and human agency.** Unless it is absolutely necessary and makes sense, write only active sentences and zero passive sentences. Ensure every action has an explicit actor. Inanimate concepts or objects must not perform human actions ("the policy encourages" -> "the leadership requires"). Put the actor at the front of the sentence.
4. **Demand concrete facts.** Replace vague generalizations ("The results were significant") with exact metrics and scope. Ban Tier 1 slop words (delve, elevate, streamline, seamless, robust, holistic, paradigm, flywheel). Anchor claims to numbers or verified sources.
5. **Vary rhythm and ban connecting dashes.** Do not join clauses using em-dashes, en-dashes, or hyphens standing in for dashes. Separate into two distinct sentences or use a comma. Preserve true compound words (e.g., self-contained). Vary consecutive sentence lengths.
6. **Eliminate decorative horizontal rules.** Never insert markdown horizontal dividers (`---`) between standard sections. Headings and white space define section boundaries.
7. **Zero metaphors and zero direct analogies.** No metaphor or direct analogy should be used in any sentence. Avoid figurative comparisons, explanatory analogies ("think of X as Y", "like a waiter in a restaurant"), physical metaphors ("building bridges", "navigating landscapes", "uncharted waters", "the glue holding systems together"), and anthropomorphic clichés ("treating servers like cattle"). State technical mechanisms, operational relationships, and facts literally and directly.

---

## Domain 2: Visual Artifact and UI Standards

1. **Visual elements carry data, not decoration.** Present metrics, comparisons, and workflows as structured data tables, bar charts, or metric tiles with explicit units and baselines. Never use mock browser windows, bars without numbers, or decorative non-functional buttons.
2. **Match layout form to the specific job.** Never use a generic dashboard for every request:
   * *Decide (Memo/Brief)*: Top ask and deadline; side-by-side option cards with recommendation highlighted; comparative risk table.
   * *Catch Up (Report)*: 3-4 primary metric tiles with period-over-period deltas; exactly one trend chart; action cards.
   * *Monitor (Dashboard)*: Metric tiles on top; categorized cards; standardized status pills.
   * *Learn/Execute (Guide)*: Sequential progression path on top; one step per view with Next/Back controls; concrete requirements.
   * *Present (Slides)*: Single thesis per slide; one large visual paired with one direct sentence.
   * *Calculate (Tool)*: Inputs on left, calculated output on right; working default data on load.
   * *Reference (Cheat Sheet)*: Topic cards with bold keywords and concise rules; live search filter.
3. **Top metadata and standalone first screen.** Begin with a concise metadata header (under 15 words) specifying document type, author, recipient, date, and core request. The initial view (50 to 120 words) must communicate the conclusion, rationale, and next steps before scrolling.
4. **Enforce strict density limits.**
   * Maximum 4 sections below the primary screen.
   * Maximum 5 items per card or list.
   * Maximum 1 comprehensive table per view.
   * Paragraphs under 2 sentences; table cells under 10 words.
5. **Clean palette and robust typography.** Use neutral high-contrast surfaces (`#ffffff` / `#151515`), system typography, and reserve semantic color exclusively for state: green for positive, red for negative, amber for warning. Disallow emoji badges (🚀, ✨, 🔥, 💰). Ensure zero layout clipping across 1440px and 400px viewports.

---

## Domain 3: Code and Engineering Standards

1. **Decision-focused comments.** Write comments that explain *why* an implementation decision exists (e.g., business invariants, concurrency constraints, protocol quirks). Never write comments that merely restate syntax (e.g., `# loop over items`).
2. **Complete, runnable implementations.** Never generate placeholder stubs (`// TODO: implement later`), synthetic mocks in production paths, or truncated outputs (`// ... rest of code unchanged`). If dependencies or credentials are required, document configuration parameters and handle missing prerequisites with explicit, loud errors.
3. **Direct architecture.** Avoid premature generalization, unnecessary factory patterns, and excessive abstraction layers for single-use routines. Prefer standard libraries and verified APIs.
4. **Verified execution.** Never claim tests, builds, or deployments succeed unless verified in the execution environment. Maintain security boundaries and sanctioned API paths.

---

## Quick Quality Checks

Before delivering output, verify these checkpoints:

### Prose Checks
- [ ] Are all throat-clearing openers and adverbs deleted?
- [ ] Are all binary contrasts ("Not X, but Y") restructured into direct assertions?
- [ ] Are sentences strictly in active voice, with passive sentences completely avoided unless absolutely necessary and justified?
- [ ] Are all connecting em-dashes and markdown horizontal rules removed?
- [ ] Are all vague intensifiers (robust, seamless, comprehensive) replaced with concrete numbers?
- [ ] Is every sentence completely free of metaphors, similes, and direct analogies?

### Artifact and UI Checks
- [ ] Does the visual layout match the reader's functional job?
- [ ] Does the initial screen state the takeaway and required action without scrolling?
- [ ] Are all metrics anchored to explicit comparative baselines (e.g., "+$1,043 vs September")?
- [ ] Are all decorative emojis, gradient buttons, and non-functional visual elements removed?
- [ ] Does the layout remain intact and readable at both 1440px and 400px widths?

### Code Checks
- [ ] Do comments document architectural decisions rather than restating obvious syntax?
- [ ] Is all requested code fully written without `TODO` stubs or fake mocked responses?
- [ ] Are error handling and boundary conditions explicitly addressed?
- [ ] Has code functionality been verified through execution or targeted testing?

---

## Anti-Slop Evaluation Scoring

Score drafts across five dimensions (1 to 10 points each):

| Dimension | Evaluation Criteria |
|---|---|
| **Directness** | Are statements delivered immediately without preamble or rhetorical scaffolding? |
| **Substance** | Are claims supported by concrete figures, verified data, and functional code? |
| **Structure** | Does the layout or organization directly serve the reader's operational objective? |
| **Authenticity** | Does the language and interface read like natural technical communication without AI cliches? |
| **Density** | Has all redundant commentary, decorative styling, and filler been removed? |

**Threshold**: Any output scoring below 40/50 must be revised before delivery.
