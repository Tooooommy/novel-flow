---
name: nf-novel-flow
description: |
  NovelFlow小说创作AI工厂主控技能。
  触发场景：创作小说、大纲、章节、审查优化、进度探测、一键自动化。
  核心流程：立项 → 创作 → 发布
---

# NovelFlow 小说创作主控技能

## 核心哲学

**三阶段流程**：立项(种子) → 创作(生成) → 发布(收获)

- 命令设计遵循「渐进式披露」原则：简单命令隐藏复杂参数
- 增量优先：自动检测已有内容，跳过完成部分
- 并行优先：多卷同时创作，节省时间

---

## 系统架构

```
用户
  │
  └──→ nf-novel-flow（主控技能）
            │
            ├──→ 创意研发层
            │       nf-idea-explorer（创意探索）
            │
            ├──→ 架构设计层
            │       nf-story-architect（世界观/人物/大纲）
            │
            ├──→ 内容生产层
            │       nf-content-generator（正文生成）
            │       nf-style-learner（风格学习）
            │
            ├──→ 质量保证层
            │       nf-logic-inspector（逻辑审查）
            │       nf-compliance-officer（合规审查）
            │       nf-quality-assessor（质量评估）
            │
            ├──→ 专业优化层
            │       nf-specialist-optimizer（文风/对话/战斗优化）
            │
            ├──→ 发布运营层
            │       nf-platform-adapter（平台适配）
            │
            ├──→ 知识管理层
            │       nf-knowledge-curator（知识沉淀）
            │
            └──→ 流程分析层
                    nf-process-analyst（流程分析）
```

---

## 技能全景图

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              NovelFlow 技能全景                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         立项阶段                                          │    │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐  │    │
│  │  │ nf-idea-explorer │  │nf-volume-manager│  │   nf-style-learner    │  │    │
│  │  │   创意探索      │  │   卷结构设计     │  │     风格学习           │  │    │
│  │  │  市场分析/灵感  │  │  分卷规划/字数   │  │   作家风格/自定义     │  │    │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                      ↓                                            │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         架构阶段                                          │    │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐  │    │
│  │  │nf-story-architect│  │nf-knowledge-    │  │   nf-style-learner    │  │    │
│  │  │   世界观/人物   │  │   curator        │  │     风格确认           │  │    │
│  │  │  大纲/主线      │  │   知识查询/收集  │  │   目标作家/应用       │  │    │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                      ↓                                            │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         创作阶段                                          │    │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐  │    │
│  │  │nf-content-      │  │nf-quality-      │  │  nf-specialist-        │  │    │
│  │  │generator        │  │assessor         │  │  optimizer             │  │    │
│  │  │  正文生成       │  │  质量评估       │  │  文风/对话/战斗       │  │    │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────────────┘  │    │
│  │                                                                         │    │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐  │    │
│  │  │nf-logic-        │  │nf-compliance-   │  │  nf-volume-manager     │  │    │
│  │  │inspector        │  │officer          │  │  卷衔接/结构优化       │  │    │
│  │  │  逻辑审查       │  │  合规检查       │  │                        │  │    │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                      ↓                                            │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         发布阶段                                          │    │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐  │    │
│  │  │nf-platform-     │  │nf-knowledge-    │  │  nf-process-analyst   │  │    │
│  │  │adapter          │  │curator          │  │  流程复盘/效率分析     │  │    │
│  │  │  平台适配        │  │  经验沉淀        │  │                        │  │    │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 技能分类总表

| 分类         | 技能缩写 | 技能名称                | 核心功能                     | 调用层级 |
| ------------ | -------- | ----------------------- | ---------------------------- | -------- |
| **主控**     | NF       | nf-novel-flow           | 主控流程、命令分发、状态管理 | L0       |
| **创意研发** | IE       | nf-idea-explorer        | 创意探索、市场分析、灵感获取 | L1       |
| **架构设计** | SA       | nf-story-architect      | 世界观、人物、主线、大纲设计 | L1       |
| **架构设计** | VM       | nf-volume-manager       | 卷结构、分卷大纲、节奏把控   | L1       |
| **内容生产** | CG       | nf-content-generator    | 正文生成、多风格支持         | L1       |
| **内容生产** | SL       | nf-style-learner        | 风格学习、作家模仿、文风提升 | L1       |
| **质量保证** | LI       | nf-logic-inspector      | 逻辑审查、战力检查、矛盾排查 | L2       |
| **质量保证** | CO       | nf-compliance-officer   | 合规检查、敏感词、违规内容   | L2       |
| **质量保证** | QA       | nf-quality-assessor     | 质量评估、评分、问题诊断     | L2       |
| **专业优化** | SO       | nf-specialist-optimizer | 文风优化、对话优化、战斗优化 | L2       |
| **发布运营** | PA       | nf-platform-adapter     | 平台适配、格式转换、发布策略 | L1       |
| **知识管理** | KC       | nf-knowledge-curator    | 知识沉淀、经验复用、模板库   | L1       |
| **流程分析** | PA-ana   | nf-process-analyst      | 效率分析、瓶颈识别、改进建议 | L1       |

