# Stop Slop

A universal anti-slop standard for autonomous coding agents and language models (Google Antigravity, Anthropic Claude Code, OpenAI Codex, Cursor, Cline, Roo-Code, Pi). Eliminates AI tells across prose, visual UI artifacts, and source code.

---

## What This Repository Does

Large language models and coding agents produce predictable patterns of low-substance output ("slop"). This repository provides a unified standard and executable agent skills to detect and eliminate slop across three primary domains:

1. **Prose and Technical Documentation**: Eliminates throat-clearing openers, empty intensifiers, formulaic binary contrasts, connecting em-dashes, passive voice, and all metaphors/analogies.
2. **Visual Artifacts and User Interfaces**: Eliminates cluttered layouts, emoji badges, unanchored metrics, fake non-functional buttons, and wall-of-text artifacts. Enforces structured layouts tailored to the reader's operational objective.
3. **Source Code and Engineering**: Eliminates trivial syntax-restating comments, placeholder stubs (`// TODO: implement later`), synthetic mocks in production paths, and unnecessary boilerplate.

---

## Repository Structure

```
stop-slop/
├── .claude-plugin/
│   └── marketplace.json            # Claude Code plugin marketplace manifest
├── .cursor/
│   └── rules/
│       └── stop-slop.mdc           # Cursor and Codex rule configuration
├── .clinerules                      # Cline and Roo-Code rule configuration
├── AGENTS.md                        # Multi-agent universal execution standard
├── CHANGELOG.md                     # Revision log
├── LICENSE                          # MIT License
├── README.md                        # Documentation and multi-agent setup guide
├── SKILL.md                         # Universal Agent Skill definition (Prose, Artifacts, Code)
├── plugins/
│   └── stop-slop/
│       ├── .claude-plugin/
│       │   └── plugin.json          # Claude Code plugin manifest
│       └── skills/
│           └── stop-slop/
│               └── SKILL.md         # Mirrored skill for plugin packaging
├── references/
│   ├── phrases.md                   # Prose: Banned openers, filler, and throat-clearing
│   ├── structures.md                # Prose: Structural clichés, binary contrasts, and zero-metaphor rules
│   ├── slop-words.md                # Prose: Two-tier slop word bank (~850 words)
│   ├── artifacts.md                 # Artifacts/UI: Job-to-form taxonomy, 10 design rules, CSS style kit
│   ├── code.md                      # Code: Decision-focused comments and runnable implementation standards
│   └── examples.md                  # Before/after transformations across all three domains
└── examples/                        # Standalone, clean reference HTML artifacts
    ├── deal-pricer.html             # Interactive tool and pricing calculator
    ├── decision-page.html           # Executive decision memo
    ├── expense-guide.html           # Step-by-step workflow guide
    ├── fixed-dashboard.html         # Clean operational metrics dashboard
    ├── hiring-dashboard.html        # Candidate tracking dashboard
    ├── monthly-report.html          # Financial report with dynamic SVG charts
    ├── pitch-slides.html            # Interactive slide deck
    ├── sloppy-dashboard.html        # "Before" anti-pattern demonstration
    └── support-cheat-sheet.html     # Reference cheat sheet with live client-side search
```

---

## Agent Configuration and Integration

Configure your preferred coding agent to use the Stop Slop standard:

### 1. Google Antigravity (`agy`)
Antigravity automatically loads `SKILL.md` from the workspace root or user skill library.
* **Workspace skill**: Clone this repository into your workspace or symlink the folder to `.agents/skills/stop-slop` or `.gemini/antigravity-cli/skills/stop-slop`.
* **Prompt invocation**:
  ```
  Apply stop-slop skill to audit and clean [FILE or ARTIFACT].
  ```

### 2. Anthropic Claude Code
Claude Code discovers the skill via the `.claude-plugin` directory or direct skill configuration.
* **Install via plugin**:
  ```bash
  claude plugin add kenhuangus/stop-slop
  ```
* **Direct skill loading**:
  Point Claude Code to `SKILL.md` in your project root or add the skill to your project settings.
* **Prompt invocation**:
  ```
  Make an HTML page about [TOPIC] for [AUDIENCE]. Follow stop-slop.
  ```
  ```
  Review this draft prose. Follow stop-slop to remove AI writing tells.
  ```

### 3. Cursor and OpenAI Codex
Cursor automatically applies `.cursor/rules/stop-slop.mdc` to all workspace interactions. Codex reads `AGENTS.md` and repository rules.
* **Automatic application**: `.cursor/rules/stop-slop.mdc` is pre-configured with `alwaysApply: true`.
* **Manual command**:
  ```
  Refactor this function according to stop-slop code standards: decision-focused comments only and verified runnable code.
  ```

### 4. Cline and Roo-Code
Cline and Roo-Code automatically parse `.clinerules` located in the workspace root.
* Ensure `.clinerules` is committed in the root directory of your project.

### 5. Pi and Open-Source LLMs
Include `SKILL.md` in your model's system prompt or reference files.

---

## Core Anti-Slop Rules

