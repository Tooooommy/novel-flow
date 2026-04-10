# Skill: nf-novel-flow

## 描述

Novelflow 小说创作流程主控技能，整合所有部门和智能体，提供一站式小说创作流程管理。支持**串行创作**和**并行分卷创作**两种模式。遵循"Think→Plan→Build→Review→Test→Ship→Reflect"的迭代开发模式。

## 调用方式

```
/nf-novel-flow <command> [options]
```

## 命令

### full ⭐NEW

**一键执行完整创作流程（推荐）**

```
/nf-novel-flow full --name <novel-name> --genre <genre>
```

**执行：** init → think → plan → split → parallel-build → merge → review → ship

---

### init

初始化新小说项目

```
/nf-novel-flow init --name <novel-name> --genre <genre> [--target-words <count>]
```

### think

启动创意思考阶段（创意研发部）

```
/nf-novel-flow think --topic <topic> [--market-research <bool>]
```

### plan

启动架构规划阶段（架构设计部）

```
/nf-novel-flow plan --concept <selected-concept> [--depth <basic|detailed>]
```

### build

启动内容生产阶段（内容生产部）

```
/nf-novel-flow build --outline <outline-file> [--chapters <range>]
```

### review

启动质量审查阶段（质量保证部）

```
/nf-novel-flow review --content <content-path> [--level <standard|strict>]
```

### test

启动测试验证阶段

```
/nf-novel-flow test --content <content-path> [--focus <logic|compliance|quality>]
```

### ship

启动发布准备阶段（发布运营部）

```
/nf-novel-flow ship --content <content-path> --platform <platform>
```

### reflect

启动复盘改进阶段（复盘改进部）

```
/nf-novel-flow reflect --project <project-id>
```

### run

运行完整流程

```
/nf-novel-flow run --from <phase> --to <phase> [--config <config-file>]
```

### status

查看项目状态

```
/nf-novel-flow status [--project <project-id>]
```

## 🆕 并行分卷创作命令

### split

拆分大纲为分卷

```
/nf-novel-flow split --outline <main-outline> --volumes <count> [--strategy <equal|plot|character>]
```

### parallel-build

并行创作分卷

```
/nf-novel-flow parallel-build --volumes <volume-list> [--max-workers <n>] [--mode <sync|async>]
```

### merge

合并分卷为完整小说

```
/nf-novel-flow merge --volumes <volume-files> --output <output-path> [--format <format>]
```

### parallel-run

执行完整并行流程

```
/nf-novel-flow parallel-run --name <novel-name> --volumes <count> [--strategy <strategy>]
```

## 完整工作流

### 模式一：串行创作模式 (Sequential Mode)

