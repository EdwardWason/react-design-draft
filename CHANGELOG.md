# Changelog

All notable changes to this project will be documented in this file.

## [4.2.0] - 2026-06-09

### Added
- **3 knowledge card sub-types**: rule-card, checklist-card, cheatsheet-card
  - rule-card: numbered rules + violation consequence (e.g., "三条铁律")
  - checklist-card: items + severity markers (e.g., "7条安全红线")
  - cheatsheet-card: name + example pairs, ultra-compact (e.g., "B1-B6访谈规则")
- **3 logic visualization sub-types**: logic-chain, process-pipeline, version-timeline
  - logic-chain: causal reasoning (A导致B导致C)
  - process-pipeline: phase-based pipeline with input/output (Phase 0→1→2)
  - version-timeline: iteration history (v1→v2→v3)
- **Cover/back-cover density gate exemption**: threshold lowered to ≥6/15 (vs ≥9/15 for other types)
  - Rationale: cover/back-cover value is brand identity, not information density

### Changed
- Version bumped from 4.1.0 to 4.2.0
- multi-illustration.md: logic-chain template expanded into 3 distinct types with selection guide
- multi-illustration.md: quote-card section expanded with 4 sub-type templates + selection guide

## [4.1.0] - 2026-06-09

### Added
- **Multi-Illustration Mode**: Generate multiple illustrations for a single article
  - Step A: Article parsing (extract thesis, data, logic chains, quotes, comparisons)
  - Step B: Illustration plan + density scoring (3-dimension 15-point gate, ≥9/15 to generate)
  - Step C: Style unification confirmation (shared design-tokens.css across all illustrations)
  - Step D: Batch generation (shared tokens + per-illustration data/components)
  - Step E: Illustration map (article section ↔ illustration mapping)
  - Two mandatory confirmation points: content plan + style plan
  - Content drives quantity, not templates
  - Every illustration independently passes density gate
- **5 new illustration templates**: cover, back-cover, quote-card, section-divider, logic-chain
- **WeChat public account size specs**: 封面 900×383, 正文 640px, 金句 640×640
- **Multi-illustration anti-patterns**: forced quantity, filler illustrations, style drift, duplicate info
- Mode detection: "多图"/"配图"/"全套"/"文章配图" triggers Multi-Illustration Mode
- Rules #14 and #15 added for multi-illustration content-driven quantity and density gate

### Changed
- Version bumped from 4.0.0 to 4.1.0
- SKILL.md restructured: Mode Detection section + Single Draft Mode + Multi-Illustration Mode
- Rule #3 updated: density threshold now differentiates single mode (≥16/25) vs multi mode (≥9/15)

## [4.0.0] - 2026-06-08

### Added
- **Chart system** (P0): 14 chart types with auto-selection decision tree + CSS/SVG implementation specs
  - bar-chart, horizontal-bar-chart, line-chart, donut-chart, quadrant-chart
  - flow-chart, swimlane-chart, state-machine, tree-chart, layered-diagram
  - venn-diagram, candlestick-chart, waterfall-chart, treemap
- **Brand Profile system** (P0): Four-layer brand configuration with priority resolution
  - Layer 1: Explicit prompts (highest)
  - Layer 2: Brand DNA auto-detection
  - Layer 3: User brand profile (`~/.config/react-design-draft/brand.md`)
  - Layer 4: Three-dimension auto-selection (lowest)
  - Project style scanning (CSS/tailwind/tokens extraction)
- **Kami Full Token System** (P1): 20+ CSS variables replacing simplified 3-variable kami-parchment
  - Brand: --kami-brand, --kami-brand-light
  - Surfaces: --kami-parchment, --kami-ivory, --kami-warm-sand, --kami-dark-surface, --kami-deep-dark
  - Text: --kami-near-black, --kami-dark-warm, --kami-olive, --kami-stone
  - Borders: --kami-border, --kami-border-soft
  - Derivatives: --kami-brand-tint, --kami-tag-bg, --kami-breaking-bg, --kami-breaking-fg
- **Extended Anti-Patterns** (P1): 7 categories, 38 rules (up from 10 red lines)
  - Content Hollow (#1-5), Metric Fraud (#6-10), Structural Mimicry (#11-15)
  - Visual Excess (#16-19), Source Missing (#20-23), Tone Pollution (#24-29)
  - CJK & Layout Specific (#30-38)
- **Writing quality gate** (P1): Assertion-evidence, Impact formula, data-over-adjectives, no-AI-officialese
- **Document type presets** (P2): 9 Kami-inspired templates
  - one-pager-doc, long-doc, letter, portfolio, resume, equity-report, changelog, landing-page, slides
- **Multi-language font stacks** (P2): Japanese (YuMincho) and Korean (Source Han Serif K)
- **Slide scaling formula** (P2): Macro ×1.6, Micro ×0.5, with 7 property-specific rules
- Step 0: Brand Profile added to execution flow
- SKILL.md Rules expanded from 10 to 13 (added #11 Brand profile, #12 Chart auto-selection, #13 Writing quality gate)

### Changed
- Version bumped from 3.0.0 to 4.0.0
- Execution flow: 4 steps → 5 steps (added Step 0: Brand Profile)
- Step 1 now includes chart needs detection and content quality pre-check
- Step 2 Confirm & Advise now includes chart type recommendation
- Step 3 now references chart-system.md

## [3.0.0] - 2026-06-08

### Added
- Three-dimension combination system: Layout × Style × Palette (5,086 combinations)
- 25 layout patterns covering enumeration, comparison, process, data, hierarchy, timeline, and mixed content
- 23 visual styles across 6 categories (Professional, Editorial, Hand-crafted, Digital, Playful, Elegant)
- 12 color palettes including kami-parchment
- 7 font presets with local-first CJK font strategy
- 11 local font registry entries (汇文明朝体, 宋徽宗瘦金体, 仓耳今楷02, etc.)
- 29 quick presets with keyword trigger mapping
- 5-dimension density scoring system (25-point scale, ≥16 threshold)
- 10 density anti-pattern red lines
- Kami Ten Invariants for kami-editorial style
- Pre-generation consultation (Step 2: Confirm & Advise)
- Post-generation edit guide (Step 4: mandatory)
- Component granularity rules (≤80 lines, 5 extraction triggers)
- Interactive edit matrix (13 user intents → file → action)
- Agent platform edit workflow comparison (React vs image design drafts)
- React 4-piece output specification (design-tokens.css / data.js / components/*.jsx / App.jsx)

### Changed
- Font strategy from Web-first to Local-first, Web-fallback
- Step 2 upgraded from "Confirm" to "Confirm & Advise" with adaptation advice
- Step 4 added as mandatory Post-Generation Guide

### Fixed
- SKILL.md frontmatter: added version, category, metadata.requires_api_key
- Description trimmed to ≤150 characters
- Style → Font mapping completed for all 23 styles (was missing 8)
