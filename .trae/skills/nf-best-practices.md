# Skill: nf-best-practices

## 元数据

- **技能ID**: skill-system-002
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: 无

---

## 描述

最佳实践库技能，收录 NovelFlow 系统中的成功经验、高效方法和优质模板。

## 调用方式

```
/nf-best-practices <command> [options]
```

## 命令

### full

**一键完整最佳实践应用**

```
/nf-best-practices full --category <category>
```

**执行：** list → get → apply

---

### list

列出最佳实践

```
/nf-best-practices list [--category <category>] [--phase <phase>]
```

### get

获取具体实践

```
/nf-best-practices get <practice-id>
```

### apply

应用最佳实践

```
/nf-best-practices apply <practice-id> --context <context>
```

### contribute

贡献新实践

```
/nf-best-practices contribute --template <template>
```

## 技能设计原则

### 1. 单一职责原则

```yaml
principle: "每个技能只做一件事"
explanation: "一个技能应该只有一个引起它变化的原因"
benefits:
  - "易于理解和维护"
  - "便于测试和调试"
  - "支持灵活组合"
examples:
  good: "nf-dialogue-optimizer 只优化对话"
  bad: "nf-content-optimizer 同时优化对话、场景、战斗"
```

### 2. 明确接口原则

```yaml
principle: "输入输出清晰定义"
explanation: "技能的接口应该明确、稳定、文档化"
benefits:
  - "降低使用门槛"
  - "便于集成测试"
  - "支持版本兼容"
requirements:
  - "输入参数有类型定义"
  - "输出格式有明确规范"
  - "错误情况有处理说明"
```

### 3. 可测试性原则

```yaml
principle: "每个技能都有评测用例"
explanation: "技能应该设计为可测试的，便于验证正确性"
benefits:
  - "保证质量"
  - "便于重构"
  - "支持持续集成"
practices:
  - "输入输出可预测"
  - "避免副作用"
  - "支持Mock数据"
```

### 4. 可复用性原则

```yaml
principle: "设计时考虑复用场景"
explanation: "技能应该能够在不同场景下复用"
benefits:
  - "减少重复开发"
  - "保持一致性"
  - "提高效率"
strategies:
  - "参数化配置"
  - "上下文无关"
  - "模块化设计"
```

### 5. 可扩展性原则

```yaml
principle: "支持功能扩展"
explanation: "技能应该容易扩展新功能"
benefits:
  - "适应需求变化"
  - "支持渐进增强"
  - "保护已有投资"
approaches:
  - "插件化架构"
  - "策略模式"
  - "配置驱动"
```

## 智能体协作原则

### 1. 松耦合原则

```yaml
principle: "智能体间依赖最小化"
explanation: "智能体之间应该通过消息通信，而非直接调用"
benefits:
  - "独立部署"
  - "故障隔离"
  - "灵活替换"
practices:
  - "使用消息队列"
  - "定义标准接口"
  - "避免共享状态"
```

### 2. 高内聚原则

```yaml
principle: "相关功能集中管理"
explanation: "一个智能体应该负责一组紧密相关的功能"
benefits:
  - "职责清晰"
  - "易于维护"
  - "减少通信"
examples:
  good: "内容生产部负责所有内容相关功能"
  bad: "将对话优化分散到多个智能体"
```

### 3. 容错设计原则

```yaml
principle: "错误不影响整体流程"
explanation: "单个智能体的失败不应该导致整个系统崩溃"
benefits:
  - "高可用性"
  - " graceful degradation"
  - "易于恢复"
strategies:
  - "断路器模式"
  - "重试机制"
  - "降级方案"
```

### 4. 状态可追溯原则

```yaml
principle: "所有操作有记录"
explanation: "系统应该记录所有重要操作和状态变更"
benefits:
  - "问题排查"
  - "审计合规"
  - "经验总结"
practices:
  - "操作日志"
  - "状态快照"
  - "变更历史"
```

### 5. 性能可监控原则

```yaml
principle: "关键指标可测量"
explanation: "系统应该暴露关键性能指标"
benefits:
  - "及时发现问题"
  - "优化依据"
  - "容量规划"
metrics:
  - "响应时间"
  - "吞吐量"
  - "错误率"
  - "资源使用"
```

## 项目管理原则

### 1. 迭代开发原则

