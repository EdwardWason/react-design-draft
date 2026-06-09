# Multi-Illustration Mode

Generate multiple illustrations for a single article. Triggered by keywords: `多图` / `配图` / `全套` / `文章配图` / `封面+配图`.

## Core Principles

1. **Content drives quantity, not templates** — extract "visualizable units" from content, don't force a fixed number
2. **Every illustration independently passes density gate** — 3-dimension 15-point scoring, ≥9 to generate
3. **Style consistency across all illustrations** — shared design-tokens.css, shared palette + style
4. **Two confirmation points before generation** — content plan first, then style plan

## Execution Flow

```
Article Input
  ↓
Step A: Article Parsing (silent)
  ↓
Step B: Illustration Plan + Density Scoring ← Confirmation Point 1 (MANDATORY)
  ↓
Step C: Style Unification ← Confirmation Point 2 (default required, "直接生成" skips)
  ↓
Step D: Batch Generation
  ↓
Step E: Illustration Map
```

## Step A: Article Parsing (Silent)

Read the full article and extract:

| Extract | What to Look For | Illustration Type |
|---------|-----------------|-------------------|
| **Core thesis** | The one-sentence argument | cover |
| **Data points** | 3+ related numbers, percentages, trends | data chart (bar/line/donut) |
| **Logic chains** | Causal/sequential/conditional reasoning | logic-chain, flow-chart |
| **Processes** | 3+ sequential steps | flow-chart, swimlane |
| **Comparisons** | A vs B with 3+ attributes each | versus, comparison |
| **Key quotes** | Statements impactful outside context | quote-card |
| **Hierarchies** | Nested/categorical structures | tree-chart, layered-diagram |
| **Timelines** | Chronological milestones | timeline |
| **Supply/demand** | Gap/shortage narratives | bar-chart, waterfall |
| **Brand info** | Author name, publication, QR code | back-cover |

### Extraction Rules

- A "visualizable unit" must have **≥2 data points** OR **a clear logical structure** OR **standalone quote impact**
- Isolated single numbers are NOT visualizable (e.g., "48天" alone → not a chart; "48天 + 5000亿 + 万亿" together → timeline)
- Narrative paragraphs without data/structure/quotes are NOT visualizable
- When two units share the same source section and overlap in content, **merge** them

## Step B: Illustration Plan + Density Scoring (Confirmation Point 1 - MANDATORY)

### Density Scoring for Individual Illustrations

Each proposed illustration is scored on 3 dimensions (5 points each, 15 total):

| Dimension | 1 | 2 | 3 | 4 | 5 |
|-----------|---|---|---|---|---|
| **Information Increment** | Pure decoration, text already clear | Minor reorganization | Reorganizes info for easier understanding | Reveals hidden patterns | Reveals relationships/structures invisible in text |
| **Data Value** | No data | 1 data point | 2-3 data points | 4+ data points | 4+ data points + reveals relationships between them |
| **Standalone Readability** | Fully depends on context | Needs section context | Needs title + subtitle | Needs title only | Self-explanatory |

**Gate threshold: ≥9/15.** Below 9 = skip or merge.

### Output Format

```
📋 配图方案：共 N 张（基于内容分析，非固定数量）

┌─────────────────────────────────────────────────────┐
│ #1 [Title]                                           │
│ 来源：[section/paragraph reference]                   │
│ 类型：[type] · [layout]                              │
│ 密度评分：[X]/15（信息[A] + 数据[B] + 独立[C]）      │
│ 内容：[what this illustration shows]                  │
│ ✅ 通过门控 / ❌ 未通过门控（建议跳过/合并）         │
├─────────────────────────────────────────────────────┤
│ #2 ...                                               │
└─────────────────────────────────────────────────────┘

📊 方案统计：
- 通过门控：X张 ✅
- 未通过门控：Y张 ❌（已标记跳过）
- 可合并：Z张 ⚠️（[merge suggestion]）

操作：
- "确认" → 按方案生成
- "加上第N张" → 覆盖门控，强制生成
- "去掉第N张" → 从方案中移除
- "第N张换成[类型]" → 调整配图类型
- "合并第M和第N张" → 合并为一张
```

### User Override Rules

- User can **add** any illustration (override gate) — but must explicitly request it
- User can **remove** any illustration — no justification needed
- User can **change type** of any illustration — e.g., "第3张换成流程图"
- User can **merge** illustrations — e.g., "合并第5和第6张"
- Gate-failed illustrations are **shown but marked for skip** — user decides, not the system

## Step C: Style Unification (Confirmation Point 2)

After confirming WHAT to illustrate, confirm HOW to illustrate.

### Output Format

```
🎨 风格方案：全文统一

📐 风格：[style] — [reason]
🎯 配色：[palette] — [reason]
🔤 字体：[display] + [body]
📏 尺寸规范：
  - 封面：900×383（公众号封面 2.35:1）
  - 正文配图：640px 宽（公众号正文区）
  - 金句图：640×640（1:1）
  - 封底：900×383

所有配图共享同一 design-tokens.css，确保风格一致。

确认风格？或调整：--style / --palette
```

### Style Consistency Rules

1. **All illustrations share the same design-tokens.css** — one palette, one font system
2. **Layout varies per illustration type** — but colors/fonts/spacing are identical
3. **Brand DNA applies to all** — if economist-red is selected, ALL illustrations use it
4. **Individual illustration style override is allowed** — e.g., "第3张用纸墨风" → that one gets its own tokens override

