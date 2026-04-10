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

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| type | string | 是 | - | 框架类型 |

---

### outline

生成故事大纲

```
/nf-story-architect outline --concept <concept> [--acts <count>] [--twists <count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| concept | string | 是 | - | 故事概念 |
| acts | number | 否 | 3 | 幕数 |
| twists | number | 否 | - | 反转数量 |

---

### plotline

设计情节线

```
/nf-story-architect plotline --main <main-plot> [--subplots <subplot-list>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| main | string | 是 | - | 主线情节 |
| subplots | string | 否 | - | 支线列表 |

---

### beats

安排情节点

```
/nf-story-architect beats --framework <framework> [--count <beat-count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| framework | string | 是 | - | 故事框架 |
| count | number | 否 | 15 | 节拍数量 |

---

### tension

设计张力曲线

```
/nf-story-architect tension --story <story-outline> [--peaks <peak-count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| story | string | 是 | - | 故事大纲 |
| peaks | number | 否 | - | 高潮数量 |

---

### structure

验证结构完整性

```
/nf-story-architect structure --outline <outline>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| outline | string | 是 | - | 大纲内容 |

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
