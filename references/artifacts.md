# Artifacts and UI Anti-Slop Guide

Guidelines for eliminating visual and structural slop from AI-generated artifacts, user interfaces, dashboards, and documents.

## 1. Determine Reader Requirements and Job Scope

Before constructing an interface or artifact, determine three core parameters:

1. **Audience profile**: Identify who reads the output and their baseline knowledge.
2. **Target action**: Define the required next step: decide, catch up, monitor, learn, approve, or calculate.
3. **Reading frequency**: Establish whether the document is read once or referenced repeatedly.

If the prompt lacks these parameters, confirm them directly before generating output. If the response fits in a short direct message, write the message rather than generating an unnecessary artifact.

## 2. Match Artifact Form to Functional Objective

Layout must reflect functional purpose. Do not use a generic dashboard layout for every task.

| Objective | Artifact Type | Structure |
|---|---|---|
| **Decide** (Memo, brief, proposal) | Decision page | Primary request and deadline at top. Options displayed side-by-side as cards with the recommendation highlighted. Quantitative trade-offs as comparative bars. Risks listed concisely. |
| **Catch up** (Weekly or monthly update) | Report | Top 3-4 operational metrics as numeric tiles with deltas versus prior periods. Exactly one primary chart. Action items and decisions formatted as discrete cards. Sequential event summary below. |
| **Monitor** (Tracker, system dashboard) | Dashboard | Key indicators on top. Domain sections organized in dedicated cards. Status indicated by standardized status pills. One chart per operational question. |
| **Learn or execute** (Onboarding, SOP, guide) | Step-by-step workflow | Visual progression path at top. Step-by-step sequential view with Back and Next controls. Each step displays actual interface states, explicit requirements, constraints, and deadlines. |
| **Present or convince** (Pitch, stakeholder proposal) | Slide deck | One thesis per slide. Each slide pairs one visual element (metric, chart, comparative layout) with one direct summary sentence. Sequential controls. Final slide specifies the direct request. |
| **Calculate or interact** (Tool, estimator, planner) | Interactive tool | Single-screen layout. Inputs on left, calculated output on right. Operational with realistic default values immediately upon loading. |
| **Reference** (Cheat sheet, syntax guide) | Reference sheet | Topic-grouped cards with functional headers. Each entry consists of an explicit keyword and a direct definition. Warnings highlighted in designated alert styling. Fits single view. |

## 3. Ten Core Design Rules

1. **Visuals convey primary information.** Visual elements must carry data rather than decoration. Every chart, bar, and metric must include explicit numbers, units, and axis labels. Do not use decorative mock windows, empty bars, or non-functional buttons. Every section must lead with structured data: a metric callout, comparison table, timeline, or workflow sequence.
2. **Identify context and objective at the top.** Include a structured metadata line at the head of the artifact (under 15 words) specifying what the document is, creator, recipient, date, and primary action required. State the core takeaway as the primary heading. State the direct request with responsible person, deadline, and response channel. State this request once; do not repeat it in banners, boxes, and buttons simultaneously.
3. **Use direct language.** Write headings and labels in standard technical prose (e.g., "4 candidates pending interview schedule", not "Candidates in motion"). Avoid dramatic slogans and redundant subtitles beneath headings.
4. **Retain necessary technical detail.** Simple design does not mean omission of essential facts. Include precise figures, operational limits, effective dates, owners, approval gates, exceptions, and links. State comparative baselines for every metric delta (e.g., "+$1,043 versus September", never "+$1,043"). Place reference material (methodologies, full raw tables) one click away in expandable rows or reference tabs.
5. **Eliminate narrative text blocks and redundant captions.** Paragraphs must not exceed 2 sentences. Table cells must not exceed 10 words. If text exceeds 6 consecutive lines, divide content into categorized cards. Highlight primary terms in bold. Avoid secondary explanatory captions beneath numbers or headings; make the primary label precise instead.
6. **Apply a standardized, high-contrast palette.** Use neutral backgrounds (`#ffffff` light, `#151515` dark), subtle borders, system typography (serif for titles, sans-serif for interface elements and data), and reserve color for semantic meaning: green for positive/complete, red for negative/blocked, amber for warning/review, and a single neutral accent tone for primary actions.
7. **Maintain clear visual hierarchy and enforce hard limits.** Layouts must direct visual attention to the most critical data first without unbounded scrolling. Reports, decision memos, and proposals should fit within two standard display heights without nested tabs.
   * Hard limits: At most 4 content sections beneath the primary screen.
   * At most 5 items per card or list.
   * At most 1 comprehensive table per view.
8. **Ensure the initial view functions independently.** The initial display screen must communicate the core status, primary rationale, and required action before any scrolling occurs. This screen contains the header metadata, title, primary metric or visual, and concise decision rationale (50 to 120 words total).
9. **Eliminate non-essential content rather than hiding it.** Moving excessive copy into collapsible accordions or tabs does not solve structural bloat. Retain only actionable facts, key risks, and owners in the primary interface.
10. **Present each data point once.** Avoid duplicating the same figure in headings, metric tiles, and narrative text. Avoid displaying the same underlying dataset in multiple formats (e.g., calendar view alongside an identical table). Ensure all component figures sum accurately to reported totals.

## 4. Visual Slop Checklist

Reject or revise artifacts exhibiting any of the following characteristics:

