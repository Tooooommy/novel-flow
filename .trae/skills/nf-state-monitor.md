# Skill: nf-state-monitor

## 描述

小说创作流程的状态监控器，实时跟踪创作流程的整体状态、各阶段进度和关键指标。

## 调用方式

```
/nf-state-monitor <command> [options]
```

## 命令

### full

**一键完整状态监控**

```
/nf-state-monitor full
```

**执行：** status → progress → metrics

---

### status

获取当前创作流程整体状态

```
/nf-state-monitor status [--detail]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| detail | boolean | 否 | false | 是否显示详细信息 |

---

### progress

查看指定阶段进度

```
/nf-state-monitor progress --phase <phase-name>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| phase | string | 是 | - | 阶段名称 |

---

### metrics

查看关键创作指标

```
/nf-state-monitor metrics [--category <creative|quality|efficiency>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| category | string | 否 | - | 指标类别 |

---

### checkpoint

创建状态检查点

```
/nf-state-monitor checkpoint --name <checkpoint-name> [--note <description>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| name | string | 是 | - | 检查点名称 |
| note | string | 否 | - | 检查点描述 |

---

### compare

比较不同检查点的状态差异

```
/nf-state-monitor compare <checkpoint-1> <checkpoint-2>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| checkpoint-1 | string | 是 | - | 检查点1 |
| checkpoint-2 | string | 是 | - | 检查点2 |

## 监控指标

- 创作进度完成率
- 各阶段耗时统计
- 质量评分趋势
- 阻塞任务数量
- 返工率统计

## 输出格式

状态报告包含：

- 当前阶段概览
- 进度可视化（文本进度条）
- 异常/风险提示
- 下一步建议