```
┌─────────────────────────────────────────────────────────────────┐
│                     串行创作流程                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │  Think   │───▶│   Plan   │───▶│  Build   │                  │
│  │  创意研发 │    │  架构设计 │    │  内容生产 │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│       │               │               │                         │
│       ▼               ▼               ▼                         │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │ nf-idea  │    │ nf-length│    │ nf-pacing│                  │
│  │ nf-market│    │ nf-world │    │ nf-content│                  │
│  │ nf-eval  │    │ nf-story │    │ nf-optim │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│                                                                 │
│       ┌──────────┐    ┌──────────┐    ┌──────────┐             │
│       │  Review  │◀───│   Test   │◀───│   Ship   │             │
│       │  质量保证 │    │  测试验证 │    │  发布运营 │             │
│       └──────────┘    └──────────┘    └──────────┘             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**适用场景**：

- 单卷小说
- 分卷间强依赖的作品
- 需要精细控制的作品

### 模式二：并行分卷创作模式 (Parallel Volume Mode) ⭐NEW

```
┌─────────────────────────────────────────────────────────────────┐
│                   并行分卷创作流程                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Phase 1: 整体规划 (串行)                                       │
│  ┌──────────┐    ┌──────────┐                                  │
│  │  Think   │───▶│   Plan   │                                  │
│  │  创意研发 │    │  整体架构 │                                  │
│  └──────────┘    └────┬─────┘                                  │
│                       │                                         │
│                       ▼                                         │
│              ┌──────────────┐                                   │
│              │ Split Outline│                                   │
│              │ 拆分为分卷大纲│                                   │
│              └──────┬───────┘                                   │
│                     │                                           │
│  Phase 2: 并行创作 (并行)                                       │
│                     ▼                                           │
│         ┌─────────┬─────────┬─────────┐                        │
│         ▼         ▼         ▼         ▼                        │
│      ┌────┐   ┌────┐   ┌────┐   ┌────┐                        │
│      │卷1 │   │卷2 │   │卷3 │   │卷4 │   ← 并行执行            │
│      │创作│   │创作│   │创作│   │创作│                        │
│      └──┬─┘   └──┬─┘   └──┬─┘   └──┬─┘                        │
│         │        │        │        │                           │
│         ▼        ▼        ▼        ▼                           │
│      ┌────┐   ┌────┐   ┌────┐   ┌────┐                        │
│      │审查│   │审查│   │审查│   │审查│   ← 并行审查            │
│      └──┬─┘   └──┬─┘   └──┬─┘   └──┬─┘                        │
│         │        │        │        │                           │
│  Phase 3: 合并整合 (串行)                                       │
│         └────────┴────────┴────────┘                           │
│                     │                                           │
│                     ▼                                           │
│              ┌──────────────┐                                   │
│              │Merge Volumes │                                   │
│              │ 合并为全书   │                                   │
│              └──────┬───────┘                                   │
│                     │                                           │
│                     ▼                                           │
│              ┌──────────────┐                                   │
│              │   Review     │                                   │
│              │ 整体质量审查 │                                   │
│              └──────┬───────┘                                   │
│                     │                                           │
│                     ▼                                           │
│              ┌──────────────┐                                   │
│              │    Ship      │                                   │
│              │   发布运营   │                                   │
│              └──────────────┘                                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**适用场景**：

- 多卷长篇小说
- 分卷相对独立的作品
- 需要快速完成的作品

## 并行分卷创作详细流程

### Step 1: 整体规划

```yaml
执行步骤: 1. 创意研发 (Think)
  - 生成整体创意概念
  - 市场分析
  - 确定分卷数量

  2. 架构设计 (Plan)
  - 整体世界观设计
  - 主线剧情规划
  - 人物成长弧线
  - 分卷节点设计
```

### Step 2: 拆分大纲

```yaml
执行命令: /nf-novel-flow split --outline main.md --volumes 3 --strategy plot

处理流程:
  1. 分析整体大纲
  2. 确定分卷节点
  3. 生成分卷大纲:
     - volume-1-outline.md
     - volume-2-outline.md
     - volume-3-outline.md
  4. 验证分卷一致性
  5. 建立分卷依赖关系
```

### Step 3: 并行创作

```yaml
执行命令: /nf-novel-flow parallel-build --volumes 1,2,3 --max-workers 3

并行执行:
  Worker-1: 创作第一卷
    - 章节生成
    - 专项优化
    - 质量自检

  Worker-2: 创作第二卷
    - 章节生成
    - 专项优化
    - 质量自检

  Worker-3: 创作第三卷
    - 章节生成
    - 专项优化
    - 质量自检

监控:
  - 实时进度追踪
  - 质量评分监控
  - 异常自动处理
```

### Step 4: 合并整合

```yaml
执行命令: /nf-novel-flow merge --volumes vol1.md,vol2.md,vol3.md --output novel.md

合并步骤: 1. 加载各分卷内容
  2. 按顺序整合
  3. 处理卷间衔接
  4. 统一全书风格
  5. 生成完整目录
  6. 导出最终文档
```

## 阶段详解

### Phase 1: Think (思考与创意)

**目标**：从用户模糊想法到清晰创意方案

**智能体**：创意研发部 (nf-creative-rd-dept)

**工作流程**：

```
用户输入 → 创意发散 → 市场分析 → 创意评估 → 方案确定
```

**核心技能**：

- /nf-idea-explorer - 创意探索
- /nf-market-analyzer - 市场分析
- /nf-innovation-evaluator - 创新评估

**输出模板**：

