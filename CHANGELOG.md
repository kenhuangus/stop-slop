# Changelog

## 2026-11-03

### Added
- **Zero-Metaphor and Zero-Analogy Rule**: Strictly prohibited the use of metaphors, similes, and direct analogies in any sentence across all prose and agent responses. Added dedicated structural analysis, phrase scan lists, and before/after transformation models.
- **Unified 3-Pillar Anti-Slop Architecture**: Integrated prose anti-slop with visual UI/artifact anti-slop and source code engineering anti-slop.
- **Visual Artifact Standards (`references/artifacts.md`)**: Added job-to-form taxonomy, 10 core design rules, density limits, standard CSS palette, and web version deployment guidelines (integrated and adapted from Ruben Hassid's `noslop`).
- **Code Anti-Slop Standards (`references/code.md`)**: Added standards for decision-focused comments, complete runnable implementations (no placeholder `TODO` stubs or synthetic mocks), minimal architecture, and verified execution.
- **Standalone Reference Artifacts (`examples/`)**: Imported 9 HTML templates (decision page, monthly report, hiring dashboard, fixed dashboard, expense guide, pitch slides, deal pricer, support cheat sheet, and sloppy dashboard anti-pattern), stripped of telemetry/frame-runtime sandbox bloat.
- **Multi-Agent Configuration Adapters**:
  - Claude Code: `.claude-plugin/marketplace.json` and `plugins/stop-slop/.claude-plugin/plugin.json`.
  - Cursor & OpenAI Codex: `.cursor/rules/stop-slop.mdc`.
  - Cline & Roo-Code: `.clinerules`.
  - Universal Coding Agents (agy, Codex, open assistants): `AGENTS.md`.

### Changed
- Refactored all previous naming to standard `stop-slop`.
- Expanded `SKILL.md` to cover prose, visual artifacts, and code engineering with quick checklists and a 50-point evaluation scoring matrix.
- Enriched `references/examples.md` with visual artifact and source code before/after transformations.

## 2026-01-13

### Added

**Phrases (references/phrases.md)**
- Throat-clearing: "Here's what I find interesting", "Here's the problem though"
- Performative emphasis: "creeps in", "I promise", "They exist, I promise"
- Telling instead of showing: "This is genuinely hard", "This is what leadership actually looks like"

**Structures (references/structures.md)**
- Binary contrasts: "Not X. But Y.", "It's not this. It's that.", "stops being X and starts being Y"
- Rhythm patterns: staccato fragmentation, dashes for dramatic pause, hedging as reassurance
- Word patterns: absolute words (always, never, everyone, etc.), AI-overused intensifiers (deeply, truly, fundamentally, inherently, simply, literally, inevitably)

## 2026-01-12

- Restructured skill following Claude Code best practices (PR #1)
- Split into SKILL.md and references/ folder

## 2025-01-12

- Initial release
