---
name: nf-content-generator
description: |
  内容生成技能。为 `/nf write` 命令提供能力。
  当用户要生成小说章节正文、创作场景描写、编写对话、设计动作场景时使用。
  整合节奏设计、场景、对话、描写、动作、情感生成功能。
---

# 内容生成技能

## 使用场景

- 用户要生成章节正文
- 用户要创作特定场景
- 用户要编写对话
- 用户要生成动作/战斗场景
- 用户要生成情感场景

---

## 命令

### full - 生成章节正文

```
/nf-content-generator full --volume <卷号> --chapter <章节号> [--previous <上章摘要>]
```

| 参数     | 类型   | 必填 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| volume   | number | 是   | -      | 分卷号   |
| chapter  | number | 是   | -      | 章节号   |
| previous | string | 否   | -      | 上章摘要 |

**执行**: pacing → scene → dialogue → description → action → emotion

**智能行为**:

- 自动衔接上章结尾
- 自动去AI味道
- 节奏控制

---

## 内部命令

### pacing - 节奏设计

```
/nf-content-generator pacing --outline <大纲> --type <类型>
```

### scene - 生成场景

```
/nf-content-generator scene --outline <大纲> --setting <背景>
```

### dialogue - 生成对话

```
/nf-content-generator dialogue --context <上下文> --characters <角色>
```

### description - 生成描写

```
/nf-content-generator description --subject <对象> --type <类型>
```

### action - 生成动作

```
/nf-content-generator action --event <事件> --intensity <强度>
```

### emotion - 生成情感

```
/nf-content-generator emotion --character <角色> --context <上下文>
```

---

## 错误处理

| 错误码 | 说明     | 处理方式   |
| ------ | -------- | ---------- |
| CG-001 | 大纲为空 | 自动生成   |
| CG-002 | 卷号无效 | 使用第一卷 |
