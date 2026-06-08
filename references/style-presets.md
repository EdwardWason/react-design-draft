# Style Presets (Quick Shortcuts)

Pre-configured Layout × Style × Palette combinations for common use cases. User can invoke by name or keyword.

## Preset Library

### Knowledge & Education

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **knowledge-card** | 知识卡片、干货、要点 | grid-cards | hand-drawn-edu | warm |
| **checklist** | 清单、待办、步骤 | step-flow | minimal | cool |
| **concept-map** | 概念图、思维导图 | hub-spoke | craft-handmade | warm |
| **study-guide** | 学习指南、复习 | grid-cards | chalkboard | dark |
| **classroom** | 课堂、教学、培训 | bento-grid | hand-drawn-edu | warm |

### Comparison & Analysis

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **versus** | 对比、PK、优劣 | binary-comparison | bold-editorial | duotone |
| **swot** | SWOT、四象限 | comparison-matrix | corporate-memphis | cool |
| **pro-con** | 优缺点、正反 | split-comparison | minimal | mono |

### Data & Dashboard

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **metrics** | 指标、KPI、数据 | dashboard | ui-wireframe | cool |
| **leaderboard** | 排行榜、排名 | grid-cards | bold-graphic | vivid |
| **report** | 报告、报表 | dense-modules | editorial-infographic | elegant |

### Process & Flow

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **roadmap** | 路线图、规划 | winding-roadmap | technical-schematic | cool |
| **pipeline** | 管道、漏斗、转化 | funnel | corporate-memphis | cool |
| **cycle** | 循环、闭环、迭代 | circular-flow | technical-schematic | dark |
| **journey** | 旅程、体验、故事 | story-mountain | storybook-watercolor | warm |

### Architecture & System

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **architecture** | 架构、系统、组件 | isometric-map | technical-schematic | dark |
| **stack** | 技术栈、层级 | hierarchical-layers | technical-schematic | cool |
| **breakdown** | 拆解、分解、剖析 | structural-breakdown | craft-handmade | warm |

### Visual & Creative

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **infographic** | 信息图、可视化 | bento-grid | pop-laboratory | vivid |
| **poster** | 海报、宣传、展示 | dense-modules | bold-editorial | duotone |
| **magazine** | 杂志、排版、编辑 | bento-grid | editorial-infographic | elegant |
| **retro** | 复古、怀旧、年代 | timeline | retro-pop-grid | retro |
| **cute** | 可爱、萌、卡哇伊 | grid-cards | kawaii | macaron |
| **dark-tech** | 暗黑、科技、赛博 | dense-modules | cyberpunk-neon | dark |

### High-Density Specials

| Preset Name | Keywords | Layout | Style | Palette |
|-------------|----------|--------|-------|---------|
| **dense-info** | 高密度信息大图、密集 | dense-modules | morandi-journal | warm |
| **one-pager** | 一页纸、总览、全貌 | dense-modules | editorial-infographic | elegant |
| **cheat-sheet** | 速查表、备忘录 | periodic-table | technical-schematic | cool |
| **kami-report** | 纸墨风、Kami、雅致、财报 | grid-cards or bento-grid | kami-editorial | kami-parchment |
| **kami-long-doc** | 长文档、排版、阅读 | step-flow or timeline | kami-editorial | kami-parchment |

## How Presets Work

1. **User mentions a keyword** (e.g., "帮我做一个知识卡片")
2. **Match to preset** → knowledge-card → grid-cards + hand-drawn-edu + warm
3. **Apply preset as defaults**, but allow user override
4. **If no preset matches**, fall back to the three-dimension auto-selection logic

## Custom Override

User can override any dimension of a preset:

```
"用赛博朋克风格做知识卡片" → knowledge-card preset, but style overridden to cyberpunk-neon
"高密度信息图，用暗色方案" → dense-info preset, but palette overridden to dark
```

Override format: `--layout <name> --style <name> --palette <name>`