### Skip Conditions

- User says "直接生成" → skip Step C, auto-match style from content analysis
- User says "快速搞定" → skip both Step B and Step C (but density gate still applies silently)

## Step D: Batch Generation

### Output Directory Structure

```
[article-name]-illustrations/
├── shared/
│   └── design-tokens.css          ← Shared across all illustrations
├── 01-cover/
│   ├── data.js
│   ├── components/
│   │   └── CoverHero.jsx
│   └── App.jsx
├── 02-timeline/
│   ├── data.js
│   ├── components/
│   │   └── MilestoneTimeline.jsx
│   └── App.jsx
├── ...
├── 08-back-cover/
│   ├── data.js
│   ├── components/
│   │   └── BackCover.jsx
│   └── App.jsx
└── index.html                      ← Preview all illustrations in one page
```

### Generation Rules

1. **Shared design-tokens.css** — generated once, referenced by all
2. **Each illustration has its own data.js** — isolated, independently editable
3. **Component granularity** — same 80-line limit as single mode
4. **Naming convention** — `{NN}-{type}/` where NN is zero-padded sequence number
5. **index.html** — a single preview page showing all illustrations in order, for quick review

### WeChat Public Account Size Specs

| Illustration Type | Width | Height | Ratio | Usage |
|------------------|-------|--------|-------|-------|
| 封面 (cover) | 900px | 383px | 2.35:1 | 文章封面 |
| 正文配图 (body) | 640px | auto | flexible | 文章内嵌 |
| 金句图 (quote) | 640px | 640px | 1:1 | 文章内嵌/朋友圈 |
| 章节分隔 (divider) | 640px | 200px | ~3:1 | 章节间 |
| 封底 (back-cover) | 900px | 383px | 2.35:1 | 文章结尾 |

## Step E: Illustration Map

After generation, output the article ↔ illustration mapping:

```
🗺️ 配图地图

§1 导言 ─────────── 🖼️ 01-cover（封面）
§1 48天翻倍 ─────── 📊 02-timeline（里程碑时间线）
§2 Token经济学 ──── 🔗 03-logic-chain（论证链）
§2 内存墙 ───────── 📊 04-data-chart（HBM占比柱状图）
§3 内存更难造 ───── 🍩 05-donut（DRAM三巨头份额）
§4 供给紧张 ─────── 📊 06-bar-chart（HBM供需缺口）
§5 2000亿投资 ───── 📊 07-waterfall（投资+回购结构）
§6 个人故事 ─────── 💬 08-quote-card（金句：四个儿子）
全文 ────────────── 🖼️ 09-back-cover（封底）

📝 编辑指南：
- 修改数据 → 改对应目录的 data.js
- 修改配色 → 改 shared/design-tokens.css（全局生效）
- 修改单张风格 → 在该目录新建 local-tokens.css 覆盖
- 调整顺序 → 重命名目录编号
```

## Illustration Type Templates

### Cover (封面)

```jsx
// Layout: hero-center
// Content: thesis statement + author + source + date
// Size: 900×383
// Density: low (visual impact > information density)
// Required data: { thesis, author, source, date, accentText }
```

### Back Cover (封底)

```jsx
// Layout: center-stack
// Content: publication name + author + QR placeholder + CTA
// Size: 900×383
// Density: low (brand identity > information)
// Required data: { publicationName, author, qrPlaceholder, cta }
```

### Quote Card (金句图)

```jsx
// Layout: single-focus
// Content: one powerful quote + attribution + context hint
// Size: 640×640
// Density: medium (one idea, maximum impact)
// Required data: { quote, attribution, contextHint }
// Gate rule: quote must be impactful WITHOUT full article context
```

### Section Divider (章节分隔图)

```jsx
// Layout: hero-center
// Content: section number + section title + subtle decoration
// Size: 640×200
// Density: minimal (rhythm > information)
// Required data: { sectionNumber, sectionTitle }
// Gate rule: only for articles with 4+ clearly delineated sections
```

### Logic Chain (论证链)

```jsx
// Layout: flow-chart
// Content: causal chain with 3-6 nodes, each node = one claim
// Size: 640px wide
// Density: high (reveals structure invisible in prose)
// Required data: { nodes: [{ claim, evidence? }], connections: [{ from, to, label? }] }
// Gate rule: chain must have ≥3 nodes with clear causal/sequential relationship
```

## Anti-Patterns Specific to Multi-Illustration Mode

| Anti-Pattern | Detection | Fix |
|-------------|-----------|-----|
| **Forced quantity** | "Generate 10 illustrations" regardless of content | Remove fixed number; let content analysis determine count |
| **Filler illustrations** | Illustration with density score <9 | Skip or merge; only generate if user explicitly overrides |
| **Style drift** | Different palettes/fonts across illustrations | Enforce shared design-tokens.css |
| **Duplicate information** | Two illustrations showing the same data | Merge into one, or split by angle (e.g., same data as bar chart + donut chart = duplicate) |
| **Context-dependent quote** | Quote that makes no sense without the article | Skip; only use quotes that are independently impactful |
| **Over-illustration** | More illustrations than paragraphs | Maximum ratio: 1 illustration per 2 substantial paragraphs |
| **Under-illustration** | Article with 5+ data points but no data chart | Flag in Step B as "missed opportunity" |
