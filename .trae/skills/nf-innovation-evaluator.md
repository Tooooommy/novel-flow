# Skill: nf-innovation-evaluator

## 描述

创新评估师技能，负责评估创意的新颖性、可行性和市场潜力，筛选最优创意方向。

## 调用方式

```
/nf-innovation-evaluator <command> [options]
```

## 命令

### full

**一键完整创意评估**

```
/nf-innovation-evaluator full --idea <idea-description>
```

**执行：** score → risk → compare

---

### score

对创意进行多维度评分

```
/nf-innovation-evaluator score --idea <idea-description> [--criteria <criteria-list>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| idea | string | 是 | - | 创意描述 |
| criteria | string | 否 | - | 评估标准 |

---

### compare

对比多个创意方案

```
/nf-innovation-evaluator compare --ideas <idea1;idea2;idea3...>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| ideas | string | 是 | - | 创意列表（分号分隔） |

---

### risk

评估创意风险

```
/nf-innovation-evaluator risk --idea <idea-description> [--market <market-context>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| idea | string | 是 | - | 创意描述 |
| market | string | 否 | - | 市场背景 |

---

### feasibility

可行性分析

```
/nf-innovation-evaluator feasibility --idea <idea-description> [--resources <resource-constraints>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| idea | string | 是 | - | 创意描述 |
| resources | string | 否 | - | 资源限制 |

---

### recommend

推荐最佳创意

```
/nf-innovation-evaluator recommend --ideas <idea-list> [--goal <goal-description>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| ideas | string | 是 | - | 创意列表 |
| goal | string | 否 | - | 目标描述 |

## 评估维度

- 新颖性 (Novelty): 1-10分
- 可行性 (Feasibility): 1-10分
- 市场潜力 (Market Potential): 1-10分
- 创作难度 (Difficulty): 1-10分
- 差异化 (Differentiation): 1-10分
- 延展性 (Scalability): 1-10分

## 输出格式

评估报告包含：

- 综合评分雷达图（文本形式）
- 各维度详细分析
- SWOT分析
- 最终推荐等级
