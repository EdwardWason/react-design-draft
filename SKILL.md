---
name: "react-design-draft"
version: "4.1.0"
category: "content-creation"
description: "Generate React design drafts (4-piece set) from content. Invoke for 'design draft'/'设计稿'/'生成页面'/'信息图'/'知识卡片'/'多图配图'. Do NOT use for editing existing code."
metadata:
  requires_api_key: false
---

# React Design Draft Generator v4.1

Transforms user content into information-dense, visually refined React design drafts. Core advantage: **every element is independently editable, restructuring-capable, and version-controllable**.

## Task

Only generates React design drafts from content. Does NOT: write production apps, edit existing projects, or replace full development workflows.

## Mode Detection

```
User input contains "多图"/"配图"/"全套"/"文章配图"/"封面+配图"?
  → YES: Multi-Illustration Mode (5-step flow)
  → NO: Single Draft Mode (5-step flow, different steps)
```

---

## Single Draft Mode

```
User Content → Step 0: Brand Profile → Step 1: Parse & Match → Step 2: Confirm & Advise → Step 3: Generate → Step 4: Post-Generation Guide
```

### Step 0: Brand Profile (if applicable)

Read [`references/brand-profile.md`](references/brand-profile.md) for the four-layer brand configuration system.

1. **Check explicit prompts** — user-specified `--layout/--style/--palette/--brand` flags (highest priority)
2. **Check Brand DNA auto-detection** — scan content source URL/keywords against Brand DNA Registry
3. **Check user brand profile** — load `~/.config/react-design-draft/brand.md` if exists
4. **Check project style scan** — if user references a sibling project, scan its CSS/tokens
5. **Fall through to auto-selection** — if no higher layer applies

### Step 1: Parse & Match

Read [`references/content-layout-mapping.md`](references/content-layout-mapping.md) for the three-dimension system.

1. **Check brand DNA** — scan content source URL and keywords against Brand DNA Registry in [`references/content-layout-mapping.md`](references/content-layout-mapping.md). If matched, apply brand visual DNA (highest priority).
2. **Check keyword shortcuts** — scan user input against [`references/style-presets.md`](references/style-presets.md). If a preset keyword matches, use that as defaults.
3. **Parse content structure** — extract: content type, key units count, density level.
4. **Check chart needs** — if content contains numeric comparisons, time-series, or hierarchical data, suggest chart types from [`references/chart-system.md`](references/chart-system.md).
5. **Content quality pre-check** — apply writing quality rules:
   - **Assertion-evidence**: Titles must be complete assertions, not topic labels
   - **Impact formula**: Resume/achievement entries use Action + Scope + Measurable Result
   - **Data over adjectives**: Every claim must survive "how much exactly?" challenge
   - **No AI officialese**: Ban 赋能/打造/拥抱/助力/leverage/unlock/seamlessly
6. **Auto-select three dimensions**: Layout × Style × Palette.
7. **Allow user override** — if user specifies any dimension explicitly, override that dimension only.

### Step 2: Confirm & Advise (MANDATORY)

Never skip. Present the selected combination AND adaptation advice before generating:

```
📐 Layout: <name> — <reason>
🎨 Style: <name> — <reason>
🎯 Palette: <name> — <reason>
📊 Density: <level> — <N> key units
📈 Charts: <type> — <reason> (if applicable)

📋 Adaptation Advice:
- Aspect ratio / Mobile-friendly / Recommended output

🔄 Alternative options:
- If you want <X>, try --style <alt>
- If targeting <Y>, try --layout <alt>

确认生成？或指定调整：--layout / --style / --palette
```

Only skip if user says "直接生成".

### Step 3: Generate React 4-Piece Set

Read [`references/react-output-spec.md`](references/react-output-spec.md) for output spec.
Read [`references/aesthetics-guide.md`](references/aesthetics-guide.md) for style CSS details.
Read [`references/density-standards.md`](references/density-standards.md) for quality thresholds.
Read [`references/chart-system.md`](references/chart-system.md) for chart component specs.

