# PM AI Workflow Skills

一套面向产品经理的 AI 工作流 Skills，用于把产品设计过程中的「产品规划 -> 需求澄清 -> PRD -> 交互原型」串成可复用、可交接、可评审的标准流程。

这套 Skills 的目标不是让 AI 直接替代产品经理，而是帮助产品经理更快地想清楚需求、写清楚文档、生成可评审原型，并让产品、研发、测试、设计、运营围绕同一套结构化产物协作。

## 项目定位

当前产品设计过程中常见的问题：

- 需求理解不清，目标用户、范围边界、上下游依赖容易遗漏。
- PRD 写作耗时，功能说明、状态、异常、验收标准反复补充。
- 原型和文档割裂，研发和测试很难从页面直接定位对应需求说明。
- Roadmap、需求分析、PRD、原型之间缺少稳定的交接格式。

本项目通过 4 个独立但可串联的 Skills 解决这些问题：

```text
roadmap-planner
  -> requirement-analyzer
  -> prd-generator
  -> prototype-generator
```

## Skills 概览

| Skill | 负责什么 | 主要产物 |
| --- | --- | --- |
| `roadmap-planner` | 产品方向、机会池、优先级、版本节奏 | Roadmap、机会池、优先级评估、Requirement Analyzer Handoff |
| `requirement-analyzer` | 单个需求的澄清、依赖、数据、状态、风险 | 需求分析、澄清问题、PRD 交接摘要 |
| `prd-generator` | 生成、优化、评审 PRD | 结构化 PRD、验收标准、PRD Review、Prototype Handoff |
| `prototype-generator` | 基于 PRD 生成可交互 HTML 原型和标注 | `prototype.html`、页面模块、交互、需求标注 |

## 工作流

### 1. Roadmap 规划

使用 `roadmap-planner` 处理全局规划问题：

- 产品战略
- 机会池 / 需求池
- 季度 / 月度 Roadmap
- 版本节奏
- 优先级排序
- 资源、依赖、风险和取舍

示例：

```text
Use $roadmap-planner 帮我规划一个面向产品经理的 AI 工作流系统 Q3 Roadmap，包含机会池、优先级、版本节奏和下一步要澄清的需求。
```

### 2. 需求澄清

使用 `requirement-analyzer` 处理单个需求：

- 业务目标
- 目标用户与场景
- 功能边界
- 功能上下游依赖
- 数据上下游依赖
- 状态流转与异常
- 权限、规则、埋点
- 风险与待确认问题

示例：

```text
Use $requirement-analyzer 基于这个 Roadmap item，帮我澄清「订单异常处理优化」的需求，重点分析上下游功能依赖、数据依赖、状态异常和 PRD 交接摘要。
```

### 3. PRD 生成

使用 `prd-generator` 将清晰的需求分析转成可执行 PRD：

- 需求概述
- 问题与目标
- 范围与非范围
- 功能需求
- 非功能需求
- 用户故事与验收标准
- 埋点与指标
- 风险、依赖、待确认问题

示例：

```text
Use $prd-generator 基于上面的 PRD 交接摘要，生成一份标准 PRD，要求研发和测试可以直接评审。
```

### 4. 交互原型生成

使用 `prototype-generator` 从 PRD 生成可交互 HTML 原型：

- 页面导航
- 模块点击
- Tab / 筛选 / 搜索 / 弹窗 / 状态切换
- Mock 数据
- 右侧标注面板
- 需求 ID 与页面模块双向绑定
- 非可视化需求说明

示例：

```text
Use $prototype-generator 基于这份 PRD 生成一个单文件 HTML 原型，支持页面跳转、状态切换、弹窗和右侧需求标注。
```

## 核心设计原则

### 1. 边界清晰

每个 Skill 只负责一个阶段：

- `roadmap-planner` 决定做什么、为什么做、什么时候做。
- `requirement-analyzer` 把一个需求想清楚。
- `prd-generator` 把清楚的需求写成 PRD。
- `prototype-generator` 把 PRD 转成可评审原型。

### 2. 交接明确

每个阶段都提供下游可消费的交接内容：

- `roadmap-planner` 输出 `Requirement Analyzer Handoff`
- `requirement-analyzer` 输出 `PRD 交接摘要`
- `prd-generator` 输出给原型使用的页面、模块、需求 ID、状态和交互信息
- `prototype-generator` 输出原型评审和协作说明

### 3. 中文工作流友好

