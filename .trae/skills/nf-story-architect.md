---
name: nf-story-architect
description: |
  故事架构技能。为 `/nf outline` 命令提供能力。
  当用户要生成小说大纲、设计世界观、创建人物设定、规划分卷结构时使用。
  整合世界观构建、人物设计、篇幅规划功能。
---

# 故事架构技能

## 使用场景

- 用户要生成小说大纲
- 用户要设计世界观设定
- 用户要创建人物设定
- 用户要生成分卷大纲

---

## 命令

### full - 生成完整大纲

```
/nf-story-architect full [--genre <题材>] [--chapters <数量>] [--volumes <卷数>]
```

| 参数     | 类型   | 必填 | 默认值   | 说明       |
| -------- | ------ | ---- | -------- | ---------- |
| genre    | string | 否   | 当前项目 | 题材类型   |
| chapters | number | 否   | 30       | 每卷章节数 |
| volumes  | number | 否   | 3        | 分卷数量   |

**执行**: world → characters → structure → outline → volumes

**输出**:

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

## 内部命令

### world - 构建世界观

```
/nf-story-architect world [--genre <题材>] [--scale <规模>]
```

### characters - 设计人物

```
/nf-story-architect characters [--count <数量>]
```

### structure - 篇章结构

```
/nf-story-architect structure [--volumes <卷数>] [--chapters <总章节>]
```

### outline - 生成大纲

```
/nf-story-architect outline [--framework <框架>] [--theme <主题>]
```

### volumes - 生成分卷

```
/nf-story-architect volumes [--count <卷数>]
```

---

## 错误处理

| 错误码 | 说明     | 处理方式     |
| ------ | -------- | ------------ |
| SA-001 | 题材为空 | 使用默认题材 |
| SA-002 | 卷数无效 | 默认3卷      |
