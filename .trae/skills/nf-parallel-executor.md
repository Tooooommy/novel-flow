# Skill: nf-parallel-executor

## 元数据

- **技能ID**: skill-process-004
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-process-coordinator

---

## 描述

并行执行技能，负责协调多个内容生产代理并行创作不同分卷，提高创作效率。

## 调用方式

```
/nf-parallel-executor <command> [options]
```

## 命令

### full

**一键启动完整并行执行**

```
/nf-parallel-executor full --volumes <volume-list>
```

**执行：** run → status → pause

---

### run

启动并行创作

```
/nf-parallel-executor run --volumes <volume-list> [--max-workers <n>] [--mode <sync|async>]
```

### status

查看并行执行状态

```
/nf-parallel-executor status [--execution-id <id>]
```

### pause

暂停并行执行

```
/nf-parallel-executor pause --execution-id <id> [--volumes <volume-list>]
```

### resume

恢复并行执行

```
/nf-parallel-executor resume --execution-id <id>
```

### cancel

取消并行执行

```
/nf-parallel-executor cancel --execution-id <id> [--reason <reason>]
```

### optimize

优化并行策略

```
/nf-parallel-executor optimize --execution-id <id> [--strategy <strategy>]
```

## 并行执行模式

### 1. 完全并行模式 (full-parallel)

所有分卷同时创作，适合无强依赖关系的多卷作品

```
Volume 1: ████████████████████ 100%
Volume 2: ████████████████████ 100%
Volume 3: ████████████████████ 100%
          ↑ 同时执行
```

### 2. 流水线模式 (pipeline)

分阶段并行，适合有前后依赖的创作流程

```
Phase 1: Volume 1 大纲 → Volume 2 大纲 → Volume 3 大纲
Phase 2: Volume 1 创作 → Volume 2 创作 → Volume 3 创作
Phase 3: Volume 1 审查 → Volume 2 审查 → Volume 3 审查
```

### 3. 混合模式 (hybrid)

部分并行 + 部分串行，适合复杂依赖关系

```
Step 1: 并行创作 Volume 1 & Volume 2 大纲
Step 2: Volume 1 大纲 → 创作 Volume 1
        ↓ (依赖Volume 1部分设定)
        Volume 2 大纲 → 创作 Volume 2
Step 3: 并行审查 Volume 1 & Volume 2
```

## 工作线程管理

### 线程池配置

```yaml
thread_pool:
  max_workers: 5 # 最大并行工作线程
  min_workers: 2 # 最小保持线程
  queue_size: 10 # 任务队列大小

resource_limits:
  max_memory: "8GB"
  max_cpu_percent: 80
  timeout_per_chapter: 600 # 每章超时时间(秒)
```

### 任务分配策略

```yaml
assignment_strategy:
  type: "round_robin" # round_robin / least_loaded / priority

  round_robin:
    description: "轮流分配给各工作线程"

  least_loaded:
    description: "分配给负载最轻的工作线程"

  priority:
    description: "按优先级分配"
    priority_rules:
      - "关键分卷优先"
      - "有依赖的分卷优先"
```

## 执行状态监控

### 实时监控面板

```
╔═══════════════════════════════════════════════════════════════╗
║           并行创作执行面板 - Execution: PAR-001               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  总体进度: ████████████████████░░░░░░  67%                   ║
║  预计完成: 2024-02-15 18:30 (剩余 2小时)                      ║
║                                                               ║
║  ┌─────────────┬──────────┬──────────┬──────────┐            ║
║  │   分卷      │  进度    │  状态    │  代理    │            ║
║  ├─────────────┼──────────┼──────────┼──────────┤            ║
║  │ 第一卷      │ 100%     │ ✅完成   │ CP-01    │            ║
║  │ 第二卷      │  85%     │ 🔄执行中 │ CP-02    │            ║
║  │ 第三卷      │  45%     │ 🔄执行中 │ CP-03    │            ║
║  │ 第四卷      │  30%     │ ⏸️暂停   │ CP-04    │            ║
║  │ 第五卷      │   0%     │ ⏳等待   │ -        │            ║
║  └─────────────┴──────────┴──────────┴──────────┘            ║
║                                                               ║
║  活跃线程: 3/5  队列任务: 2  完成速度: 3章/小时               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 性能指标

```yaml
metrics:
  throughput:
    chapters_per_hour: 3
    words_per_hour: 9000

  efficiency:
    cpu_usage: "65%"
    memory_usage: "4.2GB"
    thread_utilization: "75%"

  quality:
    average_score: 8.3
    revision_rate: "12%"
```

## 错误处理与恢复

### 故障转移

```yaml
failover:
  trigger: "worker_failure / timeout / quality_reject"

  actions:
    1: "标记失败任务"
    2: "保存当前进度"
    3: "重新分配任务"
    4: "通知协调器"
    5: "继续执行"
```

### 断点续作

```yaml
checkpoint:
  interval: "每5章"
  storage: "持久化存储"

  recovery:
    - "读取最后检查点"
    - "恢复执行上下文"
    - "继续未完成任务"
```

## 输出格式

执行报告包含：

- 执行概况
- 各分卷进度
- 性能指标
- 错误日志
- 优化建议
