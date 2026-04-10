# Skill: nf-specialist-optimizer

## 描述

专业优化师技能，为 `/nf optimize` 命令提供内容优化能力。支持文风、情节、对话、战斗、卷间衔接优化。

## 调用方式

由主控技能 `/nf optimize` 调用，无需直接使用。

---

## full

**全量优化**

```
/nf-specialist-optimizer full --chapter <章节号> [--volume <卷号>]
```

**执行：** style → plot → dialogue → battle → connection

---

## style

**文风优化** - 去AI味道

```
/nf-specialist-optimizer style --chapter <章节号>
```

**优化内容**:

- 删除过度解释性词语
- 替换机械化副词
- 情绪用身体反应而非直接陈述
- 对话口语化，允许不完整
- 长短句交错

---

## plot

**情节优化** - 逻辑/节奏

```
/nf-specialist-optimizer plot --chapter <章节号>
```

**优化内容**:

- 检查逻辑矛盾
- 调整节奏快慢
- 优化爽点密度
- 增强情感张力

---

## dialogue

**对话优化** - 口语化/潜台词

```
/nf-specialist-optimizer dialogue --chapter <章节号>
```

**优化内容**:

- 对话符合人物性格
- 增加潜台词
- 优化对话节奏
- 去除AI感

---

## battle

**战斗描写优化**

```
/nf-specialist-optimizer battle --chapter <章节号>
```

**优化内容**:

- 动作描写紧凑
- 战术逻辑清晰
- 紧张感营造
- 胜负合理

---

## connection

**卷间衔接优化**

```
/nf-specialist-optimizer connection --volume <卷号>
```

**优化内容**:

- 衔接上卷结尾情节
- 统一全卷文风
- 调整人物状态连贯性
- 修复伏笔呼应

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| SO-001 | 章节不存在 | 跳过优化   |
| SO-002 | 卷号无效   | 使用当前卷 |