```yaml
principle: "小步快跑，持续交付"
explanation: "将大任务分解为小迭代，快速交付价值"
benefits:
  - "降低风险"
  - "快速反馈"
  - "适应变化"
practices:
  - "每章作为一个迭代"
  - "每10章一个小里程碑"
  - "持续集成和测试"
```

### 2. 数据驱动原则

```yaml
principle: "决策基于数据分析"
explanation: "用数据支撑决策，而非主观判断"
benefits:
  - "客观公正"
  - "可验证"
  - "持续改进"
metrics:
  - "质量评分趋势"
  - "生产效率"
  - "返工率"
  - "读者反馈"
```

### 3. 用户中心原则

```yaml
principle: "始终考虑最终读者"
explanation: "所有决策都应该以读者体验为出发点"
benefits:
  - "提高满意度"
  - "增加留存"
  - "提升口碑"
practices:
  - "可读性优先"
  - "情感共鸣"
  - "爽点设计"
```

### 4. 质量优先原则

```yaml
principle: "不牺牲质量换速度"
explanation: "质量是底线，不能因为赶进度而降低标准"
benefits:
  - "长期价值"
  - "减少返工"
  - "建立口碑"
gates:
  - "逻辑一致性检查"
  - "合规性审查"
  - "质量评分门槛"
```

### 5. 持续改进原则

```yaml
principle: "每个项目都是学习机会"
explanation: "从每个项目中总结经验，持续优化流程"
benefits:
  - "效率提升"
  - "质量改进"
  - "知识积累"
practices:
  - "项目复盘"
  - "知识入库"
  - "流程优化"
```

## 创作最佳实践

### 创意阶段

```yaml
brainstorming:
  - "先发散后收敛"
  - "鼓励疯狂想法"
  - "结合市场数据"
  - "评估可行性"

market_analysis:
  - "关注趋势而非热点"
  - "分析竞品差异化"
  - "了解读者痛点"
  - "识别市场空白"
```

### 规划阶段

```yaml
world_building:
  - "规则要自洽"
  - "细节要丰富"
  - "留有余地"
  - "文档化"

plot_design:
  - "三幕式结构"
  - "每章有钩子"
  - "节奏张弛有度"
  - "铺垫与呼应"

character_design:
  - "欲望驱动"
  - "有成长弧线"
  - "关系复杂"
  - "有记忆点"
```

### 创作阶段

```yaml
chapter_writing:
  - "开头抓人"
  - "中间推进"
  - "结尾留钩"
  - "每章有爽点"

dialogue:
  - "符合人物"
  - "推动情节"
  - "有潜台词"
  - "避免说教"

description:
  - "多感官"
  - "服务情节"
  - "不堆砌"
  - "营造氛围"
```

### 优化阶段

```yaml
self_review:
  - "隔日再改"
  - "朗读检查"
  - "关注节奏"
  - "删减冗余"

peer_review:
  - "多角度反馈"
  - "关注盲点"
  - "建设性意见"
  - "迭代改进"
```

## 知识库模板

### 成功经验条目

```yaml
knowledge_entry:
  id: "EXP-{category}-{number}"
  type: "success_experience"
  title: "经验标题"

  metadata:
    category: "创意/架构/创作/优化/发布"
    phase: "所属阶段"
    created_at: "创建时间"
    verified: true/false
    verification_count: 0

  content:
    context: "适用场景"
    problem: "解决的问题"
    solution: "具体方法"
    steps:
      - "步骤1"
      - "步骤2"
    tips:
      - "注意事项"

  evidence:
    projects: ["项目ID"]
    metrics:
      improvement: "提升数据"

  related:
    tags: ["标签"]
    related_entries: ["相关条目ID"]
```

### 问题解决方案条目

```yaml
knowledge_entry:
  id: "SOL-{category}-{number}"
  type: "problem_solution"
  title: "问题标题"

  metadata:
    category: "问题类别"
    severity: "严重/中等/轻微"
    frequency: "常见/偶发"

  content:
    problem:
      description: "问题描述"
      symptoms: ["症状1", "症状2"]
      causes: ["原因1", "原因2"]

    solution:
      immediate: "应急方案"
      long_term: "根本解决"
      prevention: "预防措施"

    steps:
      - "解决步骤1"
      - "解决步骤2"

  related:
    similar_problems: ["相关问题"]
    prerequisites: ["前置知识"]
```

## 输出格式

最佳实践文档包含：

- 设计原则
- 协作原则
- 管理原则
- 创作实践
- 知识模板
- 应用指南
