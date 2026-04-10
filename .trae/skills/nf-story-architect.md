# Skill: nf-story-architect

## 描述

故事架构师技能，负责设计小说的整体故事结构、情节线和叙事框架。

## 调用方式

```
/nf-story-architect <command> [options]
```

## 命令

### full

**一键设计完整故事架构**

```
/nf-story-architect full --concept <concept>
```

**执行：** framework → outline → plotline → beats → tension

---

### framework

选择并定制故事框架

```
/nf-story-architect framework --type <three-act|hero-journey|save-the-cat|freytag|kishotenketsu>
```

### outline

生成故事大纲

```
/nf-story-architect outline --concept <concept> [--acts <count>] [--twists <count>]
```

### plotline

设计情节线

```
/nf-story-architect plotline --main <main-plot> [--subplots <subplot-list>]
```

### beats

安排情节点

```
/nf-story-architect beats --framework <framework> [--count <beat-count>]
```

### tension

设计张力曲线

```
/nf-story-architect tension --story <story-outline> [--peaks <peak-count>]
```

### structure

验证结构完整性

```
/nf-story-architect structure --outline <outline>
```

## 故事框架

- 三幕式结构 (Three-Act Structure)
- 英雄之旅 (Hero's Journey)
- Save the Cat 节拍表
- 弗莱塔格金字塔 (Freytag's Pyramid)
- 起承转合 (Kishotenketsu)

## 输出格式

架构文档包含：

- 故事框架说明
- 分幕/分章大纲
- 情节点清单
- 张力曲线图
- 结构完整性评估