Output: `design-tokens.css` + `data.js` + `components/*.jsx` + `App.jsx`

### Step 4: Post-Generation Guide (MANDATORY)

Always append after generation. This is the #1 advantage of React design drafts. See [`references/react-output-spec.md`](references/react-output-spec.md) "Interactive Edit Guide" section for the full template. Must include:

- **File Tree** with edit-responsibility annotations
- **Quick Edits** map (user intent → file → action)
- **Component Hierarchy** tree (editable structure)
- **Restructure hint**: tell user they can extract/refactor components

---

## Multi-Illustration Mode

Read [`references/multi-illustration.md`](references/multi-illustration.md) for full spec.

```
Article Input → Step A: Article Parsing → Step B: Illustration Plan (MANDATORY) → Step C: Style Unification → Step D: Batch Generate → Step E: Illustration Map
```

### Step A: Article Parsing (Silent)

Extract from article: core thesis, data points, logic chains, processes, comparisons, key quotes, hierarchies, timelines, brand info. See [`references/multi-illustration.md`](references/multi-illustration.md) Step A for extraction rules.

### Step B: Illustration Plan + Density Scoring (MANDATORY)

**Confirmation Point 1** — show every proposed illustration with:
- Source (which section/paragraph)
- Type + Layout
- Density score (3-dimension 15-point: Information Increment + Data Value + Standalone Readability)
- Gate result (≥9/15 = pass, <9 = skip/merge)

User can: confirm / add / remove / change type / merge. Gate-failed items shown but marked for skip.

### Step C: Style Unification (Confirmation Point 2)

Show unified style plan: shared palette + style + fonts + size specs. All illustrations share one `design-tokens.css`. User can override individual illustrations. Skip if user says "直接生成".

### Step D: Batch Generate

Output directory: `[article-name]-illustrations/` with `shared/design-tokens.css` + per-illustration `data.js` + `components/` + `App.jsx` + `index.html` preview.

### Step E: Illustration Map

Show article section ↔ illustration mapping + per-illustration edit guide.

---

## Rules

1. **Three-dimension combination**: Layout × Style × Palette. See [`references/content-layout-mapping.md`](references/content-layout-mapping.md).
2. **Content-first**: Layout serves content structure. Every visual element carries information.
3. **Density = signal per pixel**: Single mode ≥16/25; Multi mode per-illustration ≥9/15. See [`references/density-standards.md`](references/density-standards.md).
4. **Data-driven**: All data in `data.js`. Components receive via props. Zero data in JSX.
5. **Design tokens as single source of truth**: All visual values reference CSS variables. No magic numbers.
6. **Anti-AI-slop**: See [`references/aesthetics-guide.md`](references/aesthetics-guide.md) and extended anti-patterns in [`references/density-standards.md`](references/density-standards.md).
7. **Pre-generation consultation mandatory**: Always show planned combination + advice first.
8. **Post-generation edit guide mandatory**: Always output Component Map & Edit Guide.
9. **Component granularity**: Each visual concern = own component. Extract ComparisonBlock, StepList, QuestionList etc. Avoid monolithic components > 80 lines.
10. **Local-first fonts**: Prioritize local CJK fonts over web fonts. See [`references/aesthetics-guide.md`](references/aesthetics-guide.md).
11. **Brand profile resolution**: Apply four-layer brand config. See [`references/brand-profile.md`](references/brand-profile.md).
12. **Chart auto-selection**: When content contains numeric data, suggest chart type from [`references/chart-system.md`](references/chart-system.md).
13. **Writing quality gate**: Apply assertion-evidence, impact formula, data-over-adjectives, no-AI-officialese rules before generating.
14. **Multi-illustration: content drives quantity** — number of illustrations determined by extractable visualizable units, not by fixed template. See [`references/multi-illustration.md`](references/multi-illustration.md).
15. **Multi-illustration: every illustration passes density gate** — 3-dimension 15-point scoring, ≥9 to generate. Gate-failed items skipped unless user explicitly overrides.