```markdown
## 创意方向：[方向名称]

### 核心概念

[一句话概括故事]

### 分卷规划

- 第一卷：[主题]
- 第二卷：[主题]
- 第三卷：[主题]

### 创新亮点

1. [创新点1：与传统差异]
2. [创新点2：新颖设定]
3. [创新点3：独特视角]

### 市场匹配度

- 当前热度：★★★☆☆
- 竞争程度：中等
- 目标读者：[具体画像]
- 平台偏好：[适配平台]
```

### Phase 2: Plan (规划与设计)

**目标**：将创意转化为可执行蓝图

**智能体**：架构设计部 (nf-architecture-design-dept)

**工作流程**：

```
创意输入 → 篇幅确定 → 世界观构建 → 故事架构 → 人物设计 → 大纲输出
```

**核心技能**：

- /nf-length-planner - 篇幅规划
- /nf-world-builder - 世界构建
- /nf-story-architect - 故事架构
- /nf-character-designer - 人物设计

**篇幅规划模板**：

```yaml
总字数: 900000
分卷数: 3
每卷字数: 300000
每卷章节: 100章
更新频率: 每日2章
创作周期: 150天

分卷节点:
  volume_1:
    chapters: 1-100
    theme: "觉醒"
    climax: "第85章"

  volume_2:
    chapters: 101-200
    theme: "成长"
    climax: "第185章"

  volume_3:
    chapters: 201-300
    theme: "巅峰"
    climax: "第295章"
```

### Phase 3: Split (分卷拆分) ⭐NEW

**目标**：将整体大纲拆分为独立的分卷大纲

**智能体**：流程协调智能体 + 架构设计部

**核心技能**：

- /nf-volume-manager - 分卷管理
- /nf-story-architect - 故事架构

**拆分策略**：

| 策略      | 说明         | 适用场景       |
| --------- | ------------ | -------------- |
| equal     | 等字数拆分   | 篇幅固定的作品 |
| plot      | 剧情节点拆分 | 情节驱动的作品 |
| character | 人物成长拆分 | 成长型作品     |

**分卷大纲结构**：

```yaml
volume_outline:
  metadata:
    volume_number: 1
    volume_title: "第一卷：觉醒"
    total_volumes: 3
    word_count: 300000
    chapters: 100

  plot_arc:
    theme: "本卷主题"
    starting_state: "主角初始状态"
    ending_state: "主角卷末状态"
    main_conflict: "核心冲突"
    climax_chapter: 85

  chapter_outlines:
    - chapter: 1
      title: "章节标题"
      word_count: 3000
      plot_point: "情节点"

  continuity:
    previous_volume: null
    next_volume: 2
```

### Phase 4: Parallel Build (并行创作) ⭐NEW

**目标**：并行创作多个分卷，提高效率

**智能体**：流程协调智能体 + 多个内容生产部实例

**核心技能**：

- /nf-parallel-executor - 并行执行
- /nf-content-generator - 内容生成
- /nf-pacing-engineer - 节奏工程
- /nf-specialist-optimizer - 专业优化

**并行模式**：

| 模式          | 说明     | 效率 |
| ------------- | -------- | ---- |
| full-parallel | 完全并行 | 最高 |
| pipeline      | 流水线   | 中等 |
| hybrid        | 混合模式 | 灵活 |

**执行示例**：

```
╔═══════════════════════════════════════════════════════════════╗
║           并行创作执行面板                                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  总体进度: ████████████████████░░░░░░  67%                   ║
║  预计完成: 2024-02-15 18:30 (剩余 2小时)                      ║
║                                                               ║
║  ┌─────────────┬──────────┬──────────┬──────────┐            ║
║  │   分卷      │  进度    │  状态    │  代理    │            ║
║  ├─────────────┼──────────┼──────────┼──────────┤            ║
║  │ 第一卷      │ 100%     │ ✅完成   │ CP-01    │            ║
║  │ 第二卷      │  85%     │ 🔄执行中 │ CP-02    │            ║
║  │ 第三卷      │  45%     │ 🔄执行中 │ CP-03    │            ║
║  └─────────────┴──────────┴──────────┴──────────┘            ║
║                                                               ║
║  活跃线程: 3/5  完成速度: 3章/小时                            ║
╚═══════════════════════════════════════════════════════════════╝
```

