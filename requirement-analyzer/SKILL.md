---
name: requirement-analyzer
description: Requirement discovery and clarification skill for product managers. Use when the user provides a raw product idea, business request, customer feedback, meeting notes, feature brief, or vague requirement and wants to clarify goals, users, scenarios, scope, functional dependencies, data dependencies, states, permissions, edge cases, risks, metrics, or PRD handoff input.
---

# Requirement Analyzer

Use this skill to turn unclear product input into structured requirement analysis before PRD writing. The goal is to help the product manager think clearly, expose hidden dependencies, and prepare high-quality input for `prd-generator`.

Match the user's language by default. For Chinese requests, write Chinese headings and content unless the user asks for another language.

## Workflow Position

If the user is clarifying one roadmap item, feature idea, business request, or vague requirement, start here. If the user is planning multiple opportunities or releases, use `roadmap-planner` first. If the requirement is already clear enough to write, use `prd-generator`.

## Boundary

- Use `roadmap-planner` for product direction, opportunity pools, prioritization, version planning, and multi-initiative sequencing.
- Use `requirement-analyzer` for one roadmap item, feature idea, or requirement that needs clarification before PRD writing.
- Use `prd-generator` after the requirement is clear enough to become an executable PRD.
- Use `prototype-generator` after PRD creation to generate interactive prototypes and annotations.

## Task Types

- `Clarify`: ask focused questions because the current input is too vague.
- `Analyze`: produce structured requirement analysis from available information.
- `Deepen`: expand a known requirement with dependencies, states, edge cases, risks, and metrics.
- `Handoff`: prepare a structured brief for `prd-generator`.

Do not create roadmap-level plans or polished PRDs here. If the user asks for global product planning, use `roadmap-planner`. If the user asks for a complete PRD and the input is unclear, run this skill first, then hand off to `prd-generator`.

## Workflow

1. Identify the task type and available input.
   - Raw idea, business request, customer feedback, meeting note, feature brief, existing requirement, or partial PRD.
   - Note the request source when provided: business, user feedback, sales, customer success, operations, leadership, data, compliance, design, engineering, or internal team.

2. Decide whether to ask questions or proceed.
   - Ask up to 7 focused questions when missing answers would materially change scope, user flow, dependencies, data logic, permissions, or success metrics.
   - Ask first when two or more are unclear: target users, core goal, core workflow, scope boundary, upstream/downstream dependency, data source.
   - If enough context exists, proceed with labeled assumptions and open questions.
   - Never invent metrics, dates, staffing, user volumes, data sources, system dependencies, policy constraints, or stakeholder decisions as facts.

3. Analyze the requirement.
   - Read `references/analysis-framework.md` for normal analysis.
   - Focus on decision-changing information, not generic questionnaires.
   - Separate facts, assumptions, risks, dependencies, and open questions.
   - Make hidden dependencies explicit enough for product, design, engineering, QA, data, and operations to review.

4. Produce the output.
   - Read `references/handoff-template.md` for structured analysis or handoff.
   - Read `references/handoff-example.md` when preparing a PRD handoff for `prd-generator`.
   - Read `references/quality-checklist.md` for review or final quality checks.
   - End with `PRD 交接摘要` when the next step is PRD generation.

## Output Contract

For Chinese requests, use Chinese headings and labels.

For clarification-only tasks, return:

- 已理解的信息
- 关键缺口
- 最多 7 个澄清问题
- 每个问题会影响的后续 PRD/原型决策

For standard analysis, include:

- 需求理解
- 业务目标与成功指标
- 目标用户与核心场景
- 当前流程与目标流程
- 需求范围与非范围
- 功能上下游依赖
- 数据上下游依赖
- 状态流转与异常情况
- 角色与权限
- 业务规则与约束
- 埋点与指标
- 发布与运营影响
- 风险、假设与待确认问题
- PRD 交接摘要

For deepen tasks, include:

- 深化范围
- 新增或细化的功能依赖
- 新增或细化的数据依赖
- 新增或细化的状态、权限、异常和兜底
- 新增或细化的业务规则、指标和埋点
- 对 PRD 的影响
- 新增风险、假设与待确认问题

For `PRD 交接摘要`, include:

- 功能摘要
- 目标与非目标
- 目标用户与核心场景
- P0/P1/P2 范围建议
- 功能依赖摘要
- 数据与指标摘要
- 状态、异常与风险
- 待确认问题
- 建议 PRD 深度：`Lightweight`, `Standard`, or `Full`

## Quality Rules

- Prefer precise questions over broad questionnaires.
- Prioritize dependencies: workflow, data, permissions, integration, configuration, approval, and operations.
- Identify what changes upstream, what is consumed downstream, and who is affected.
- Treat unknowns as unknowns. Use `假设` or `待确认` rather than pretending certainty.
- If the requirement is already clear enough, do not over-question; provide analysis and move toward handoff.
