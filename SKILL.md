---
name: "react-design-draft"
version: "3.0.0"
category: "content-creation"
description: "Generate React design drafts (4-piece set) from content. Invoke for 'design draft'/'设计稿'/'生成页面'/'信息图'/'知识卡片'. Do NOT use for editing existing code."
metadata:
  requires_api_key: false
---

# React Design Draft Generator v3

Transforms user content into information-dense, visually refined React design drafts. Core advantage: **every element is independently editable, restructuring-capable, and version-controllable**.

## Task

Only generates React design drafts from content. Does NOT: write production apps, edit existing projects, or replace full development workflows.

## Execution Flow

```
User Content → Step 1: Parse & Match → Step 2: Confirm & Advise → Step 3: Generate → Step 4: Post-Generation Guide
```

### Step 1: Parse & Match

Read [`references/content-layout-mapping.md`](references/content-layout-mapping.md) for the three-dimension system.

1. **Check keyword shortcuts** — scan user input against [`references/style-presets.md`](references/style-presets.md). If a preset keyword matches, use that as defaults.
2. **Parse content structure** — extract: content type, key units count, density level.
3. **Auto-select three dimensions**: Layout × Style × Palette.
4. **Allow user override** — if user specifies any dimension explicitly, override that dimension only.

### Step 2: Confirm & Advise (MANDATORY)

Never skip. Present the selected combination AND adaptation advice before generating:

```
📐 Layout: <name> — <reason>
🎨 Style: <name> — <reason>
🎯 Palette: <name> — <reason>
📊 Density: <level> — <N> key units

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

Output: `design-tokens.css` + `data.js` + `components/*.jsx` + `App.jsx`

### Step 4: Post-Generation Guide (MANDATORY)

Always append after generation. This is the #1 advantage of React design drafts. See [`references/react-output-spec.md`](references/react-output-spec.md) "Interactive Edit Guide" section for the full template. Must include:

- **File Tree** with edit-responsibility annotations
- **Quick Edits** map (user intent → file → action)
- **Component Hierarchy** tree (editable structure)
- **Restructure hint**: tell user they can extract/refactor components

## Rules

1. **Three-dimension combination**: Layout × Style × Palette. See [`references/content-layout-mapping.md`](references/content-layout-mapping.md).
2. **Content-first**: Layout serves content structure. Every visual element carries information.
3. **Density = signal per pixel**: Minimum quality score 16/25. See [`references/density-standards.md`](references/density-standards.md).
4. **Data-driven**: All data in `data.js`. Components receive via props. Zero data in JSX.
5. **Design tokens as single source of truth**: All visual values reference CSS variables. No magic numbers.
6. **Anti-AI-slop**: See [`references/aesthetics-guide.md`](references/aesthetics-guide.md).
7. **Pre-generation consultation mandatory**: Always show planned combination + advice first.
8. **Post-generation edit guide mandatory**: Always output Component Map & Edit Guide.
9. **Component granularity**: Each visual concern = own component. Extract ComparisonBlock, StepList, QuestionList etc. Avoid monolithic components > 80 lines.
10. **Local-first fonts**: Prioritize local CJK fonts over web fonts. See [`references/aesthetics-guide.md`](references/aesthetics-guide.md) "Font Strategy" and "Local Font Registry".