### Phase 5: Merge (合并整合) ⭐NEW

**目标**：将多个分卷合并为完整小说

**智能体**：流程协调智能体

**核心技能**：

- /nf-novel-merger - 小说合并
- /nf-specialist-optimizer - 专业优化

**合并步骤**：

```yaml
merge_steps:
  1_load: "加载所有分卷内容"
  2_order: "按卷号排序"
  3_connect: "处理卷间衔接"
  4_unify: "统一全书风格"
  5_polish: "整体润色"
  6_finalize: "生成最终文档"
```

**统一维度**：

- 语言风格统一
- 格式规范统一
- 术语使用统一
- 叙述语气统一

### Phase 6: Review (审查与优化)

**目标**：整体质量检查

**智能体**：质量保证部

**核心技能**：

- /nf-logic-inspector - 逻辑审查
- /nf-compliance-officer - 合规审查
- /nf-quality-assessor - 质量评估

### Phase 7: Ship (发布与运营)

**目标**：作品发布

**智能体**：发布运营部

**核心技能**：

- /nf-platform-adapter - 平台适配
- /nf-publish-strategist - 发布策略

## 效率对比

| 模式              | 100万字小说 | 300万字小说 | 适用场景 |
| ----------------- | ----------- | ----------- | -------- |
| **串行模式**      | 约 5-7 天   | 约 15-21 天 | 精细控制 |
| **并行模式(3卷)** | 约 2-3 天   | 约 6-9 天   | 快速产出 |
| **效率提升**      | **60%**     | **60%**     | -        |

## 使用示例

### 示例1：快速创建多卷小说

```bash
# 一键执行完整并行流程
/nf-novel-flow parallel-run \
  --name "九霄神帝" \
  --genre "玄幻" \
  --volumes 3 \
  --strategy plot

系统输出:
🚀 启动并行分卷创作流程...

Phase 1/5: 整体规划
├─ 创意研发 ✅
├─ 架构设计 ✅
└─ 生成整体大纲 ✅

Phase 2/5: 分卷拆分
├─ 分析分卷节点 ✅
├─ 生成第一卷大纲 ✅
├─ 生成第二卷大纲 ✅
└─ 生成第三卷大纲 ✅

Phase 3/5: 并行创作 (预计6小时)
├─ 第一卷创作 🔄 (Worker-1) 45%
├─ 第二卷创作 🔄 (Worker-2) 42%
└─ 第三卷创作 🔄 (Worker-3) 38%

Phase 4/5: 合并整合
...

Phase 5/5: 发布准备
...

✅ 创作完成！
📚 作品: 《九霄神帝》
📊 总字数: 900,000字
⏱️ 耗时: 5.5小时
📈 效率提升: 65%
```

### 示例2：分步执行

```bash
# Step 1: 初始化项目
/nf-novel-flow init --name "星际穿越" --genre "科幻"

# Step 2: 创意研发
/nf-novel-flow think --topic "人类星际移民"

# Step 3: 架构设计
/nf-novel-flow plan --concept "方案A"

# Step 4: 拆分大纲为3卷
/nf-novel-flow split --outline outline.md --volumes 3 --strategy plot

# Step 5: 并行创作3卷
/nf-novel-flow parallel-build --volumes 1,2,3 --max-workers 3

# Step 6: 合并为全书
/nf-novel-flow merge --volumes vol1.md,vol2.md,vol3.md --output novel.md

# Step 7: 质量审查
/nf-novel-flow review --content novel.md

# Step 8: 发布
/nf-novel-flow ship --content novel.md --platform qidian
```

## 部门与智能体映射

