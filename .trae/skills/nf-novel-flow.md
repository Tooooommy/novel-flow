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
            ├──→ 创意/大纲 Skills
            │       nf-idea-explorer, nf-story-architect, nf-volume-manager
            │
            ├──→ 内容创作 Skills
            │       nf-content-generator, nf-style-learner
            │
            ├──→ 审查优化 Skills
            │       nf-logic-inspector, nf-compliance-officer, nf-quality-assessor
            │       nf-specialist-optimizer
            │
            ├──→ 发布 Skills
            │       nf-platform-adapter
            │
            └──→ 知识管理 Skills
                    nf-knowledge-curator (统一管控)
```

---

## 命令地图

| 阶段 | 命令     | 说明       | 典型用法                            |
| ---- | -------- | ---------- | ----------------------------------- |
| 立项 | idea     | 创意探索   | `idea --genre 玄幻`                 |
| 立项 | init     | 项目初始化 | `init --name xxx --genre 玄幻`      |
| 创作 | outline  | 生成大纲   | `outline --volumes 3 --chapters 30` |
| 创作 | write    | 创作正文   | `write --mode parallel`             |
| 创作 | review   | 内容审查   | `review --chapter 5`                |
| 创作 | optimize | 优化内容   | `optimize --type style`             |
| 发布 | publish  | 发布平台   | `publish --platform qidian`         |
| 全局 | detect   | 进度探测   | `detect`                            |
| 全局 | auto     | 一键自动化 | `auto --name xxx --genre 玄幻`      |
| 全局 | learn    | 知识学习   | `learn --collect --from 我的作品`   |
| 全局 | query    | 知识查询   | `query 写作技巧`                    |

---

## 立项阶段

### idea - 创意探索

**用途**：当你不知道写什么时，获取创意灵感

```
/nf idea [--count <数量>] [--genre <题材>]
```

| 参数  | 类型   | 默认值 | 说明         |
| ----- | ------ | ------ | ------------ |
| count | number | 5      | 生成几个创意 |
| genre | string | -      | 指定题材方向 |

**输出示例**：

```
[1] 都市修仙：废物逆袭，校花倒贴
    标签：都市｜修仙｜热血｜爽文
    爽点：身份反差+系统流+打脸

[2] 异世穿越：成为史上最弱召唤师
    标签：奇幻｜穿越｜召唤流
    爽点：反套路+宠物成长体系
```

**建议**：先用 `idea` 探索方向，再用 `init` 立项

---

### init - 项目立项

**用途**：创建新小说项目，初始化目录结构

```
/nf init --name <名称> --genre <题材> [--target <字数>]
```

| 参数   | 类型   | 默认值 | 说明             |
| ------ | ------ | ------ | ---------------- |
| name   | string | -      | 小说名称（必填） |
| genre  | string | -      | 题材类型（必填） |
| target | number | 100000 | 目标字数         |

**自动创建目录结构**：

```
novels/{name}/
├── novel.yaml      # 项目元数据
├── outline/        # 大纲目录
│   ├── overview.md     # 总览
│   ├── world.md        # 世界观
│   ├── characters.md    # 人物
│   ├── plot.md          # 主线
│   ├── timeline.md      # 时间线
│   └── volume-*.md      # 分卷大纲
├── content/        # 正文目录
│   └── volume-1/ch-001.md
└── research/      # 研究目录
```

---

## 创作阶段

### outline - 大纲生成

**用途**：生成完整大纲体系（总大纲 + 分卷大纲 + 人物设定 + 世界观）

```
/nf outline [--chapters <数量>] [--volumes <卷数>]
```

| 参数     | 类型   | 默认值 | 说明       |
| -------- | ------ | ------ | ---------- |
| chapters | number | 30     | 每卷章节数 |
| volumes  | number | 3      | 分卷数量   |

**生成文件**：

```
outline/
├── overview.md        # 小说总览
├── world.md          # 世界设定
├── characters.md     # 人物档案
├── plot.md           # 主线剧情
├── timeline.md        # 时间线
├── volume-1-outline.md  # 分卷大纲
├── volume-2-outline.md
└── volume-3-outline.md
```

---

### write - 创作写作

**用途**：按大纲生成章节正文，内置审查循环

```
/nf write [--volume <卷号>] [--chapter <章节号>] [--mode <模式>]
```

| 参数    | 类型   | 默认值   | 说明       |
| ------- | ------ | -------- | ---------- |
| volume  | number | 1        | 从哪卷开始 |
| chapter | number | 1        | 从哪章开始 |
| mode    | string | parallel | 创作模式   |

**创作模式**：

| 模式     | 说明               | 适用场景           |
| -------- | ------------------ | ------------------ |
| serial   | 串行：按卷按章顺序 | 需严格按大纲顺序   |
| parallel | 并行：多卷同时创作 | 效率优先、卷间独立 |

**串行流程**（适合章节间有强依赖）：

```
V1 Ch1 → 审查 → V1 Ch2 → ... → V1 Ch30
                                    ↓
                              换卷衔接
                                    ↓