---

## 技能调用关系

### 阶段调用链

```
立项阶段:
  idea → IE → 市场分析 → 创意生成
       → VM → 分卷规划
       → SL → 风格选择

架构阶段:
  outline → SA → 世界观 → 人物 → 主线
          → VM → 卷大纲
          → KC → 知识查询

创作阶段:
  write → CG → 正文生成
        → LI → 逻辑审查
        → CO → 合规检查
        → QA → 质量评估
        → SO → 专业优化
        → VM → 卷衔接

发布阶段:
  publish → PA → 平台适配
          → KC → 知识沉淀
          → PA-ana → 流程复盘
```

### 技能间调用矩阵

| 调用方 ↓ / 被调用方 → | IE  | SA  | VM  | CG  | SL  | LI  | CO  | QA  | SO  | PA  | KC  | PA-ana |
| --------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------ |
| **NF (主控)**         | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | ✅     |
| **IE (创意)**         | -   | -   | ✅  | -   | -   | -   | -   | -   | -   | -   | ✅  | -      |
| **SA (架构)**         | -   | -   | ✅  | -   | ✅  | -   | -   | -   | -   | -   | ✅  | -      |
| **VM (卷管理)**       | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | ✅  | -      |
| **CG (内容生成)**     | -   | -   | ✅  | -   | ✅  | -   | -   | ✅  | ✅  | -   | -   | -      |
| **SL (风格学习)**     | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | ✅  | -      |
| **LI (逻辑审查)**     | -   | -   | -   | ✅  | -   | -   | -   | -   | ✅  | -   | ✅  | -      |
| **CO (合规审查)**     | -   | -   | -   | ✅  | -   | -   | -   | -   | -   | -   | -   | -      |
| **QA (质量评估)**     | -   | -   | -   | ✅  | -   | -   | -   | -   | -   | -   | -   | -      |
| **SO (专业优化)**     | -   | -   | -   | ✅  | ✅  | -   | -   | ✅  | -   | -   | -   | -      |
| **PA (平台适配)**     | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | -      |
| **KC (知识管理)**     | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | -      |
| **PA-ana (流程分析)** | -   | -   | -   | -   | -   | -   | -   | -   | -   | -   | ✅  | -      |

---

## 干预节点

| 节点     | 阶段 | 干预方式           | 超时处理     |
| -------- | ---- | ------------------ | ------------ |
| 创意确认 | 立项 | 选择/修改/重新生成 | 自动通过推荐 |
| 大纲确认 | 规划 | 确认/修改          | 暂停等待     |
| 人物确认 | 规划 | 确认/修改          | 暂停等待     |
| 章节审核 | 创作 | 通过/打回          | 自动下一章   |

