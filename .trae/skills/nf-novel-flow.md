---
name: nf-novel-flow
description: |
  NovelFlow小说创作AI工厂主控技能。当用户要创作小说、写小说大纲、生成章节内容、审查优化小说内容时触发。
  支持8个核心命令：idea(创意)、init(立项)、outline(大纲)、write(写作)、review(审查)、optimize(优化)、publish(发布)、auto(自动化)。
---

# NovelFlow 小说创作主控技能

## 使用场景

- 用户要创作新小说
- 用户要生成小说大纲（含分卷大纲）
- 用户要生成章节正文
- 用户要审查/优化小说内容
- 用户不知道写什么，需要创意建议
- 用户要一键自动化完成整本小说创作

---

## 核心命令

### idea - 创意探索

生成多个创意方案供用户选择

```
/nf idea [--count <数量>] [--genre <题材>]
```

| 参数  | 类型   | 必填 | 默认值 | 说明     |
| ----- | ------ | ---- | ------ | -------- |
| count | number | 否   | 5      | 创意数量 |
| genre | string | 否   | -      | 题材方向 |

**示例输出**:

```
[1] 都市修仙：废物逆袭，校花倒贴
    标签：都市｜修仙｜热血｜爽文
    亮点：身份反差+系统流

[2] 异世穿越：成为史上最弱召唤师
    标签：奇幻｜穿越｜召唤流
    亮点：反套路+宠物成长
```

---

### init - 项目立项

创建新小说项目

```
/nf init --name <名称> --genre <题材> [--target <字数>]
```

| 参数   | 类型   | 必填 | 默认值 | 说明     |
| ------ | ------ | ---- | ------ | -------- |
| name   | string | 是   | -      | 小说名称 |
| genre  | string | 是   | -      | 题材类型 |
| target | number | 否   | 100000 | 目标字数 |

---

### outline - 大纲生成

生成总大纲和分卷大纲

```
/nf outline [--chapters <数量>] [--volumes <卷数>]
```

| 参数     | 类型   | 必填 | 默认值 | 说明       |
| -------- | ------ | ---- | ------ | ---------- |
| chapters | number | 否   | 30     | 每卷章节数 |
| volumes  | number | 否   | 3      | 分卷数量   |

**输出结构**:

```
novels/{project}/
├── outline.md      # 总大纲
├── characters.md   # 人物设定
├── world.md       # 世界观设定
├── volume-1.md    # 第一卷大纲
├── volume-2.md    # 第二卷大纲
└── volume-3.md    # 第三卷大纲
```

---

### write - 创作写作

按分卷创作，自动审查循环，支持串行和并行两种模式

```
/nf write [--volume <卷号>] [--chapter <章节号>] [--mode <模式>]
```

| 参数    | 类型   | 必填 | 默认值 | 说明     |
| ------- | ------ | ---- | ------ | -------- |
| volume  | number | 否   | 1      | 分卷号   |
| chapter | number | 否   | 1      | 章节号   |
| mode    | string | 否   | serial | 创作模式 |

**创作模式**:

- `serial`: 串行模式，按卷按章顺序创作
- `parallel`: 并行模式，多卷同时创作

**串行创作流程**:

```
Volume 1 → Chapter 1 → 审查 → 下一章 → ... → Volume 2 → ...
                                                    ↓
                                              换卷衔接优化
```

**并行创作流程**:

```
┌─ Volume 1 ──┬─ Volume 2 ──┬─ Volume 3 ──┐
│  Chapter 1  │  Chapter 1  │  Chapter 1   │ ← 同时创作
│  Chapter 2  │  Chapter 2  │  Chapter 2   │
│  ...        │  ...        │  ...         │
└─────────────┴─────────────┴─────────────┘
                    ↓
              卷间衔接优化（最后）
```

---

### review - 内容审查

审查章节：逻辑、合规、质量

```
/nf review [--chapter <章节号>]
```

| 参数    | 类型   | 必填 | 默认值 | 说明   |
| ------- | ------ | ---- | ------ | ------ |
| chapter | number | 否   | 当前   | 章节号 |

**审查输出**:

```json
{
  "logic": { "passed": true, "issues": [] },
  "compliance": { "passed": true, "issues": [] },
  "quality": { "score": 85, "passed": true }
}
```

