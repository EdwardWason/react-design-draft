# Changelog

All notable changes to this project will be documented in this file.

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