| 阶段               | 部门               | 智能体                         | 技能                                                                           |
| ------------------ | ------------------ | ------------------------------ | ------------------------------------------------------------------------------ |
| Think              | 创意研发部         | nf-creative-rd-dept            | nf-idea-explorer, nf-market-analyzer, nf-innovation-evaluator                  |
| Plan               | 架构设计部         | nf-architecture-design-dept    | nf-length-planner, nf-world-builder, nf-story-architect, nf-character-designer |
| **Split**          | **流程协调**       | **nf-process-coordinator**     | **nf-volume-manager** ⭐NEW                                                    |
| **Parallel Build** | **内容生产部(xN)** | **nf-content-production-dept** | **nf-parallel-executor, nf-content-generator** ⭐NEW                           |
| **Merge**          | **流程协调**       | **nf-process-coordinator**     | **nf-novel-merger** ⭐NEW                                                      |
| Review             | 质量保证部         | nf-quality-assurance-dept      | nf-logic-inspector, nf-compliance-officer, nf-quality-assessor                 |
| Ship               | 发布运营部         | nf-publishing-ops-dept         | nf-platform-adapter, nf-publish-strategist                                     |

## 📁 文件输出规范

### 项目目录结构

所有流程产生的文件都保存在 `novels/` 目录下，每个小说一个独立项目：

```
novels/
└── <novel-name>/              # 小说项目目录 (由 init 命令创建)
    │
    ├── novel.yaml              # 📋 小说元数据配置
    │
    ├── outline/                # 📝 大纲文档 (Plan 阶段输出)
    │   ├── overview.md        # 总览
    │   ├── world.md           # 世界观设定
    │   ├── plot.md            # 主线剧情
    │   ├── characters.md      # 人物关系图
    │   ├── timeline.md        # 时间线
    │   ├── volume-1-outline.md
    │   ├── volume-2-outline.md
    │   └── volume-3-outline.md
    │
    ├── content/                # 📖 正文内容 (Build 阶段输出)
    │   ├── volume-1/
    │   │   ├── ch-001.md     # 第1章
    │   │   ├── ch-002.md
    │   │   └── ...
    │   ├── volume-2/
    │   └── volume-3/
    │
    ├── drafts/                 # 📄 草稿 (原始生成内容)
    │   ├── ch-001-draft.md
    │   └── ...
    │
    ├── research/               # 🔍 研究资料 (Think 阶段输出)
    │   ├── market-analysis.md
    │   ├── idea-brainstorm.md
    │   └── innovation-eval.md
    │
    ├── reviews/                # ✅ 审查报告 (Review 阶段输出)
    │   ├── logic-check.md
    │   ├── compliance.md
    │   └── quality-report.md
    │
    └── output/                # 📦 发布输出 (Ship 阶段输出)
        ├── full-novel.md      # 合并后完整版
        ├── qidian/
        └── tomato/
```

### 命令与文件对应

| 命令     | 主要输出目录                             | 说明           |
| -------- | ---------------------------------------- | -------------- |
| `init`   | `novels/<name>/novel.yaml`               | 创建项目元数据 |
| `think`  | `novels/<name>/research/`                | 创意研发文档   |
| `plan`   | `novels/<name>/outline/`                 | 大纲文档       |
| `split`  | `novels/<name>/outline/volume-*.md`      | 分卷大纲       |
| `build`  | `novels/<name>/content/volume-X/ch-*.md` | 正文章节       |
| `merge`  | `novels/<name>/output/full-novel.md`     | 合并后全文     |
| `review` | `novels/<name>/reviews/`                 | 审查报告       |
| `ship`   | `novels/<name>/output/<platform>/`       | 平台适配版本   |

### 文件命名规范

```bash
# 章节文件
ch-XXX.md           # XXX 为三位章节号，如 ch-001.md

# 分卷大纲
volume-X-outline.md # X 为卷号，如 volume-1-outline.md

# 草稿版本
ch-XXX-draft-vN.md  # N 为版本号，如 ch-001-draft-v1.md

# 审查报告
<type>-<date>.md    # 如 logic-check-20240115.md
```

## 输出

- 完整小说作品 (`novels/<name>/output/full-novel.md`)
- 各分卷独立文件 (`novels/<name>/content/volume-X/`)
- 创作过程文档 (`novels/<name>/research/`)
- 质量评估报告 (`novels/<name>/reviews/`)
- 发布就绪版本 (`novels/<name>/output/<platform>/`)
- 效率分析报告
