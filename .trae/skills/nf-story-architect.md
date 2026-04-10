# Skill: nf-story-architect

## 描述

故事架构师技能，为 `/nf outline` 命令提供大纲设计能力。整合世界观、人物、篇幅、大纲生成。

## 调用方式

由主控技能 `/nf outline` 调用，无需直接使用。

---

## full

**生成完整大纲** - 含总分卷结构

```
/nf-story-architect full --genre <题材> --chapters <数量> --volumes <卷数>
```

**执行：** world → characters → structure → outline → volumes

**输出结构**:

```
novels/{project}/
├── outline.md          # 总大纲
├── characters.md       # 人物设定
├── world.md           # 世界观设定
├── volume-1.md        # 第一卷大纲
├── volume-2.md        # 第二卷大纲
└── volume-3.md        # 第三卷大纲
```

---

## 内部子命令

### world

**构建世界观**

```
/nf-story-architect world --genre <题材> --scale <规模>
```

### characters

**设计人物**

```
/nf-story-architect characters --count <数量> --type <类型>
```

### structure

**篇章结构**

```
/nf-story-architect structure --volumes <卷数> --chapters <总章节>
```

### outline

**生成大纲**

```
/nf-story-architect outline --framework <框架> --theme <主题>
```

### volumes

**生成分卷**

```
/nf-story-architect volumes --count <卷数> --outline <总纲>
```

---

## 错误处理

| 错误码 | 说明     | 处理方式     |
| ------ | -------- | ------------ |
| SA-001 | 题材为空 | 使用默认题材 |
| SA-002 | 卷数无效 | 默认3卷      |