**干预节点详细标准**:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        干预节点执行标准                                   │
├────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  N1: 创意确认节点                                                       │
│  ├── 触发时机: idea命令执行完成后                                      │
│  ├── 干预方式:                                                         │
│  │      - 选择: 从生成的创意中选择                                      │
│  │      - 修改: 对选中创意进行调整                                      │
│  │      - 重新生成: 放弃当前结果，重新生成                               │
│  │                                                                         │
│  ├── 超时处理: 10分钟无响应，自动选择排名第一的创意                     │
│  └── 输出: 确认的创意概念                                               │
│                                                                         │
│  N2: 大纲确认节点                                                       │
│  ├── 触发时机: outline命令执行完成后                                   │
│  ├── 干预方式:                                                         │
│  │      - 确认: 直接进入下一阶段                                        │
│  │      - 修改: 指出需修改的部分                                        │
│  │      - 补充: 提供额外信息完善大纲                                     │
│  │                                                                         │
│  ├── 超时处理: 30分钟无响应，暂停并发送提醒                             │
│  └── 输出: 确认的大纲版本                                               │
│                                                                         │
│  N3: 人物确认节点                                                       │
│  ├── 触发时机: 人物档案生成完成后                                      │
│  ├── 干预方式:                                                         │
│  │      - 确认: 人物设定通过                                             │
│  │      - 调整: 修改人物性格/背景/关系                                   │
│  │      - 新增: 添加新人物                                               │
│  │                                                                         │
│  ├── 超时处理: 20分钟无响应，自动确认当前版本                           │
│  └── 输出: 确认的人物档案                                               │
│                                                                         │
│  N4: 章节审核节点                                                       │
│  ├── 触发时机: 每章创作完成                                            │
│  ├── 干预方式:                                                         │
│  │      - 通过: 质量达标，进入下一章                                     │
│  │      - 打回: 质量不达标，返回优化                                     │
│  │      - 跳过: 临时跳过，继续下一章                                     │
│  │                                                                         │
│  ├── 超时处理: 自动通过(基于质量评估分数>70)                            │
│  └── 输出: 审核通过的章节                                               │
│                                                                         │
└────────────────────────────────────────────────────────────────────────┘
```

**质量门禁标准**:

| 检查阶段 | 门禁条件    | 不通过处理 | 超时处理      |
| -------- | ----------- | ---------- | ------------- |
| 立项     | 创意评分≥60 | 重新生成   | 自动通过      |
| 大纲     | 结构完整    | 补充大纲   | 暂停等待      |
| 人物     | 人物立体    | 完善设定   | 自动确认      |
| 章节     | 质量评分≥70 | 优化重审   | 自动通过(>70) |
| 优化     | 达标分数≥80 | 再次优化   | 保留原版      |
| 发布     | 合规检查    | 修改内容   | 暂停发布      |

---

## 命令地图

| 命令           | 对应SKILL                                                      | 用途       | 典型用法                       |
| -------------- | -------------------------------------------------------------- | ---------- | ------------------------------ |
| `/nf idea`     | [nf-idea-explorer](../nf-idea-explorer/SKILL.md)               | 创意探索   | `idea --genre 玄幻`            |
| `/nf init`     | -                                                              | 项目初始化 | `init --name xxx --genre 玄幻` |
| `/nf outline`  | [nf-volume-manager](../nf-volume-manager/SKILL.md)             | 生成大纲   | `outline`                      |
| `/nf volume`   | [nf-volume-manager](../nf-volume-manager/SKILL.md)             | 生成分卷   | `volume`                       |
| `/nf write`    | [nf-content-generator](../nf-content-generator/SKILL.md)       | 创作正文   | `write --mode parallel`        |
| `/nf review`   | [nf-quality-assessor](../nf-quality-assessor/SKILL.md)         | 内容审查   | `review --chapter 5`           |
| `/nf optimize` | [nf-specialist-optimizer](../nf-specialist-optimizer/SKILL.md) | 优化内容   | `optimize --type style`        |
| `/nf publish`  | [nf-platform-adapter](../nf-platform-adapter/SKILL.md)         | 发布平台   | `publish --platform qidian`    |
| `/nf detect`   | -                                                              | 进度探测   | `detect`                       |
| `/nf auto`     | -                                                              | 一键自动化 | `auto --name xxx --genre 玄幻` |

**主控命令流程**:

```mermaid
flowchart LR
    A[idea] --> B[init] --> C[outline] --> D[volume] --> E[write] --> F[review] --> G[optimize] --> H[publish]
```

**子技能直接调用**（使用技能缩写）：

| 缩写 | 对应SKILL            | 缩写     | 对应SKILL               |
| ---- | -------------------- | -------- | ----------------------- |
| `ie` | nf-idea-explorer     | `li`     | nf-logic-inspector      |
| `sa` | nf-story-architect   | `co`     | nf-compliance-officer   |
| `vm` | nf-volume-manager    | `qa`     | nf-quality-assessor     |
| `cg` | nf-content-generator | `so`     | nf-specialist-optimizer |
| `sl` | nf-style-learner     | `pa`     | nf-platform-adapter     |
| `kc` | nf-knowledge-curator | `pa-ana` | nf-process-analyst      |

---

## 状态管理标准

**项目状态机**:

```mermaid
stateDiagram-v2
    [*] --> NONE
    NONE --> INITIAL : init
    INITIAL --> PLANNED : outline
    PLANNED --> WRITING : write
    WRITING --> WRITTEN : write
    WRITTEN --> OPTIMIZED : optimize
    OPTIMIZED --> READY : 全部章节完成
    READY --> PUBLISHED : publish
