# Skill: nf-market-analyzer

## 描述

市场分析师技能，负责分析小说市场趋势、读者偏好和竞品情况，为创作决策提供数据支持。

## 调用方式

```
/nf-market-analyzer <command> [options]
```

## 命令

### full

**一键完整市场分析**

```
/nf-market-analyzer full --genre <genre>
```

**执行：** genre → audience → compete

---

### genre

分析特定类型市场

```
/nf-market-analyzer genre <genre-name> [--period <3m|6m|1y|all>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| genre | string | 是 | - | 类型名称 |
| period | string | 否 | 6m | 分析周期 |

---

### audience

分析目标读者群体

```
/nf-market-analyzer audience [--genre <genre>] [--demographic <age-group>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| genre | string | 否 | - | 题材类型 |
| demographic | string | 否 | - | 年龄群体 |

---

### compete

竞品分析报告

```
/nf-market-analyzer compete --title <book-title> [--similar <count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| title | string | 是 | - | 书籍标题 |
| similar | number | 否 | 5 | 相似作品数 |

---

### gap

发现市场空白机会

```
/nf-market-analyzer gap [--genre <genre>] [--theme <theme>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| genre | string | 否 | - | 题材类型 |
| theme | string | 否 | - | 主题要素 |

---

### predict

预测趋势走向

```
/nf-market-analyzer predict --aspect <aspect> [--horizon <short|medium|long>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| aspect | string | 是 | - | 预测方面 |
| horizon | string | 否 | medium | 预测周期 |

## 分析维度

- 热门题材排行
- 读者评分分布
- 评论情感分析
- 价格区间分析
- 更新频率影响
- 平台差异对比

## 输出格式

市场报告包含：

- 市场概况摘要
- 数据可视化（文本图表）
- 机会点识别
- 风险提示
- 策略建议
