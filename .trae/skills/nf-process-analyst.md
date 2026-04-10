# Skill: nf-process-analyst

## 描述
流程分析员技能，负责分析小说创作流程的效率、瓶颈和改进空间。

## 调用方式
```
/nf-process-analyst <command> [options]
```

## 命令

### full ⭐NEW
**一键完整流程分析**
```
/nf-process-analyst full --logs <process-logs>
```
**执行：** analyze → bottleneck → efficiency

---

### analyze
流程效率分析
```
/nf-process-analyst analyze --logs <process-logs> [--metrics <metric-list>]
```

### bottleneck
识别瓶颈
```
/nf-process-analyst bottleneck --timeline <phase-timeline>
```

### efficiency
效率评估
```
/nf-process-analyst efficiency --data <process-data> [--compare <benchmark>]
```

### report
生成分析报告
```
/nf-process-analyst report --project <project-id> [--scope <full|phase|task>]
```

### suggest
改进建议
```
/nf-process-analyst suggest --issues <issue-list> [--constraints <constraints>]
```

## 分析维度
- 时间效率：各阶段耗时分析
- 资源效率：人力/算力利用率
- 质量效率：返工率统计
- 协作效率：部门间配合度
- 迭代效率：改进速度

## 指标类型
- 吞吐量：单位时间产出
- 周期时间：端到端耗时
- 在制品：并行任务数
- 缺陷率：质量问题比例
- 满意度：主观评价

## 输出格式
分析报告包含：
- 流程可视化
- 效率指标统计
- 瓶颈识别
- 改进建议
- ROI预测
