# Skill: nf-content-generator

## 描述

内容生成师技能，为 `/nf write` 命令提供正文创作能力。按分卷创作，自动衔接上下章节，应用文风设置和节奏控制。

## 调用方式

由主控技能 `/nf write` 调用，无需直接使用。

---

## full

**生成章节正文**

```
/nf-content-generator full --volume <卷号> --chapter <章节号> [--previous <上章摘要>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| volume | number | 是 | - | 分卷号 |
| chapter | number | 是 | - | 章节号 |
| previous | string | 否 | - | 上章摘要（用于衔接） |

**执行：** pacing → scene → dialogue → description → action → emotion

**智能行为**:

- 自动衔接上章结尾情节
- 自动应用去AI味道写作技巧
- 节奏控制（张弛有度）

---

## 内部子命令

### pacing

**设计章节节奏**

```
/nf-content-generator pacing --outline <章节大纲> --type <类型>
```

### scene

**生成场景**

```
/nf-content-generator scene --outline <场景大纲> --setting <背景>
```

### dialogue

**生成对话**

```
/nf-content-generator dialogue --context <上下文> --characters <角色列表>
```

### description

**生成描写**

```
/nf-content-generator description --subject <对象> --type <类型>
```

### action

**生成动作**

```
/nf-content-generator action --event <事件> --intensity <强度>
```

### emotion

**生成情感场景**

```
/nf-content-generator emotion --character <角色> --context <上下文>
```

---

## 错误处理

| 错误码 | 说明     | 处理方式         |
| ------ | -------- | ---------------- |
| CG-001 | 大纲为空 | 自动生成简略大纲 |
| CG-002 | 卷号无效 | 使用第一卷       |
