# 简历更新 - AI 探索经历

## What This Is

在简历的商城营销活动方向负责人板块最上方，新增一条"AI 探索"经历。展示在字节跳动电商团队中推动 AI 能力建设的实践，包括创建 AI Skill 实现自动化操作、降低平台操作门槛、提升研发效率。

## Core Value

用一条精准的简历条目，突出 AI 实践能力和业务价值——AI Skill 累计下载 10736 次，用自动化取代手动平台操作。

## Requirements

### Validated

- ✓ 现有简历结构和内容完整 — existing
- ✓ 代码库结构已映射 — existing (`.planning/codebase/`)

### Active

- [ ] **AI-01**: 在商城营销活动方向负责人板块中，最上方新增 AI 探索条目
- [ ] **AI-02**: 条目包含三个核心职责：创建 AI Skill、自动化操作内部平台、降低门槛提升效率
- [ ] **AI-03**: 条目包含量化数据：AI Skill 累计下载 10736 次
- [ ] **AI-04**: 新增内容与现有 LaTeX 格式和风格保持一致（\textcolor、\textbf 等）

### Out of Scope

- 修改简历其他部分的内容 — 聚焦仅新增 AI 探索条目
- 修改简历整体结构或布局 — 不改动现有 section 划分

## Context

- 简历使用 moderncv + ctex，单文件 `main.tex`（144 行）
- AI Skill 具体功能：自动完成框架分支代码生成，生成完成后通知用户更新依赖，使用 skill 自动操作取代平台手动操作
- 位置：`工作经历 → 字节跳动中国电商 → 商城营销活动方向负责人 → 最上方子项`

## Constraints

- **Format**: 必须使用现有的 `\item` + `\textcolor[RGB]{64,127,191}{...}` 风格
- **Language**: 中文为主，英文技术术语保留
- **Length**: 新增内容精炼，不显著增加简历篇幅

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| 放在活动方向负责人最上方 | AI 探索是最新重点方向，优先展示 | — Pending |
| 使用现有格式风格 | 保持简历视觉一致性 | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd:transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd:complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: 2026-04-08 after initialization*
