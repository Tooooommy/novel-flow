# Skill: nf-length-planner

## 描述

篇幅规划师技能，负责规划小说的整体篇幅结构、章节划分和字数分配。

## 调用方式

```
/nf-length-planner <command> [options]
```

## 命令

### full

**一键规划完整篇幅**

```
/nf-length-planner full --target <total-words>
```

**执行：** plan → allocate → adjust

---

### plan

制定篇幅规划方案

```
/nf-length-planner plan --target <total-words> [--type <short|medium|long|epic>] [--chapters <count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| target | number | 是 | - | 目标字数 |
| type | string | 否 | - | 篇幅类型 |
| chapters | number | 否 | - | 章节数量 |

---

### allocate

分配各章节字数

```
/nf-length-planner allocate --structure <structure-type> [--ratio <ratio-pattern>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| structure | string | 是 | - | 结构类型 |
| ratio | string | 否 | - | 比例模式 |

---

### adjust

根据进度调整规划

```
/nf-length-planner adjust --current <current-words> --target <target-words> [--phase <current-phase>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| current | number | 是 | - | 当前字数 |
| target | number | 是 | - | 目标字数 |
| phase | string | 否 | - | 当前阶段 |

---

### pace

计算叙事节奏指标

```
/nf-length-planner pace --plot-points <count> [--total-chapters <count>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| plot-points | number | 是 | - | 情节点数量 |
| total-chapters | number | 否 | - | 总章节数 |

## 篇幅类型

- 短篇 (Short): 3-10万字，适合网文短篇/杂志
- 中篇 (Medium): 10-30万字，适合单行本
- 长篇 (Long): 30-100万字，适合系列作品
- 史诗 (Epic): 100万+字，适合大型系列

## 结构模板

- 三幕式结构
- 英雄之旅
- 章节小说结构
- 多线叙事结构

## 输出格式

规划报告包含：

- 总字数目标与章节数
- 各卷/部字数分配
- 关键情节点位置
- 节奏曲线建议
