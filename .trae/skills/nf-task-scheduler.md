# Skill: nf-task-scheduler

## 描述

小说创作流程的任务调度器，负责管理创作流程中各阶段的任务分配、优先级排序和依赖关系处理。

## 调用方式

```
/nf-task-scheduler <command> [options]
```

## 命令

### full

**一键完整任务调度**

```
/nf-task-scheduler full --phase <phase>
```

**执行：** schedule → list → update

---

### schedule

创建并调度新任务

```
/nf-task-scheduler schedule --phase <phase> --task <task> --priority <high|medium|low> [--depends-on <task-id>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| phase | string | 是 | - | 所属阶段 |
| task | string | 是 | - | 任务描述 |
| priority | string | 是 | - | 优先级 |
| depends-on | string | 否 | - | 依赖任务ID |

---

### list

列出当前所有任务状态

```
/nf-task-scheduler list [--phase <phase>] [--status <pending|in-progress|completed>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| phase | string | 否 | - | 阶段名称 |
| status | string | 否 | - | 任务状态 |

---

### update

更新任务状态

```
/nf-task-scheduler update <task-id> --status <status> [--result <result-summary>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| task-id | string | 是 | - | 任务ID |
| status | string | 是 | - | 新状态 |
| result | string | 否 | - | 结果摘要 |

---

### deps

分析任务依赖关系

```
/nf-task-scheduler deps --phase <phase>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| phase | string | 是 | - | 阶段名称 |

## 工作流集成

- 在 Plan 阶段定义任务依赖图
- 在 Build 阶段按优先级执行任务
- 在 Review 阶段检查任务完成度

## 输出格式

任务状态报告以 Markdown 表格形式输出，包含：

- 任务ID
- 阶段
- 任务描述
- 优先级
- 状态
- 依赖任务
- 预计/实际耗时
