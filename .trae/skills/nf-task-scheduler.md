# Skill: nf-task-scheduler

## 元数据

- **技能ID**: skill-process-002
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-process-coordinator

---

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

### list

列出当前所有任务状态

```
/nf-task-scheduler list [--phase <phase>] [--status <pending|in-progress|completed>]
```

### update

更新任务状态

```
/nf-task-scheduler update <task-id> --status <status> [--result <result-summary>]
```

### deps

分析任务依赖关系

```
/nf-task-scheduler deps --phase <phase>
```

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
