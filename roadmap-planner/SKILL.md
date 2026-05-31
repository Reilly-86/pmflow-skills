---
name: roadmap-planner
description: Product roadmap and planning skill for product managers. Use when the user asks to create, review, prioritize, or refine a product roadmap, 产品规划, 版本规划, quarterly plan, release plan, opportunity map, product strategy, initiative sequencing, prioritization, milestones, or global product planning before individual requirements and PRDs.
---

# Roadmap Planner

Use this skill for product-level planning before individual requirement analysis and PRD writing. The goal is to turn product strategy, business goals, user problems, opportunity ideas, and constraints into a prioritized roadmap with clear stages, tradeoffs, dependencies, and next-step requirement candidates.

Match the user's language by default. For Chinese requests, write Chinese headings and content unless the user asks for another language.

## Workflow Position

If the user is planning across multiple opportunities, releases, product areas, or quarters, start here. If the user already has one concrete feature or requirement, use `requirement-analyzer` instead.

## Boundary

- Use `roadmap-planner` to decide **what to do, why, when, and in what order** across multiple opportunities, initiatives, or releases.
- Use `requirement-analyzer` to clarify **one roadmap item or requirement** before PRD writing.
- Use `prd-generator` to write **one concrete requirement or feature** into an executable PRD.
- Use `prototype-generator` after PRD creation to generate **interactive HTML prototypes and annotations**.

Do not write detailed feature PRDs here. When a roadmap item is ready for detail, end with a `Requirement Analyzer Handoff` for `requirement-analyzer`.

## Task Types

- `Strategy`: clarify product direction, goals, users, positioning, and success metrics.
- `Opportunity Map`: organize user problems, business opportunities, and solution ideas.
- `Prioritize`: rank initiatives or requirements using explicit criteria.
- `Roadmap`: create quarterly/monthly/release-based plans and milestones.
- `Review`: evaluate an existing roadmap for focus, sequencing, dependencies, risk, and feasibility.
- `Handoff`: prepare selected roadmap items for `requirement-analyzer`.

## Workflow

1. Identify planning scope.
   - Product, business line, module, platform, growth area, internal system, or feature family.
   - Planning horizon: quarter, half-year, year, release train, MVP phase, or custom period.
   - Audience: product, design, engineering, data, operations, sales, customer success, leadership.
2. Gather or infer planning inputs.
   - Product vision and current stage
   - Business goals and user goals
   - Target users, segments, and key scenarios
   - Current problems and opportunity pool
   - Metrics, constraints, resources, deadlines, dependencies
   - Existing initiatives, commitments, risks, and known decisions
3. Decide whether to ask questions or proceed.
   - Ask up to 7 focused questions when missing answers would materially change strategy, prioritization, sequencing, or feasibility.
   - Ask first when two or more are unclear: planning horizon, target users, business goal, key metric, resource constraint, committed initiative.
   - If enough context exists, proceed with labeled assumptions and open questions.
   - Never invent revenue targets, user numbers, dates, team capacity, budgets, dependencies, or stakeholder commitments as facts.
4. Analyze and prioritize.
   - Read `references/roadmap-framework.md` for roadmap structure and planning dimensions.
   - Read `references/prioritization-methods.md` for prioritization methods.
   - Make tradeoffs explicit: why now, why not now, what is deferred, and what depends on what.
5. Produce the output.
   - Read `references/roadmap-template.md` for roadmap drafts.
   - Read `references/handoff-example.md` when preparing roadmap items for `requirement-analyzer`.
   - Read `references/quality-checklist.md` for review or final checks.
   - End with `Requirement Analyzer Handoff` for roadmap items that should enter detailed requirement clarification.

## Output Contract

For Chinese requests, use Chinese headings and labels.

For strategy tasks, include:

- 产品阶段与背景
- 目标用户与核心场景
- 产品定位
- 北极星指标
- 阶段目标
- 核心假设
- 主要机会方向
- 战略取舍
- 风险与待确认问题
- 下一步机会池 / Roadmap 建议

For roadmap creation, include:

- 产品方向与规划背景
- 规划周期与目标
- 用户分层与核心场景
- 机会池 / 需求池
- 优先级评估
- Roadmap 阶段规划
- 关键里程碑
- 资源、依赖与约束
- 风险、取舍与待确认问题
- 下一步与 Requirement Analyzer Handoff

For roadmap review, lead with findings:

- `阻塞 Blocking`: prevents planning approval or execution
- `重要 Major`: likely to cause wrong sequencing, resource conflict, or missed goals
- `次要 Minor`: clarity, granularity, or communication issue
- `建议 Suggestion`: optional improvement

For each selected roadmap item handoff, include:

- 项目/机会摘要
- 目标用户与核心场景
- 业务目标与成功指标
- 推荐优先级与原因
- 已知范围与非范围
- 关键依赖与约束
- 主要风险与待确认问题

## Quality Rules

- Roadmaps should communicate intent and sequencing, not a promise that every date is fixed.
- Prioritize by value, urgency, confidence, effort, dependencies, and strategic fit.
- Separate committed work, planned work, and exploratory opportunities.
- Include rationale for deferring important work.
- Prefer a small number of coherent initiatives over a scattered feature list.
- Treat unknowns as unknowns. Use `假设` or `待确认` rather than pretending certainty.