V2 Ch1 → 审查 → V2 Ch2 → ... → V2 Ch30
```

**并行流程**（默认，效率更高）：

```
┌────────────┬────────────┬────────────┐
│  Volume 1  │  Volume 2  │  Volume 3  │
│  Ch 1,2,3  │  Ch 1,2,3  │  Ch 1,2,3  │ ← 同时创作
│  ...       │  ...       │  ...       │
└────────────┴────────────┴────────────┘
                 ↓
          卷1-2, 2-3衔接优化
                 ↓
            全量优化
```

**创作循环**（单章内）：

```
生成 → 逻辑审查 → 有问题? → 优化 → 重新审查
              ↓
            没问题 → 存储 → 下一章
```

---

### review - 内容审查

**用途**：检查章节质量，输出审查报告

```
/nf review [--chapter <章节号>] [--volume <卷号>]
```

| 参数    | 类型   | 默认值 | 说明   |
| ------- | ------ | ------ | ------ |
| chapter | number | 当前   | 章节号 |
| volume  | number | 当前   | 卷号   |

**审查维度**：

| 维度       | 检查内容           | 权重 |
| ---------- | ------------------ | ---- |
| logic      | 逻辑矛盾、战力崩坏 | 30%  |
| compliance | 违规内容、敏感词   | 20%  |
| quality    | 文笔、节奏、爽点   | 50%  |

**输出示例**：

```json
{
  "chapter": "volume-1/ch-015",
  "passed": true,
  "score": 85,
  "issues": [],
  "suggestions": ["可在战斗场景增加环境描写"]
}
```

---

### optimize - 全量优化

**用途**：深度优化章节或全书质量

```
/nf optimize [--volume <卷号>] [--chapter <章节号>] [--type <类型>]
```

| 参数    | 类型   | 默认值 | 说明     |
| ------- | ------ | ------ | -------- |
| volume  | number | all    | 目标卷   |
| chapter | number | all    | 目标章   |
| type    | string | full   | 优化类型 |

**优化类型**：

| 类型       | 说明     | 执行内容                     |
| ---------- | -------- | ---------------------------- |
| full       | 全量优化 | 依次执行以下所有优化         |
| style      | 文风优化 | 去AI味道、长短句、描写质感   |
| plot       | 情节优化 | 逻辑矛盾、节奏调整、爽点密度 |
| dialogue   | 对话优化 | 口语化、潜台词、人物性格     |
| battle     | 战斗优化 | 动作紧凑、战术清晰、紧张感   |
| connection | 衔接优化 | 卷间情节连贯、人物状态统一   |

**优化执行链**（full模式）：

```
style → plot → dialogue → battle → connection
  ↓       ↓        ↓         ↓          ↓
去AI味  逻辑矛盾   对话自然  战斗紧凑   衔接流畅
      节奏调整   潜台词     战术清晰
      爽点密度   人物性格
```

---

## 发布阶段

### publish - 发布

**用途**：适配目标平台格式并发布

```
/nf publish --platform <平台> [--format <格式>]
```

| 参数     | 类型   | 默认值 | 说明             |
| -------- | ------ | ------ | ---------------- |
| platform | string | -      | 目标平台（必填） |
| format   | string | auto   | 格式类型         |

**支持平台**：

| 平台       | ID          | 说明       |
| ---------- | ----------- | ---------- |
| 起点中文网 | qidian      | 主流男频   |
| 起点免费   | qidian-free | 免费阅读   |
| 纵横中文网 | zongheng    | 男频老牌   |
| 17K小说网  | 17k         | 玄幻修仙   |
| 晋江文学城 | jinjiang    | 女频主战场 |

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

**用途**：从项目中收集知识、经验、模板，用于后续创作参考

```
/nf learn [--collect] [--from <来源>] [--type <类型>]
```

| 参数    | 类型   | 默认值   | 说明     |
| ------- | ------ | -------- | -------- |
| collect | flag   | false    | 收集知识 |
| from    | string | 当前项目 | 知识来源 |
| type    | string | all      | 知识类型 |

**知识类型**：

| 类型     | 说明     | 示例               |
| -------- | -------- | ------------------ |
| all      | 全量收集 | -                  |
| lesson   | 经验教训 | 某个情节的处理方式 |
| pattern  | 写作模式 | 某类场景的经典写法 |
| template | 创作模板 | 战斗场景模板       |

**执行流程**：

```
collect → organize → index → 可查询
```

---

### query - 知识查询

**用途**：查询已有知识库，用于创作参考

```
/nf query [--query <关键词>] [--type <类型>] [--limit <数量>]
```

| 参数  | 类型   | 默认值 | 说明       |
| ----- | ------ | ------ | ---------- |
| query | string | -      | 搜索关键词 |
| type  | string | all    | 知识类型   |
| limit | number | 5      | 返回数量   |

**输出示例**：

```
[1] 战斗描写模板
    标签：战斗｜动作｜模板
    内容：适用于高强度战斗场景，包含招式名、动作细节、环境互动
    使用场景：主角vs强敌

[2] 角色塑造技巧
    标签：人物｜性格｜技巧
    内容：通过对话和动作展示性格，而非直接描述
    使用场景：配角出场
```

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
