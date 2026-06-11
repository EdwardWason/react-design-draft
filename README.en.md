# React Design Draft Generator · Content → React Design 4-Piece Set

🇨🇳 中文版: [README.md](README.md)

[![Stars](https://img.shields.io/github/stars/EdwardWason/react-design-draft?style=flat-square)](https://github.com/EdwardWason/react-design-draft)
[![License](https://img.shields.io/badge/license-MIT--0-green?style=flat-square)](LICENSE)
[![ClawHub](https://img.shields.io/badge/ClawHub-react--design--draft-orange?style=flat-square)](https://clawhub.ai/skills/react-design-draft)
[![Skill](https://img.shields.io/badge/Claude%20Code-Skill-blue?style=flat-square)](SKILL.md)

[See it in action](#features) · [Get started](#30-second-start) · [Core mechanism](#core-mechanism) · [Limitations](#limitations) · [License](#license)

---

_"Translating your vague 'make it look good' into precise design parameters."_

---

**React Design Draft Generator** is not another AI illustration tool — it's a complete content-to-visual design system. It doesn't just generate images — it produces a set of **independently editable, freely restructurable, version-controllable** React design drafts. Every pixel is controlled by CSS variables. Every element lives in its own component file.

---

## Features

- 🎨 **Three-dimension system**: 25 layouts × 23 styles × 12 palettes, content-driven auto-matching
- 📐 **React 4-piece output**: design-tokens.css + data.js + components/*.jsx + App.jsx, every element independently editable
- 📊 **Density quantification**: 5-dimension 25-point scoring system, 10 anti-pattern red lines, ≥16 threshold
- 🎯 **Dual style system**: Editorial Magazine (serif + warm tones) vs Swiss International (sans + gray-white + single high-saturation accent) — one deck, one style, no mixing
- 🖼 **Multi-illustration mode**: Auto-extract visualizable units from long-form articles, batch-generate covers + quote cards + infographics + logic chains, density gate ensures every illustration earns its screen space
- 🤖 **Master Mode**: Say "surprise me" or "you decide" to skip all confirmation points, fully automated from parsing to generation
- 🔒 **Aesthetic guardrails**: Protect beauty over freedom — Swiss mode locked to 4 accent palettes, Editorial mode locked to warm color systems, no custom hex allowed
- 📝 **Post-generation edit guide**: File tree + quick edit map + component hierarchy, showcasing React's targeted editing advantage
- 🔤 **The Larger, The Lighter**: Large text uses lighter weights (200-400), small text uses heavier weights (500-650) — 100 years of magazine typography, validated

## When to Use / When Not To

✅ **Use when**
- Turning articles/data/opinions into high-density infographics or knowledge cards
- A long-form article needs a full illustration set (cover + body + quote cards)
- You need editable, restructurable design drafts (not a "dead image")
- You prioritize information density over visual spectacle
- You want magazine-grade layout but don't know design software

❌ **Don't use when**
- Full article typesetting (use md2wechat-skill or Kami)
- Video/motion graphics
- Pure image editing with no content extraction or layout
- Fan/celebrity content (requires a completely different visual language)
- Hard-sell advertising (violates the "content-first" design philosophy)
- Tutorials exceeding 15 illustration cards (illustration cards are not the optimal carrier for long tutorials)

## 30-Second Start

```bash
# ClawHub install (recommended)
clawhub install react-design-draft

# Or manual install
git clone https://github.com/EdwardWason/react-design-draft.git
```

In TRAE / Claude Code / any Agent platform, just say:

```
Turn this article into a high-density infographic
```

```
Create a knowledge card in Kami editorial style
```

```
Generate full illustrations for this long-form article
```

## Common Use Cases

| Scenario | Recommended Mode | Trigger |
|----------|-----------------|---------|
| Want an infographic but don't know design | Master Mode | "Surprise me, turn this into an infographic" |
| WeChat article illustrations | Multi-Illustration | "Generate full illustrations for this article" |
| Single knowledge card | Single Draft | "Turn this into a knowledge card" |
| Comparison analysis | Single Draft | "Compare A and B, generate a design draft" |
| Kami editorial premium feel | Style override | "Use Kami style for this strategy report" |
| Swiss minimal layout | Style override | "Use Swiss style for this data page" |

## Usage

### Three Modes

```
User input
    │
    ├── Says "surprise me"/"you decide"/"just do it"?
    │   → Master Mode (fully automated)
    │
    ├── Contains "multi"/"illustrations"/"full set"?
    │   → Multi-Illustration Mode (batch generation)
    │
    └── Otherwise?
        → Single Draft Mode (single interactive draft)
```

### Workflow

```
Content → Brand config → Parse & match → Confirm & advise → Generate 4-piece set → Edit guide
```

1. **Brand config**: Four-layer priority (user specified → Brand DNA auto-detect → personal brand profile → auto-match)
2. **Parse & match**: Parse content structure, auto-match Layout × Style × Palette
3. **Confirm & advise**: Replace 23 styles × 12 palettes with 3 simple questions (tone → impression → color)
4. **Generate 4-piece set**: design-tokens.css + data.js + components/*.jsx + App.jsx
5. **Edit guide**: File tree + quick edit map + component hierarchy

### Keyword Triggers

| Keyword | Preset |
|---------|--------|
| knowledge card / key points | knowledge-card |
| comparison / vs / PK | versus |
| infographic / visualization | infographic |
| Kami / editorial | kami-report |
| high-density / dense | dense-info |
| magazine / layout | magazine |

## Example Requests

```
User: "Turn this deep learning survey into an infographic"

Agent: Parsed 8 visualizable units. Recommending:
- Cover: Editorial — warm gray bg + serif display
- Core concept: Swiss — IKB Blue accent
- Comparison table: Editorial — parchment bg
Confirm to generate?
```

```
User: "Surprise me, generate full illustrations for this product postmortem"

Agent: [Auto-parse → Auto-match → Batch generate → Output illustration map]
Generated 6 illustrations: cover + 3 infographics + quote card + back cover
```

## Directory Structure

```
react-design-draft/
├── SKILL.md                              # Agent workflow definition
├── README.md                             # Chinese docs
├── README.en.md                          # English docs
├── CHANGELOG.md                          # Version history (v3.0.0 → v5.3.0)
├── LICENSE                               # MIT-0
├── .claude-plugin/
│   └── plugin.json                       # Claude Code metadata
└── references/                           # Reference docs
    ├── content-layout-mapping.md         # 3-dimension system + 25 layouts
    ├── aesthetics-guide.md               # 23 styles + 12 palettes + aesthetic philosophy
    ├── density-standards.md              # 5-dimension scoring + 48 anti-patterns
    ├── react-output-spec.md              # React 4-piece output spec
    ├── style-presets.md                  # 29 quick presets + keyword mapping
    ├── chart-system.md                   # 14 chart types
    ├── brand-profile.md                  # 4-layer brand config
    ├── multi-illustration.md             # Multi-illustration full spec
    └── image-sources.md                  # Image sources + screenshot styling
```

## Core Mechanism

### Three-Dimension System

| Dimension | Options | Examples |
|-----------|---------|---------|
| **Layout** | 25 | Enumeration, comparison, process, data, hierarchy, timeline, mixed |
| **Style** | 23 | Professional/Editorial/Hand-crafted/Digital/Playful/Elegant, 6 categories |
| **Palette** | 12 | kami-parchment, dark, brand colors, etc. |

5,086 total combinations, content-driven auto-matching. Users never need to manually select.

### Dual Style System

| Dimension | Editorial Magazine | Swiss International |
|-----------|-------------------|---------------------|
| **Font** | Serif, locked at 500 | Sans-serif |
| **Color** | Warm tones, parchment base | Gray-white + 4 accent palettes (IKB / Lemon Yellow / Lemon Green / Safety Orange) |
| **Layout** | Atmospheric, magazine composition | Grid system, minimal precision |
| **Gray scale** | 7-step warm gray (no cool blue-grays) | 5-step calibrated premium gray |

### Three Aesthetic Constraints

- **Restraint**: Brand color ≤ 5% area, single-color principle
- **Breathing**: Whisper shadows, 0.5pt borders, 8pt border-radius
- **Warmth**: Warm gray system replaces all cool blue-grays, no pure white backgrounds

### Density Gate

5-dimension scoring (single draft ≥16/25, multi-illustration per-card ≥9/15):

| Dimension | Max | Core Question |
|-----------|-----|---------------|
| Data density | 5 | How many actionable information points does this card convey? |
| Visual hierarchy | 5 | Can the reader find the visual entry point within 3 seconds? |
| Color efficiency | 5 | Is color conveying information or just decoration? |
| Typographic precision | 5 | Do weight, size, and spacing have semantic分工? |
| Information completeness | 5 | Can this be understood when viewed independently? |

## Theme Presets

### Editorial (5 sets)

| Theme | Background | Brand Color | Use Case |
|-------|-----------|-------------|----------|
| Parchment | `#faf9f5` | `#8b4513` | Deep observation, culture |
| Ivory | `#faf8f5` | `#c41e3a` | Tech products, data research |
| Warm Sand | `#f7f4ed` | `#2d5a27` | Career advice, book notes |
| Ink Wash | `#f5f0e8` | `#1a1a2e` | Interviews, opinion pieces |
| Washi | `#faf7f2` | `#3d5a80` | Travel, tutorials |

### Swiss (4 sets)

| Accent | Hex | Background | Use Case |
|--------|-----|------------|----------|
| IKB Blue | `#0033FF` | `#fafaf8` | Tech, data, logic |
| Lemon Yellow | `#E8FF00` | `#fafaf8` | Creative, comparison, highlight |
| Lemon Green | `#00FF41` | `#fafaf8` | Growth, positive, nature |
| Safety Orange | `#FF5F00` | `#fafaf8` | Warning, risk, high attention |

## Limitations

- **Not a full typesetting tool**: React design drafts excel at "one point per card", not continuous 3000+ word text layout
- **Not production-grade React**: Output is designed for local preview and screenshot, not deployable production code
- **Requires an Agent platform**: This Skill has no GUI — it runs in TRAE / Claude Code / Codex or similar Agent environments
- **Fonts depend on local environment**: The local-first font strategy means missing fonts fall back to web fonts, which may differ visually
- **Learning curve**: While Master Mode is zero-friction, deep customization (editing React components) requires basic React/CSS knowledge

## Core Design Principles

1. **Content-driven, not template-driven**: Layout serves content structure, not the other way around
2. **Every pixel justifies itself**: No pure decoration — every visual choice must carry information or purpose
3. **Protect beauty over freedom**: Restrict color systems, lock typography rules, to prevent "just tweak this one thing" aesthetic collapse
4. **React is a means, not an end**: React was chosen for its componentization and editability, not because it's frontend best practice
5. **Information density is the real currency**: In an era with no print approval and no printing costs, density is the true luxury

## FAQ

**Q: Why React instead of HTML?**
A: The React 4-piece set (tokens + data + components + App) naturally supports data-driven design, component reuse, and targeted editing. Changing a number doesn't require hunting for classNames across the file. Changing a component doesn't require rewriting the entire page.

**Q: Can I deploy the generated code directly?**
A: Not recommended. The output is a "previewable visual draft" meant for screenshots and stakeholder confirmation. Production deployment requires additional frontend engineering.

**Q: How do I choose between Swiss and Editorial?**
A: Content "tone" determines the style — rational, data-heavy, logical content fits Swiss; emotional, narrative, atmospheric content fits Editorial. When unsure, ask: would this topic look better in WIRED or The Economist?

**Q: Will editing my design draft's CSS affect future generations?**
A: No. Each generation is independent and doesn't read your previous edits. To persist style preferences, use brand configuration (`~/.config/react-design-draft/brand.md`).

**Q: How is the number of illustrations determined in multi-illustration mode?**
A: By the number of extractable visualizable units in the content, not a fixed template. The density gate (≥9/15) ensures every illustration earns its screen space.

---

## License

MIT-0 © 2026