---
name: prototype-generator
description: Interactive HTML prototype generation skill for product managers. Use when the user provides a PRD, product requirements document, feature specification, structured requirements, page logic, interaction rules, user flows, or acceptance criteria and wants to generate, review, or improve a clickable HTML prototype with annotations, requirement mapping, state switching, page navigation, modals, and PRD-linked module explanations.
---

# Prototype Generator

Use this skill to turn a clear PRD or structured requirement into an interactive HTML prototype with PRD-linked annotations. The goal is to support requirement review and cross-functional collaboration, not to create production-ready frontend code.

Match the user's language by default. For Chinese requests, write Chinese headings, annotation labels, and visible prototype text unless the user asks for another language.

## Workflow Position

Use this skill after `prd-generator`, when the requirement is clear enough to visualize. If the user is planning product direction or releases, use `roadmap-planner`. If the requirement is vague or dependency-heavy, use `requirement-analyzer`. If the PRD is missing core page logic or requirements, use `prd-generator` or ask for the missing information before prototyping.

## Boundary

- Use `roadmap-planner` for product strategy, opportunity prioritization, roadmap, and release sequencing.
- Use `requirement-analyzer` for unclear requirements, dependency analysis, data dependencies, states, permissions, risks, and PRD handoff.
- Use `prd-generator` for writing, optimizing, or reviewing executable PRDs.
- Use `prototype-generator` for generating interactive HTML prototypes and PRD-linked annotations from a PRD.

Do not rewrite the PRD unless the user asks. Do not claim the prototype is production code. Do not connect to real backends or real user data unless explicitly provided and appropriate.

## Task Types

- `Generate`: create an interactive HTML prototype from a PRD or structured requirement.
- `Annotate`: add or improve requirement-linked annotations for an existing prototype concept.
- `Review`: evaluate a prototype against a PRD for missing pages, states, interactions, or annotations.
- `Improve`: revise an existing prototype structure, interaction model, or annotation scheme.
- `Handoff`: prepare prototype implementation notes and missing-input questions.

## Workflow

1. Identify prototype scope and output target.
   - Default output is a single self-contained HTML file unless the user asks for multi-file output.
   - Generate files only when the user asks to save/export or the task is clearly inside a repository/documentation workflow.
   - If responding in chat, provide a concise prototype plan, assumptions, and key HTML structure instead of dumping a huge file.
   - If the prototype has more than 3 pages, many annotations, or complex interactions, recommend writing files instead of outputting full HTML in chat.
   - Only output complete HTML in chat when the user explicitly asks or the prototype is small enough to remain readable.

2. Check input sufficiency.
   - Required for a solid prototype: page list, core user flows, functional requirements, interaction rules, states, and roles/permissions when relevant.
   - If two or more are missing among page list, core flow, functional requirements, interaction rules, state descriptions, and role permissions, recommend going back to `prd-generator` or ask focused questions.
   - If the user asks to proceed anyway, create a low-fidelity assumption-based prototype and clearly list assumptions and missing information.

3. Parse the PRD.
   - Read `references/prototype-framework.md` for PRD-to-prototype analysis.
   - Extract pages, modules, user flows, actions, states, permissions, data objects, empty/error/loading states, and acceptance criteria.
   - Build a requirement-to-module map using IDs such as `REQ-001`, `FLOW-001`, `STATE-001`, or create stable IDs when absent.

4. Design the annotation system.
   - Read `references/annotation-system.md` for module-to-requirement linking.
   - Every important PRD requirement should have a visible prototype representation or an explicit note explaining why it has no UI.
   - Each key module should expose its requirement ID, functional description, interaction rules, states, and acceptance notes.

5. Generate or revise the prototype.
   - Read `references/output-template.md` for single-file HTML output requirements.
   - Default to clear desktop web or SaaS/admin-tool style unless the PRD indicates mobile, consumer, game, or another interface type.
   - Support meaningful interactions: navigation, tabs, filters, search, modal open/close, state switching, form validation, selections, success/error feedback, and simple mock data.

6. Review quality before final output.
   - Read `references/quality-checklist.md` for final checks.
   - Read `references/handoff-example.md` when preparing prototype review or collaboration handoff notes.
   - Ensure key requirements are represented, interactions work conceptually, annotations are searchable/clickable, and missing assumptions are visible.

## Output Contract

For Chinese requests, use Chinese headings and labels.

For prototype generation, provide:

- 原型范围与假设
- 页面与模块清单
- 需求 ID 到模块的映射摘要
- 交互能力说明
- 输出文件或 HTML 内容
- 缺失信息与待确认问题

For annotate tasks, provide:

- 标注范围
- 模块到需求 ID 映射表
- 新增或修改的标注
- 非可视化需求列表
- 标注覆盖缺口
- 待确认问题

For improve tasks, provide:

- 修改摘要
- 改进范围
- 改进后的页面、模块、交互或标注方案
- 影响到的需求 ID
- 保留的假设
- 待确认问题

If writing files, default to:

- `prototype.html` for a single-file prototype

If multi-file output is requested, use:

- `index.html`
- `styles.css`
- `app.js`
- `annotations.json`

For prototype review, lead with findings:

- `阻塞 Blocking`: prevents meaningful review or interaction
- `重要 Major`: missing key page, flow, state, requirement mapping, or annotation
- `次要 Minor`: clarity, consistency, visual hierarchy, or usability issue
- `建议 Suggestion`: optional improvement

## Quality Rules

- Every important PRD requirement should be visible in the prototype or explicitly marked as non-visual.
- Prioritize reviewability, clarity, and requirement traceability over visual polish.
- Keep mock data plausible but clearly fake.
- Do not introduce unrequested business logic as fact; mark assumptions.
- UI text should fit, be readable, and match the user's language.
- Avoid decorative landing pages unless the PRD is explicitly for a landing page.
- The prototype should help product, design, engineering, QA, and stakeholders discuss the same requirement with the same visual reference.
