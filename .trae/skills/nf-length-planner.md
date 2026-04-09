# Skill: nf-length-planner

## 描述
篇幅规划师技能，负责规划小说的整体篇幅结构、章节划分和字数分配。

## 调用方式
```
/nf-length-planner <command> [options]
```

## 命令

### plan
制定篇幅规划方案
```
/nf-length-planner plan --target <total-words> [--type <short|medium|long|epic>] [--chapters <count>]
```

### allocate
分配各章节字数
```
/nf-length-planner allocate --structure <structure-type> [--ratio <ratio-pattern>]
```

### adjust
根据进度调整规划
```
/nf-length-planner adjust --current <current-words> --target <target-words> [--phase <current-phase>]
```

### pace
计算叙事节奏指标
```
/nf-length-planner pace --plot-points <count> [--total-chapters <count>]
```

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
