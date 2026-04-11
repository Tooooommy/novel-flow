# NovelFlow 小说创作AI工厂

## 核心哲学

**三阶段流程**：立项(种子) → 创作(生成) → 发布(收获)

- 命令设计遵循「渐进式披露」原则：简单命令隐藏复杂参数
- 增量优先：自动检测已有内容，跳过完成部分
- 并行优先：多卷同时创作，节省时间

---

## 快速开始

```bash
# 方式一：一键自动化（推荐新手）
/nf auto --name 我的小说 --genre 玄幻 --target 8000000

# 方式二：分步创作（推荐有经验者）
/nf init --name 我的小说 --genre 玄幻 --target 8000000
/nf architect
/nf write --volume 1 --chapter 1
/nf review
/nf optimize
/nf publish --platform qidian
```

---

## 主控命令

```mermaid
flowchart LR
    A[idea] --> B[init] --> C[architect] --> D[write] --> E[review] --> F[optimize] --> G[publish]
```

| 命令 | 必填参数 | 可选参数 | 说明 |
|------|----------|----------|------|
| `/nf idea` | - | count, genre | 创意探索 |
| `/nf init` | name, genre, target | chapter-size | 项目立项 |
| `/nf architect` | - | metadata | 大纲生成 |
| `/nf write` | - | volume, chapter, style | 创作写作 |
| `/nf review` | - | chapter, volume | 内容审查 |
| `/nf optimize` | - | volume, chapter, type | 全量优化 |
| `/nf publish` | platform | chapter, volume | 发布 |
| `/nf analyze` | - | mode | 流程分析 |
| `/nf detect` | - | project | 进度探测 |
| `/nf auto` | name, genre, target | chapter-size, platform, mode | 一键自动化 |
| `/nf learn` | - | collect, from, type | 知识学习 |
| `/nf query` | - | query, type, limit | 知识查询 |

---

## 子技能

| 技能 | 命令前缀 | 功能 |
|------|----------|------|
| [nf-idea-explorer](skills/nf-idea-explorer/SKILL.md) | `/nf ie` | 趋势分析、概念生成、创新添加 |
| [nf-project-init](skills/nf-project-init/SKILL.md) | `/nf init` | 项目结构初始化 |
| [nf-story-architect](skills/nf-story-architect/SKILL.md) | `/nf architect` | 世界观、人物、结构、大纲、分卷 |
| [nf-content-generator](skills/nf-content-generator/SKILL.md) | `/nf write` | 风格应用、节奏设计、内容生成 |
| [nf-specialist-optimizer](skills/nf-specialist-optimizer/SKILL.md) | `/nf optimize` | 文风/情节/对话/战斗优化 |
| [nf-quality-assessor](skills/nf-quality-assessor/SKILL.md) | `/nf review` | 质量评估 |
| [nf-logic-inspector](skills/nf-logic-inspector/SKILL.md) | `/nf review` | 逻辑审查 |
| [nf-compliance-officer](skills/nf-compliance-officer/SKILL.md) | `/nf review` | 合规审查 |
| [nf-platform-adapter](skills/nf-platform-adapter/SKILL.md) | `/nf publish` | 平台适配 |
| [nf-process-analyst](skills/nf-process-analyst/SKILL.md) | `/nf analyze` | 流程分析 |
| [nf-knowledge-curator](skills/nf-knowledge-curator/SKILL.md) | `/nf learn/query` | 知识管理 |

---

## 干预节点

| 节点 | 触发时机 | 干预方式 | 超时处理 |
|------|----------|----------|----------|
| N1 创意确认 | idea完成后 | 选择/修改/重新生成 | 自动通过推荐 |
| N2 大纲确认 | architect完成后 | 确认/修改/补充 | 暂停等待 |
| N3 人物确认 | 人物档案生成后 | 确认/调整/新增 | 自动确认 |
| N4 章节审核 | 每章创作完成 | 通过/打回/跳过 | 自动通过(>70分) |

---

## 内置创作风格

| 作家 | 风格 | 适用场景 |
|------|------|----------|
| 猫腻 | 文青伏笔流 | 权谋、慢热、智斗 |
| 辰东 | 史诗热血流 | 玄幻、热血、战斗 |
| 天蚕土豆 | 升级爽文流 | 升级、打脸、爽文 |
| 唐家三少 | 简洁小白流 | 小白文、通俗易懂 |
| 我吃西红柿 | 流畅热血流 | 流畅、战斗、情感 |
| 愤怒的香蕉 | 沉稳细腻流 | 权谋、细腻、文学性 |

---

## 质量门禁

| 检查阶段 | 门禁条件 | 不通过处理 | 超时处理 |
|----------|----------|------------|----------|
| 立项 | 创意评分≥80 | 重新生成 | 自动通过 |
| 大纲 | 结构完整 | 补充大纲 | 暂停等待 |
| 人物 | 人物立体 | 完善设定 | 自动确认 |
| 章节 | 质量评分≥80 | 优化重审 | 自动通过(>80) |
| 优化 | 达标分数≥85 | 再次优化 | 保留原版 |
| 发布 | 合规检查 | 修改内容 | 暂停发布 |

---

## auto 一键自动化

```
[1/6] init        → 创建项目结构
[2/6] architect   → 生成大纲体系
[3/6] write       → 并行创作正文
[4/6] optimize    → 衔接优化
[5/6] optimize    → 全量优化
[6/6] publish     → 平台发布（可选）
```

---

## 目录结构

```
skills/
├── nf-novel-flow/          # 主控技能
├── nf-idea-explorer/       # 创意探索
├── nf-project-init/        # 项目立项
├── nf-story-architect/     # 故事架构
├── nf-content-generator/   # 内容生成
├── nf-specialist-optimizer/ # 专业优化
├── nf-quality-assessor/    # 质量评估
├── nf-logic-inspector/     # 逻辑审查
├── nf-compliance-officer/  # 合规审查
├── nf-platform-adapter/    # 平台适配
├── nf-process-analyst/     # 流程分析
└── nf-knowledge-curator/   # 知识管理
```