Skills 主体说明以英文保持触发稳定性，但输出规则明确要求：

- 中文请求默认输出中文标题和正文。
- PRD、Roadmap、需求分析、原型标注均使用中文工作流表达。
- 保留必要英文术语，如 `P0/P1/P2`、`REQ-001`、`Given/When/Then`。

### 4. 不编造事实

所有 Skills 都强调：

- 不编造市场数据、指标、预算、日期、人力、系统依赖。
- 未知内容标记为「假设」或「待确认」。
- 用户要求快速推进时，可以基于假设产出，但必须显式标注。

### 5. 需求可追溯

`prototype-generator` 的关键设计是让 PRD 和页面模块互相定位：

- 页面模块绑定 `REQ-ID`
- 点击模块查看需求说明
- 点击标注高亮页面模块
- 搜索需求 ID 定位页面
- 非可视化需求单独列出

## 目录结构

```text
.
├── roadmap-planner/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── roadmap-framework.md
│       ├── prioritization-methods.md
│       ├── roadmap-template.md
│       ├── handoff-example.md
│       └── quality-checklist.md
├── requirement-analyzer/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── analysis-framework.md
│       ├── handoff-template.md
│       ├── handoff-example.md
│       └── quality-checklist.md
├── prd-generator/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── prd-structure.md
│       ├── prd-template.md
│       ├── prd-example.md
│       ├── handoff-example.md
│       └── quality-checklist.md
└── prototype-generator/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── prototype-framework.md
        ├── annotation-system.md
        ├── output-template.md
        ├── handoff-example.md
        └── quality-checklist.md
```

## 安装方式

将需要的 Skill 文件夹复制到你的 Codex Skills 目录，例如：

```text
~/.codex/skills/
```

推荐完整安装 4 个 Skill，以获得完整链路体验：

```text
roadmap-planner
requirement-analyzer
prd-generator
prototype-generator
```

也可以只安装其中一个 Skill。单个 Skill 可以独立工作，但只能覆盖对应阶段：

- 只安装 `roadmap-planner`：可以做产品规划，但无法自动进入需求澄清。
- 只安装 `requirement-analyzer`：可以澄清单个需求，但不会生成完整 PRD。
- 只安装 `prd-generator`：可以写 PRD，但输入太模糊时会建议先澄清。
- 只安装 `prototype-generator`：可以从 PRD 生成原型，但需要已有 PRD 或结构化需求。

## 使用建议

### 从全局产品规划开始

```text
Use $roadmap-planner 帮我规划一个 AI 产品经理工作台的产品路线图。
```

### 从单个模糊需求开始

```text
Use $requirement-analyzer 帮我澄清这个需求：用户反馈订单异常时看不懂原因，客服也很难排查。
```

### 从已有需求分析生成 PRD

```text
Use $prd-generator 基于这份需求分析生成一份标准 PRD。
```

### 从已有 PRD 生成原型

```text
Use $prototype-generator 基于这份 PRD 生成可交互 HTML 原型，并为每个模块绑定需求标注。
```

## 输出示例链路

```text
产品目标 / 业务问题
  -> roadmap-planner
  -> Roadmap + Requirement Analyzer Handoff
  -> requirement-analyzer
  -> 需求分析 + PRD 交接摘要
  -> prd-generator
  -> PRD + Prototype Handoff
  -> prototype-generator
  -> prototype.html + 标注系统 + 评审说明
```

## 适用场景

- 产品经理日常需求分析
- Roadmap 与版本规划
- PRD 起草、优化和评审
- 研发评审前的需求补全
- 测试验收标准梳理
- 从 PRD 快速生成可交互原型
- 团队围绕页面模块和需求标注进行评审

## 非目标

这套 Skills 不试图解决所有产品研发问题：

- 不替代真实用户研究。
- 不替代产品经理的业务判断。
- 不生成生产级前端代码。
- 不默认接入真实后端、真实数据或第三方协作工具。
- 不强制用户必须从 Roadmap 开始；可以从任意阶段进入。

## 维护建议

- 每个 Skill 的 `SKILL.md` 保持轻量，只放触发、边界、工作流和输出契约。
- 详细框架、模板、样例和检查清单放在 `references/` 中。
- 新增能力时优先考虑是否属于现有阶段，避免把单个 Skill 做成大而全。
- 交接字段变更时，及时同步上下游 `handoff-example.md`。

## License

MIT License - 详见 [LICENSE](LICENSE) 文件。
