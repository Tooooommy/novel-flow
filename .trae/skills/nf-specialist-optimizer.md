---
name: nf-specialist-optimizer
description: |
  专业优化技能。为 `/nf optimize` 命令提供能力。
  当用户要优化章节内容、去AI味道、优化对话、优化战斗描写、处理卷间衔接时使用。
  整合文风、情节、对话、战斗、衔接优化功能。
---

# 专业优化技能

## 使用场景

- 用户要优化章节内容
- 用户觉得文章有AI味道
- 用户要优化对话
- 用户要优化战斗描写
- 用户要优化卷间衔接

---

## 命令

### full - 全量优化

```
/nf-specialist-optimizer full [--chapter <章节号>] [--volume <卷号>]
```

| 参数    | 类型   | 必填 | 默认值 | 说明   |
| ------- | ------ | ---- | ------ | ------ |
| chapter | number | 否   | 当前   | 章节号 |
| volume  | number | 否   | 当前   | 分卷号 |

**执行**: style → plot → dialogue → battle → connection

---

## 内部命令

### style - 文风优化

```
/nf-specialist-optimizer style [--chapter <章节号>]
```

**去AI味道**:

- 删除过度解释性词语
- 替换机械化副词
- 情绪用身体反应
- 对话口语化
- 长短句交错

### plot - 情节优化

```
/nf-specialist-optimizer plot [--chapter <章节号>]
```

**内容**:

- 检查逻辑矛盾
- 调整节奏快慢
- 优化爽点密度

### dialogue - 对话优化

```
/nf-specialist-optimizer dialogue [--chapter <章节号>]
```

**内容**:

- 对话符合人物性格
- 增加潜台词
- 优化对话节奏

### battle - 战斗优化

```
/nf-specialist-optimizer battle [--chapter <章节号>]
```

**内容**:

- 动作紧凑
- 战术清晰
- 紧张感

### connection - 卷间衔接

```
/nf-specialist-optimizer connection [--volume <卷号>]
```

**内容**:

- 衔接上卷情节
- 统一文风
- 人物状态连贯

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| SO-001 | 章节不存在 | 跳过优化   |
| SO-002 | 卷号无效   | 使用当前卷 |
