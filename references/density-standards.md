# Information Density Quantification Standards

## Core Principle

**Density = Signal per Pixel**. High density means more useful information per unit of visual space, NOT more visual noise.

## Density Scoring

For each design draft, evaluate on these 5 dimensions (each 1-5 points):

### 1. Content Utilization Rate

| Score | Standard |
|-------|----------|
| 1 | < 30% of viewport carries information, rest is decoration |
| 2 | 30-50% content, significant empty decoration |
| 3 | 50-70% content, balanced whitespace |
| 4 | 70-85% content, purposeful whitespace only |
| 5 | > 85% content, every pixel serves a purpose |

### 2. Information Hierarchy Clarity

| Score | Standard |
|-------|----------|
| 1 | Flat structure, no visual distinction between levels |
| 2 | 2 levels distinguishable (title vs body) |
| 3 | 3 levels clear (title → subtitle → body) |
| 4 | 4+ levels with consistent scale system |
| 5 | 4+ levels + visual encoding (color/size/weight/position) maps to importance |

### 3. Data-Ink Ratio (Tufte)

| Score | Standard |
|-------|----------|
| 1 | > 60% of visual elements are non-informational (borders, backgrounds, decorations) |
| 2 | 40-60% non-informational ink |
| 3 | 25-40% non-informational ink |
| 4 | 10-25% non-informational ink |
| 5 | < 10% non-informational ink, every line/shade carries meaning |

### 4. Scanning Efficiency

| Score | Standard |
|-------|----------|
| 1 | User must read everything to find key info |
| 2 | Key info identifiable with effort |
| 3 | Key info findable within 3 seconds |
| 4 | Key info immediately visible, hierarchy guides eye naturally |
| 5 | F-pattern/Z-pattern optimized, key info in expected positions |

### 5. Whitespace Purposefulness

| Score | Standard |
|-------|----------|
| 1 | Random or excessive whitespace |
| 2 | Whitespace exists but inconsistent |
| 3 | Consistent spacing system (4/8px grid) |
| 4 | Whitespace creates clear grouping (proximity principle) |
| 5 | Whitespace is an active design element — creates rhythm, emphasis, and breathing |

## Minimum Quality Threshold

**Total score must be ≥ 16/25** for a design draft to be acceptable.

If score < 16, identify the weakest dimension and improve before outputting.

## Density Anti-Patterns (Red Lines)

These patterns indicate density has crossed into clutter. **Any one = reject and fix**:

| Anti-Pattern | Detection Rule |
|-------------|---------------|
| **Card nesting > 2 levels** | Card inside card inside card = visual noise |
| **> 3 font sizes in one card** | Indicates hierarchy failure |
| **> 4 colors used as accents** | Color coding loses meaning beyond 4 |
| **Horizontal scrolling required** | Content overflow = layout failure |
| **Text < 12px** | Readability threshold violated |
| **Line height < 1.4** | Cramped text = unreadable at high density |
| **> 2 box-shadow layers** | Depth illusion becomes noise |
| **Border + background + shadow on same element** | Triple emphasis = no emphasis |
| **Icon + emoji + badge on same line** | Visual overload |
| **Grid gap < 8px** | Elements merge visually |

## Spacing System

Use a consistent spacing scale based on 4px:

```
4px  — micro (icon-to-label)
8px  — tight (badge-to-text)
12px — compact (list items)
16px — standard (card padding)
24px — comfortable (section gap)
32px — generous (major section)
48px — spacious (page sections)
64px — expansive (hero spacing)
```

**Rule**: Only use values from this scale. No arbitrary margins.

## Typography Scale

```
12px / 1.4 — caption, metadata, timestamps
14px / 1.5 — body text, descriptions
16px / 1.5 — large body, lead text
20px / 1.4 — subtitle, card titles
24px / 1.3 — section headings
32px / 1.2 — page headings
48px / 1.1 — hero titles
```

**Font weight mapping**:
- 400: body, descriptions
- 500: labels, badges
- 600: subtitles, card titles
- 700: headings
- 800: hero titles

## Grid System

- **Base unit**: 4px
- **Column count**: 12-column grid
- **Gutter**: 16px (compact) / 24px (standard) / 32px (spacious)
- **Max content width**: 1200px
- **Breakpoints**: 640px / 768px / 1024px / 1280px