* Bullet lists and paragraphs used where structured tables, charts, or metrics convey the information more directly.
* Missing header metadata: Document lacks author, recipient, date, or purpose.
* Artificial headings ("Navigating the Horizon", "Unlocking Growth") rather than literal statements.
* Secondary subtitles beneath headings or explanatory captions under metric callouts.
* Introductory narrative paragraphs placed between titles and primary data.
* More than 4 primary numeric callouts competing for visual priority.
* Decorative visual elements: Fake window controls, bar charts without quantitative values, non-functional action buttons.
* Inconsistent metrics: Deltas without comparative baselines (e.g., "+15%" without stating time interval).
* Cluttered visual artifacts: Gradients, neon accents, floating badge tags, or emoji used in place of standard interface icons.
* Text overflow: Labels truncated or wrapped mid-number across responsive breakpoints (1440px and 400px).
* Repetitive representations: Identical records displayed in both card grids and data tables.
* Exceeding structural density limits: More than 4 sections, cards with more than 5 items, or multiple large tables.

## 5. Artifact Revision Procedure

When revising an existing interface or artifact:

1. Inventory all visual slop indicators present in the current artifact. Count word volume on the initial viewport.
2. Formulate one direct sentence stating what the user must evaluate or perform.
3. Determine revision scope:
   * **Full rebuild**: If the layout uses an incorrect form for the objective or violates primary design rules, construct a new layout from functional requirements.
   * **Targeted fix**: If the structure is sound and only isolated labels, alignments, or paddings are non-compliant, correct those elements directly.
4. If rebuilding, do not reproduce the previous section breakdown or container hierarchy. Reduce total word count by at least 40% while preserving every operational fact, constraint, and metric.
5. Re-verify all numbers, percentages, and names against the original specification to prevent data loss or distortion.

## 6. Pre-Delivery Verification

Verify the artifact against these objective criteria before delivery:

* Do the structured visuals and metrics tell the complete operational story if all paragraphs are hidden?
* Does the initial screen state the core finding, justification, and required response within 50-120 words?
* Are all metric changes anchored to explicit comparative baselines?
* Are headings literal, direct technical statements?
* Does the interface render without horizontal overflow, text clipping, or broken layouts at 1440px and 400px widths?
* Can a technical lead or manager review the document without requiring supplemental briefing?

## 7. Standard CSS Foundation

```css
:root {
  --bg: #ffffff;
  --surface: #f9f9f9;
  --card: #ffffff;
  --text-primary: rgba(0, 0, 0, 0.9);
  --text-secondary: rgba(0, 0, 0, 0.6);
  --text-tertiary: rgba(0, 0, 0, 0.45);
  --border: rgba(0, 0, 0, 0.12);
  --shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  --accent: #2563eb;
  --accent-action: #1d4ed8;
  --state-good: #15803d;
  --state-good-bg: rgba(22, 163, 74, 0.12);
  --state-bad: #b91c1c;
  --state-bad-bg: rgba(220, 38, 38, 0.12);
  --state-warn: #b45309;
  --state-warn-bg: rgba(217, 119, 6, 0.12);
  --font-title: Georgia, "Times New Roman", serif;
  --font-ui: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --bg: #121212;
    --surface: #1a1a1a;
    --card: #202020;
    --text-primary: rgba(255, 255, 255, 0.92);
    --text-secondary: rgba(255, 255, 255, 0.6);
    --text-tertiary: rgba(255, 255, 255, 0.4);
    --border: rgba(255, 255, 255, 0.14);
    --shadow: none;
    --accent: #3b82f6;
    --accent-action: #2563eb;
    --state-good: #4ade80;
    --state-bad: #f87171;
    --state-warn: #fbbf24;
    color-scheme: dark;
  }
}

body {
  margin: 0;
  background: var(--bg);
  color: var(--text-primary);
  font: 16px/1.55 var(--font-ui);
}

h1, h2 {
  font-family: var(--font-title);
  font-weight: 400;
  margin: 0;
  text-wrap: balance;
}

h1 { font-size: 32px; line-height: 1.25; }
h2 { font-size: 22px; line-height: 1.3; }

.meta-header {
  font-size: 13px;
  color: var(--text-secondary);
  border-bottom: 1px solid var(--border);
  padding: 12px 0;
}

.card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  box-shadow: var(--shadow);
  padding: 20px;
}

.metric-value {
  font-size: 38px;
  font-weight: 600;
  line-height: 1;
}

.status-pill {
  display: inline-block;
  border-radius: 999px;
  padding: 3px 10px;
  font-size: 12px;
  font-weight: 500;
}

.status-good { color: var(--state-good); background: var(--state-good-bg); }
.status-bad { color: var(--state-bad); background: var(--state-bad-bg); }
.status-warn { color: var(--state-warn); background: var(--state-warn-bg); }

button {
  font: 500 15px var(--font-ui);
  border-radius: 8px;
  padding: 9px 16px;
  cursor: pointer;
  background: var(--card);
  color: var(--text-primary);
  border: 1px solid var(--border);
}

button.primary {
  background: var(--accent-action);
  color: #ffffff;
  border: 0;
}
```

## 8. Web Application Production Standards

When developing deployable web application versions:

* **Technology stack**: Use Vite, React, TypeScript, Tailwind CSS, standard accessible component primitives, and SVG/canvas charting (e.g., Recharts). Do not introduce commercial or external paid runtime dependencies.
* **Responsive stability**: Ensure all grid structures transition to single-column wrapping on mobile viewports. Explicitly disallow fixed `white-space: nowrap` inside narrow containers.
* **Security and isolation**:
  1. Store production prototypes in private repositories.
  2. Protect staging deployments with authentication or environment-variable gated access middleware. Never commit access tokens or passcodes directly to source code.
  3. Include `X-Robots-Tag: noindex` in response headers to prevent search indexing of internal data.