---

### optimize - 全量优化

对全书进行风格、情节、对话、战斗、衔接优化

```
/nf optimize [--volume <卷号>] [--chapter <章节号>] [--type <类型>]
```

| 参数    | 类型   | 必填 | 默认值 | 说明     |
| ------- | ------ | ---- | ------ | -------- |
| volume  | number | 否   | 全部   | 分卷号   |
| chapter | number | 否   | 全部   | 章节号   |
| type    | string | 否   | full   | 优化类型 |

**优化类型**:

- `full`: 全量优化（style→plot→dialogue→battle→connection）
- `style`: 文风优化（去AI味道）
- `plot`: 情节优化
- `dialogue`: 对话优化
- `battle`: 战斗描写优化
- `connection`: 卷间衔接优化

**执行流程**:

```
style → plot → dialogue → battle → connection
   ↓        ↓         ↓         ↓           ↓
去AI味道  逻辑矛盾   对话自然  战斗紧凑    衔接流畅
        节奏调整   潜台词     战术清晰
        爽点密度   人物性格
```

---

### publish - 发布

平台适配并发布

```
/nf publish --platform <平台>
```

| 参数     | 类型   | 必填 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| platform | string | 是   | -      | 目标平台 |

**支持平台**: qidian, qidian-free, zongheng, 17k, jinjiang

---

### auto - 自动化创作

一键自动化完成整本小说创作（立项→大纲→写作→审查→发布）

```
/nf auto --name <名称> --genre <题材> [--platform <平台>] [--chapters <数量>] [--volumes <卷数>] [--mode <模式>]
```

| 参数     | 类型   | 必填 | 默认值   | 说明       |
| -------- | ------ | ---- | -------- | ---------- |
| name     | string | 是   | -        | 小说名称   |
| genre    | string | 是   | -        | 题材类型   |
| platform | string | 否   | -        | 发布平台   |
| chapters | number | 否   | 30       | 每卷章节数 |
| volumes  | number | 否   | 3        | 分卷数量   |
| mode     | string | 否   | parallel | 创作模式   |

**创作模式**:

- `serial`: 串行模式，按卷按章顺序创作
- `parallel`: 并行模式，多卷同时创作（默认）

**自动化流程（并行模式）**:

```
┌─────────────────────────────────────────────────────────────┐
│ init → outline                                             │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌───────────────┬───────────────┬───────────────┐
│  Volume 1     │  Volume 2     │  Volume 3     │
│  Chapter 1    │  Chapter 1    │  Chapter 1    │ ← 并行创作
│  Chapter 2    │  Chapter 2    │  Chapter 2    │
│  ...          │  ...          │  ...          │
└───────────────┴───────────────┴───────────────┘
                              ↓
              optimize --type connection（衔接优化）
                              ↓
                     optimize --type full（全量优化）
                              ↓
                       [publish]（可选）
```

**状态输出（并行模式）**:

```
[1/5] 初始化项目: 逆天剑尊
[2/5] 生成大纲: 3卷 × 30章 = 90章
[3/5] 并行创作中: [V1: Ch15/30] [V2: Ch12/30] [V3: Ch10/30]
[4/5] 全量优化: connection → style → plot → dialogue → battle
[5/5] 发布: qidian
```

**执行模式**:

- **完全自动化**: 提供所有参数，自动完成整个流程
- **半自动化**: 省略参数使用默认值，中途可干预
- **增量模式**: 检测已完成的章节，跳过继续

**状态输出**:

```
[1/5] 初始化项目: 逆天剑尊
[2/5] 生成大纲: 3卷 × 30章 = 90章
[3/5] 创作中: Volume 1/3, Chapter 15/30
[4/5] 全量优化: style → plot → dialogue → battle → connection
[5/5] 发布: qidian
```

---

## 错误处理

| 错误码 | 说明       | 处理方式           |
| ------ | ---------- | ------------------ |
| NF-001 | 项目不存在 | 提示先执行 init    |
| NF-002 | 大纲不存在 | 提示先执行 outline |
| NF-003 | 章节不存在 | 自动创建           |
| NF-004 | 平台不支持 | 使用通用格式       |
| NF-005 | 自动化失败 | 回滚到手动流程     |
| NF-006 | 创作中断   | 支持断点续传       |
