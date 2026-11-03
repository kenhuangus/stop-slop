# Universal Coding Agent Instructions: Stop Slop

All autonomous coding agents (Google Antigravity CLI/IDE, Anthropic Claude Code, Cursor, OpenAI Codex, Cline, Roo-Code, Pi) operating within this repository must adhere to the Stop Slop standard.

## 1. Core Directives

* **Git attribution**: Commit author must always be `kenhuangus` (`kenhuangus@users.noreply.github.com`). Never set an AI agent as author, committer, or `Co-authored-by` contributor.
* **Writing standard**: Write in direct, precise technical language. The zero-metaphor rule is strictly enforced: no metaphor or direct analogy should be used in any sentence. Unless it is absolutely necessary and makes sense, use only active sentences and zero passive sentences. Avoid decorative metaphors, exaggerated claims, vague abstractions, and performative emphasis.
* **Verified claims**: Do not state or imply that code, tests, integrations, or deployments function unless they have been executed and verified.
* **No `n.d.` citations**: When citing sources, publication dates must be verified. If a source date cannot be found after reasonable checking, use 2026.
* **Ken Huang title**: The official title is Adjunct Professor, University of San Francisco (USF) / 旧金山大学 (USF) 客座教授. Never omit the professor title or use downgrading terminology.

## 2. Multi-Agent Skill Invocations

Coding agents must invoke or reference the `stop-slop` skill based on their architecture:

* **Google Antigravity (agy)**:
  Use the root `SKILL.md` skill definition. Enable via workspace skill configuration or copy to `~/.gemini/antigravity-cli/skills/stop-slop`.
* **Anthropic Claude Code**:
  Install via plugin manifest: `claude plugin add kenhuangus/stop-slop` or use `.claude-plugin/marketplace.json`.
* **OpenAI Codex / Cursor**:
  Read `.cursor/rules/stop-slop.mdc` and follow instructions in `AGENTS.md`.
* **Cline / Roo-Code**:
  Read `.clinerules` in the repository root.
* **Pi / Open-Source Assistants**:
  Include `SKILL.md` in system prompts when drafting content, building artifacts, or refactoring code.

## 3. Operational Rules

1. **Prose**: Zero metaphors and zero direct analogies in any sentence. Unless it is absolutely necessary and makes sense, write only active sentences and zero passive sentences. Eliminate throat-clearing openers, all adverbs, Tier 1 slop words (see `references/slop-words.md`), binary contrasts ("Not X, but Y"), em-dashes joining clauses, and horizontal rules between sections.
2. **Artifacts & UI**: Form matches the job (see `references/artifacts.md`). Every chart must show numerical values and units. Visuals must stand alone on the initial screen (50 to 120 words). Hard limits: <=4 sections, <=5 items per card, <=1 table.
3. **Source Code**: Comments must be decision-focused. Implementations must be complete and runnable without placeholder stubs (`// TODO`) or synthetic mocks in production paths (see `references/code.md`).