```

**章节状态标准**:

| 状态       | 说明       | 可执行操作       |
| ---------- | ---------- | ---------------- |
| pending    | 待创作     | write            |
| writing    | 创作中     | -                |
| reviewing  | 审查中     | -                |
| passed     | 审查通过   | optimize         |
| optimizing | 优化中     | -                |
| completed  | 完成       | publish          |
| rejected   | 审查不通过 | rewrite/optimize |

**状态转换规则**:

```
pending → writing: write命令触发
writing → reviewing: 章节生成完成
reviewing → passed: 质量评分≥70
reviewing → rejected: 质量评分<70
rejected → writing: rewrite命令
rejected → optimizing: optimize命令
passed → optimizing: optimize命令
optimizing → completed: 优化完成
completed → ready: 所有章节完成
ready → published: publish命令
```

---

## 立项阶段

### idea - 创意探索

**用途**：当你不知道写什么时，获取创意灵感

```
/nf idea [--count <数量>] [--genre <题材>]
```

1. 调用子技能 [nf-idea-explorer](../nf-idea-explorer/SKILL.md) full命令生成创意
2. 输出生成的创意列表

**建议**：先用 `idea` 探索方向，再用 `init` 立项

---

### init - 项目立项

**用途**：创建新小说项目，初始化目录结构

```
/nf init --name <名称> --genre <题材> --target <字数> [--chapter-size <每章字数>]
```

1. 调用子技能 [nf-project-init](../nf-project-init/SKILL.md) full命令初始化项目
2. 输出初始化的项目目录结构

---

## 创作阶段

### outline - 大纲生成

**用途**：根据 `novel.yaml` 项目元数据，生成完整大纲体系

```
/nf outline [--metadata <元数据文件>]
```

1. 调用子技能 [nf-story-architect](../nf-story-architect/SKILL.md) full命令生成大纲体系
2. 输出生成的大纲体系文档

### write - 创作写作

**用途**：按大纲生成章节正文，内置审查循环

```
/nf write [--volume <卷号>] [--chapter <章节号>]
```

1. 调用子技能 [nf-content-generator](../nf-content-generator/SKILL.md) full命令生成章节正文
2. 输出生成的章节正文

---

### review - 内容审查

**用途**：检查章节质量，输出审查报告（调用多技能(LI逻辑审查、CO合规审查、QA质量评估)协同工作）

```
/nf review [--chapter <章节号>] [--volume <卷号>]
```

1. 并行调用
   - 子技能 [nf-logic-inspector](../nf-logic-inspector/SKILL.md) full命令进行逻辑审查
   - 子技能 [nf-compliance-officer](../nf-compliance-officer/SKILL.md) full命令进行合规审查
   - 子技能 [nf-quality-assessor](../nf-quality-assessor/SKILL.md) full命令进行质量评估
2. 输出逻辑审查报告+质量评估报告+合规审查报告

---

### optimize - 全量优化

**用途**：深度优化章节或全书质量（调用 `nf-specialist-optimizer`）

```
/nf optimize [--volume <卷号>] [--chapter <章节号>] [--type <类型>]
```

1. 调用子技能 [nf-specialist-optimizer](../nf-specialist-optimizer/SKILL.md) full命令进行全量优化
2. 输出优化后的章节正文

---

## 发布阶段

### publish - 发布

**用途**：适配目标平台格式并发布（调用 `nf-platform-adapter`）

```
/nf publish --platform <平台> [--format <格式>]
```

| 参数     | 类型   | 默认值 | 说明             |
| -------- | ------ | ------ | ---------------- |
| platform | string | -      | 目标平台（必填） |
| format   | string | auto   | 格式类型         |

**支持平台**：详见 `nf-platform-adapter` 技能

**执行流程**：`publish` → `nf-platform-adapter` → 格式转换 → 发布

---

## 全局命令

### detect - 进度探测

**用途**：探测项目当前状态，为 `auto` 命令提供增量数据

```
/nf detect [--project <项目名>]
```

| 参数    | 类型   | 默认值 | 说明     |
| ------- | ------ | ------ | -------- |
| project | string | 当前   | 项目名称 |

**输出示例**：

```json
{
  "project": "逆天剑尊",
  "phase": "writing",
  "progress": {
    "outline": { "complete": true, "total": 6, "done": 6 },
    "content": { "total": 90, "written": 15, "progress": "16.7%" }
  },
  "volumes": [
    { "id": 1, "name": "觉醒", "chapters": 30, "written": 15, "status": "in_progress" },
    { "id": 2, "name": "崛起", "chapters": 30, "written": 0, "status": "pending" },
    { "id": 3, "name": "称霸", "chapters": 30, "written": 0, "status": "pending" }
  ],
  "missing": ["v1/ch-016", "v1/ch-017", ..., "v2/ch-001", ...]
}
```

---

### auto - 一键自动化

**用途**：全自动完成整本小说（立项→大纲→正文→优化→发布）

```
/nf auto --name <名称> --genre <题材> [--platform <平台>] [--chapters <数量>] [--volumes <卷数>] [--mode <模式>]
```

| 参数     | 类型   | 默认值   | 说明             |
| -------- | ------ | -------- | ---------------- |
| name     | string | -        | 小说名称（必填） |
| genre    | string | -        | 题材类型（必填） |
| platform | string | -        | 发布平台         |
| chapters | number | 30       | 每卷章节数       |
| volumes  | number | 3        | 分卷数量         |
| mode     | string | parallel | 创作模式         |

**智能特性**：

| 特性     | 说明               |
| -------- | ------------------ |
| 增量创作 | 自动跳过已有章节   |
| 断点续传 | 中断后可继续       |
| 智能衔接 | 换卷时自动优化衔接 |

**完整流程**：

```
[1/6] init        → 创建项目结构
[2/6] outline     → 生成大纲体系
[3/6] write        → 并行创作正文
      ↓
      ├─ V1: Ch1 → Ch30
      ├─ V2: Ch1 → Ch30
      └─ V3: Ch1 → Ch30
      ↓
