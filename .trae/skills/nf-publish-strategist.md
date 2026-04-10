# Skill: nf-publish-strategist

## 描述

发布策略师技能，负责制定小说的发布策略、更新计划和推广方案。

## 调用方式

```
/nf-publish-strategist <command> [options]
```

## 命令

### full

**一键制定完整发布策略**

```
/nf-publish-strategist full --novel <novel-info>
```

**执行：** schedule → strategy → promote

---

### schedule

制定发布计划

```
/nf-publish-strategist schedule --chapters <count> [--start-date <date>] [--frequency <freq>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| chapters | number | 是 | - | 章节数量 |
| start-date | string | 否 | - | 开始日期 |
| frequency | string | 否 | - | 更新频率 |

---

### strategy

制定整体策略

```
/nf-publish-strategist strategy --novel <novel-info> [--goal <goal-type>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| novel | string | 是 | - | 小说信息 |
| goal | string | 否 | - | 目标类型 |

---

### promote

设计推广方案

```
/nf-publish-strategist promote --novel <novel-info> --budget <budget-level>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| novel | string | 是 | - | 小说信息 |
| budget | string | 是 | - | 预算级别 |

---

### pricing

定价策略

```
/nf-publish-strategist pricing --novel <novel-info> --platform <platform>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| novel | string | 是 | - | 小说信息 |
| platform | string | 是 | - | 平台名称 |

---

### analyze

竞品发布分析

```
/nf-publish-strategist analyze --competitors <competitor-list>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| competitors | string | 是 | - | 竞品列表 |

## 策略类型

- 网文连载策略
- 实体出版策略
- 自出版策略
- 多平台同步策略
- IP开发策略

## 发布节奏

- 新书期：日更/双更
- 稳定期：日更/隔日更
- 高潮期：加更爆更
- 完本期：完结推广

## 输出格式

策略报告包含：

- 发布时间表
- 更新频率建议
- 推广节点规划
- 预期效果预测
- 风险预案