### Pillar 1: Prose and Documentation
* **Eliminate throat-clearing**: Delete openers like "Here's the thing", "In today's fast-paced world", "It turns out that", "Let's dive in", and "At its core".
* **Cut adverbs**: Remove all adverbs. Use concrete verbs.
* **Zero metaphors and zero direct analogies**: No metaphor or direct analogy should be used in any sentence. Avoid figurative comparisons, spatial metaphors, and pedagogical analogies ("think of X as Y", "navigating a maze", "building a bridge between systems"). State literal facts and technical mechanisms directly.
* **State assertions directly**: Eliminate artificial binary contrasts ("Not X, but Y") and rhetorical questions.
* **Ban connecting dashes**: Do not use em-dashes (`—`) or en-dashes to join clauses. Use periods or commas.
* **Eliminate divider lines**: Drop markdown horizontal rules (`---`) between sections. Let headings define structure.
* **Check the Word Bank**: Scan against Tier 1 banned words (delve, elevate, streamline, seamless, robust, holistic, paradigm, flywheel) in [references/slop-words.md](references/slop-words.md).

### Pillar 2: Visual Artifacts and User Interfaces
* **Form follows the reader's job**: Match layout structure to functional purpose:
  * *Decide (Memo/Brief)*: Top ask and deadline; comparative option cards; risk matrix.
  * *Catch Up (Report)*: 3-4 primary metric tiles with comparative baselines; single trend chart; action cards.
  * *Monitor (Dashboard)*: Metric tiles on top; categorized cards; standardized status pills.
  * *Learn/Execute (Guide)*: Step progression bar; one view per step with Next/Back controls.
  * *Present (Slides)*: One thesis per slide; single large visual paired with one direct sentence.
  * *Calculate (Tool)*: Inputs on left, calculated output on right; working default data on load.
  * *Reference (Cheat Sheet)*: Categorized cards with live filter.
* **Show it, do not write it**: Visuals carry quantitative data (numbers, labels, units, axes). No decorative mock windows or non-functional buttons.
* **The first screen stands alone**: Communicate conclusion, rationale, and next steps within 50 to 120 words before scrolling.
* **Enforce density limits**: Maximum 4 sections below the initial screen, maximum 5 items per card, maximum 1 primary table.
* **Clean palette**: Neutral high-contrast surfaces (`#ffffff` / `#151515`), system typography, and semantic status colors (green, red, amber). No emoji badge spam (🚀, ✨, 🔥, 💰).

### Pillar 3: Source Code and Engineering
* **Decision-focused comments**: Explain *why* a technical choice was made (invariants, business rules, edge cases). Never restate syntax (`# increment counter`).
* **Complete, runnable implementations**: Never output placeholder stubs (`// TODO: implement later`) or synthetic mocks in production paths.
* **Direct architecture**: Avoid unnecessary abstraction layers and premature generalization for single-use routines.
* **Verified execution**: Never claim code or tests succeed without verifying execution in the environment.

---

## Reference Examples

Browse verified clean implementations in the [examples/](examples/) directory:

| Objective | Template File | Live Demo Preview |
|---|---|---|
| Executive Decision Memo | [examples/decision-page.html](examples/decision-page.html) | Side-by-side option cards with cost breakdown |
| Monthly Operational Report | [examples/monthly-report.html](examples/monthly-report.html) | Clean financial report with dynamic SVG charts |
| Hiring Tracker Dashboard | [examples/hiring-dashboard.html](examples/hiring-dashboard.html) | Candidate pipeline tracker with status pills |
| Operational Metrics Dashboard | [examples/fixed-dashboard.html](examples/fixed-dashboard.html) | Clean, high-contrast metrics layout |
| Step-by-Step Workflow Guide | [examples/expense-guide.html](examples/expense-guide.html) | Interactive reimbursement workflow with step controls |
| Stakeholder Slide Deck | [examples/pitch-slides.html](examples/pitch-slides.html) | Interactive presentation deck with keyboard navigation |
| Deal Pricing Calculator | [examples/deal-pricer.html](examples/deal-pricer.html) | Interactive seat pricing estimator and email generator |
| Support Reference Cheat Sheet | [examples/support-cheat-sheet.html](examples/support-cheat-sheet.html) | Single-page lookup sheet with instant keyboard search |
| **Anti-Pattern (AI Slop)** | [examples/sloppy-dashboard.html](examples/sloppy-dashboard.html) | Example of visual slop: neon gradients, emojis, and unanchored metrics |

---

## Scoring Matrix

Evaluate outputs against five dimensions (1 to 10 points each):

| Dimension | Evaluation Criteria |
|---|---|
| **Directness** | Are statements delivered immediately without preamble or rhetorical scaffolding? |
| **Substance** | Are claims backed by concrete numbers, verified facts, or runnable code? |
| **Structure** | Does the layout or organization directly serve the reader's operational objective? |
| **Authenticity** | Does the output read like natural human technical communication without AI cliches? |
| **Density** | Has all redundant commentary, decorative styling, and filler been eliminated? |

**Standard**: Outputs scoring below 40/50 require revision before delivery.

---

## Authors and Credits

* **[Ken Huang](https://github.com/kenhuangus)**: Maintainer, unified 3-pillar anti-slop standard (prose, artifacts, and engineering code), multi-agent integration framework (agy, Claude Code, Cursor, Codex, Cline).
* **[Hardik Pandya](https://hvpandya.com)**: Creator of the original `stop-slop` prose guidelines and structural pattern analysis.
* **[Ruben Hassid](https://www.linkedin.com/in/ruben-hassid/)**: Creator of the artifact and visual design rules and HTML templates (originally developed under `noslop`).
* **Damir Sokolovsky**: Inspiration for comparative change baselines and artifact fix workflows (from `unslop`).

---

## License

MIT License. Use freely, adapt widely, and stop the slop.
