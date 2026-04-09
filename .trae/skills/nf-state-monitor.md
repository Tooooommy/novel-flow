# Skill: nf-state-monitor

## 描述
小说创作流程的状态监控器，实时跟踪创作流程的整体状态、各阶段进度和关键指标。

## 调用方式
```
/nf-state-monitor <command> [options]
```

## 命令

### status
获取当前创作流程整体状态
```
/nf-state-monitor status [--detail]
```

### progress
查看指定阶段进度
```
/nf-state-monitor progress --phase <phase-name>
```

### metrics
查看关键创作指标
```
/nf-state-monitor metrics [--category <creative|quality|efficiency>]
```

### checkpoint
创建状态检查点
```
/nf-state-monitor checkpoint --name <checkpoint-name> [--note <description>]
```

### compare
比较不同检查点的状态差异
```
/nf-state-monitor compare <checkpoint-1> <checkpoint-2>
```

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