[4/6] optimize    → 衔接优化
[5/6] optimize    → 全量优化
[6/6] publish     → 平台发布（可选）
```

**执行模式**：

| 模式        | 说明                         |
| ----------- | ---------------------------- |
| full        | 完全自动化（需所有必填参数） |
| incremental | 增量模式（跳过已完成章节）   |
| resume      | 断点续传（从中断处继续）     |

---

## 全局命令

### learn - 知识学习

**用途**：从项目中收集知识、经验、模板（调用 `nf-knowledge-curator`）

```
/nf learn [--collect] [--from <来源>] [--type <类型>]
```

| 参数    | 类型   | 默认值   | 说明     |
| ------- | ------ | -------- | -------- |
| collect | flag   | false    | 收集知识 |
| from    | string | 当前项目 | 知识来源 |
| type    | string | all      | 知识类型 |

**执行流程**：`learn` → `nf-knowledge-curator` → 收集 → 组织 → 索引 → 可查询

---

### query - 知识查询

**用途**：查询已有知识库（调用 `nf-knowledge-curator`）

```
/nf query [--query <关键词>] [--type <类型>] [--limit <数量>]
```

| 参数  | 类型   | 默认值 | 说明       |
| ----- | ------ | ------ | ---------- |
| query | string | -      | 搜索关键词 |
| type  | string | all    | 知识类型   |
| limit | number | 5      | 返回数量   |

**执行流程**：`query` → `nf-knowledge-curator` → 检索 → 返回结果

---

## 错误处理

| 错误码 | 说明       | 处理方式           |
| ------ | ---------- | ------------------ |
| NF-001 | 项目不存在 | 提示运行 `init`    |
| NF-002 | 大纲不存在 | 提示运行 `outline` |
| NF-003 | 章节不存在 | 自动创建空文件     |
| NF-004 | 平台不支持 | 使用通用格式       |
| NF-005 | 自动化失败 | 回滚到手动流程     |
| NF-006 | 创作中断   | 保存断点，支持续传 |
| NF-007 | 探测失败   | 检查项目路径       |
| NF-008 | 审查不通过 | 自动调用优化       |

---

## 使用示例

**场景1：全新创作**

```bash
/nf auto --name 逆天剑尊 --genre 玄幻 --chapters 30 --volumes 3
```

**场景2：继续创作**

```bash
/nf detect                      # 查看进度
/nf auto --name 逆天剑尊         # 增量模式自动继续
```

**场景3：分步创作**

```bash
/nf init --name 我的小说 --genre 都市
/nf outline --volumes 3
/nf write --mode parallel
/nf optimize --type full
/nf publish --platform qidian
```
