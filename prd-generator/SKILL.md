---
name: prd-generator
description: Product requirements document (PRD) generation, optimization, and review skill. Use when the user asks to create, write, improve, review, or turn rough ideas into a PRD, 产品需求文档, functional specification, feature requirements, user stories, acceptance criteria, MVP scope, roadmap-ready requirements, or product brief.
---

# PRD Generator

Use this skill to create, improve, or review PRDs. Optimize for product clarity, decision usefulness, and testable requirements rather than mechanically filling a template.

## Workflow Position

Use this skill when a requirement is clear enough to become an executable PRD. If the user is still planning product direction or releases, use `roadmap-planner`. If the user has a vague feature idea or dependency-heavy request, use `requirement-analyzer` first.

## Boundary

- Use `roadmap-planner` for product strategy, roadmap, opportunity prioritization, and release sequencing.
- Use `requirement-analyzer` before PRD writing when the input is vague, dependency-heavy, or missing users, goals, scope, workflow, data, permissions, or success metrics.
- Use `prd-generator` when the requirement is clear enough to write, optimize, or review an executable PRD.
- Use `prototype-generator` after PRD creation to generate interactive HTML prototypes and annotations.

## Task Types

- `Create`: turn an idea, brief, notes, transcript, feature request, or rough scope into a structured PRD.
- `Optimize`: rewrite or reshape an existing PRD while preserving the user's intent.
- `Review`: evaluate an existing PRD and return prioritized issues, gaps, and recommended edits.
- `Outline`: produce a PRD skeleton, section plan, or question list without writing a full PRD.

## Workflow

1. Identify the task type and output target.
   - If the user asks for review, do not rewrite the whole PRD unless asked.
   - If the user asks for a draft, produce a usable first version with assumptions.
   - Write a file only when the user explicitly asks to save/export it, or when the task is clearly inside a repository/documentation workflow.
   - If the user is discussing, brainstorming, or reviewing without asking to save changes, respond in chat first.
   - Match the user's language by default. For Chinese requests, write Chinese section headings and PRD content unless the user asks for another language.

2. Gather the minimum viable context.
   - Product or feature name
   - Target users and primary scenarios
   - Problem, goal, and success metrics
   - In-scope features and explicit non-goals
   - Platform, constraints, timeline, stakeholders, and dependencies when relevant

3. Decide whether to ask questions or proceed.
   - Check input sufficiency before drafting. If two or more are missing among target users, success metrics, and scope boundary, recommend using `requirement-analyzer` first.
   - If the user asks to proceed anyway, draft with labeled assumptions and open questions instead of blocking.
   - Ask up to 5 focused questions if missing information would materially change scope, users, or success criteria.
   - Ask before drafting when two or more of these are unknown: target users, core problem, business/user goal, scope boundary.
   - Proceed with an `Assumptions` section when enough context exists or the user wants speed.
   - Never invent market data, dates, budgets, staffing, metrics, competitors, or technical constraints as facts. Mark them as assumptions, placeholders, or open questions.

4. Choose the PRD depth.
   - `Lightweight`: small feature, MVP, experiment, early idea, or decision memo.
   - `Standard`: normal product feature or cross-functional project.
   - `Full`: large initiative with launch plan, technical dependencies, risks, milestones, and acceptance strategy.
   - Read `references/prd-structure.md` when depth, sections, or scope are ambiguous.

5. Draft, optimize, or review.
   - Read `references/prd-template.md` for full drafts.
   - Read `references/prd-example.md` when the user asks for a complete PRD and output style needs a concrete example.
   - Read `references/handoff-example.md` when preparing PRD content for `prototype-generator`.
   - Read `references/quality-checklist.md` for review or final checks.
   - When the user explicitly asks for evaluation, scoring, quality level, or readiness, use the weighted scorecard in `references/quality-checklist.md`.
   - Keep sections that add decision value; omit or mark not applicable sections that would become filler.

6. Produce the output.
   - Default format: Markdown.
   - Respond in chat unless the user asks to save/export, or the task is clearly inside a repository/documentation workflow.
   - If saving a new PRD, default to `docs/prd-{product-or-feature-name}.md` using a filesystem-safe lowercase filename.
   - If responding in chat, keep the structure readable and include assumptions/open questions.
   - When writing a file, summarize the saved path and main sections.

## Quality Rules

- Requirements must be testable, observable, and scoped.
- Separate goals, non-goals, assumptions, risks, dependencies, and open questions.
- Include user stories and acceptance criteria for important features.
- Define edge cases, empty states, error states, permissions, and data states for core flows when relevant.
- Prioritize requirements with `P0/P1/P2` or `Must/Should/Could`.
- Keep technical detail proportional to the product decision. Do not over-specify implementation when product direction is still unsettled.
- Preserve the user's intent during optimization and call out meaningful changes instead of silently changing direction.

## Output Contract

For Chinese requests, use Chinese headings and labels. For new PRDs, include at minimum:

- 需求概述
- 问题与目标
- 目标用户与核心场景
- 范围、非目标与假设
- 功能需求
- 相关时包含非功能需求
- 用户故事与验收标准
- 相关时包含埋点或成功指标
- 风险、依赖、待确认问题与下一步

For optimization tasks, preserve the user's intent and provide:

- 修改摘要
- 优化后的 PRD 或章节改写
- 保留的关键假设
- 必要时说明被调整的范围、优先级或表述决策
- 剩余待确认问题

For reviews, lead with findings ordered by severity:

- `阻塞 Blocking`: issues that prevent execution or approval
- `重要 Major`: gaps likely to cause rework, ambiguity, or incorrect implementation
- `次要 Minor`: clarity, consistency, or completeness improvements
- `建议 Suggestion`: optional improvements

For each review finding, include the affected section or quoted phrase when available, the issue, why it matters, and a concrete fix.
