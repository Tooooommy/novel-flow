# NovelFlow Agent 标准模板

> 所有 NovelFlow Agent 必须遵循此模板创建，确保一致性、可维护性和可扩展性。

---

## 1. Agent 元数据

```yaml
metadata:
  agent_id: "agent-[部门]-[名称]" # 格式: agent-{dept}-{name}
  name: "智能体中文名称"
  name_en: "Agent English Name"
  version: "v1.0"
  maintainer: "NovelFlow Team"
  created_date: "2026-01-01"
  last_updated: "2026-04-10"
```

### Agent ID 规范

| 前缀                 | 说明       | 示例                        |
| -------------------- | ---------- | --------------------------- |
| `agent-main`         | 主控智能体 | `agent-main-001`            |
| `agent-creative`     | 创意研发部 | `agent-creative-ie`         |
| `agent-architecture` | 架构设计部 | `agent-architecture-wb`     |
| `agent-content`      | 内容生产部 | `agent-content-cg`          |
| `agent-quality`      | 质量保证部 | `agent-quality-li`          |
| `agent-publishing`   | 发布运营部 | `agent-publishing-pa`       |
| `agent-retro`        | 复盘改进部 | `agent-retro-pa`            |
| `agent-process`      | 流程协调部 | `agent-process-coordinator` |

---

## 2. 部门分类

```yaml
department:
  id: "dept-[部门ID]"
  name: "部门名称"
  priority: "core" | "support" | "background"  # 核心/辅助/后台
```

### 部门定义

| 部门 ID             | 名称       | 优先级     | 说明             |
| ------------------- | ---------- | ---------- | ---------------- |
| `dept-main`         | 主控部门   | core       | 流程总控         |
| `dept-creative`     | 创意研发部 | core       | 创意发想         |
| `dept-architecture` | 架构设计部 | core       | 世界观/人物/大纲 |
| `dept-content`      | 内容生产部 | core       | 正文生成         |
| `dept-quality`      | 质量保证部 | core       | 逻辑/合规/评估   |
| `dept-publishing`   | 发布运营部 | support    | 平台适配         |
| `dept-retro`        | 复盘改进部 | background | 流程分析         |
| `dept-process`      | 流程协调部 | core       | 任务调度         |

---

## 3. 角色定义

```yaml
role:
  type: "coordinator" | "specialist" | "analyst" | "executor"
  description: "角色描述，一句话说明"
  responsibilities:
    - "职责1"
    - "职责2"
```

### Agent 类型

| 类型          | 说明                           | 典型智能体             |
| ------------- | ------------------------------ | ---------------------- |
| `coordinator` | 协调型：负责任务分配和流程控制 | 流程协调智能体         |
| `specialist`  | 专业型：专注特定领域执行       | 创意探索师、内容生成师 |
| `analyst`     | 分析型：负责评估和决策支持     | 市场分析师、质量评估师 |
| `executor`    | 执行型：批量任务执行           | 并行执行器             |

### 类型模板

#### Coordinator (协调型)

```yaml
role:
  type: "coordinator"
  description: "负责协调多个智能体的工作，管理任务分配和流程控制"
  responsibilities:
    - 任务调度
    - 流程控制
    - 结果汇总
    - 异常处理

behavior:
  creativity_level: 0.5 # 中等创造力
  conservatism: 0.6 # 适度保守
  verbosity: 0.7 # 详细输出
  rule_adherence: 0.9 # 高规则遵循
  max_iterations: 5
  timeout: 300

communication:
  subscribe: ["task", "event", "query"]
  publish: ["task", "result", "event", "response"]
```

#### Specialist (专业型)

```yaml
role:
  type: "specialist"
  description: "专注于特定领域，负责执行具体任务"
  responsibilities:
    - 执行专业任务
    - 提供专业建议
    - 维护专业规则库

behavior:
  creativity_level: 0.7 # 高创造力
  conservatism: 0.3 # 敢于创新
  verbosity: 0.6 # 适中输出
  rule_adherence: 0.75 # 适度规则
  max_iterations: 8
  timeout: 180

communication:
  subscribe: ["task"]
  publish: ["result", "event"]
```

#### Analyst (分析型)

```yaml
role:
  type: "analyst"
  description: "负责分析和评估，提供决策支持"
  responsibilities:
    - 数据分析
    - 质量评估
    - 风险识别
    - 建议生成

behavior:
  creativity_level: 0.4 # 较低创造力
  conservatism: 0.7 # 偏保守
  verbosity: 0.8 # 详细输出
  rule_adherence: 0.9 # 高规则遵循
  max_iterations: 3
  timeout: 120

communication:
  subscribe: ["task", "query"]
  publish: ["result", "event", "response"]
```

#### Executor (执行型)

```yaml
role:
  type: "executor"
  description: "负责具体执行任务，通常是批量处理"
  responsibilities:
    - 批量任务执行
    - 结果收集
    - 进度报告

behavior:
  creativity_level: 0.2 # 低创造力
  conservatism: 0.8 # 高保守
  verbosity: 0.4 # 简洁输出
  rule_adherence: 0.95 # 极高规则遵循
  max_iterations: 1
  timeout: 600

communication:
  subscribe: ["task"]
  publish: ["result", "progress", "event"]
```

---

## 4. 技能绑定

```yaml
skills:
  primary: # 主要技能（必须绑定）
    - skill_id: "skill-xxx-001"
      name: "主要技能1"
      proficiency: "expert" # expert/proficient/familiar/basic
      usage_priority: 1 # 使用优先级

  supporting: # 辅助技能（可选）
    - skill_id: "skill-yyy-001"
      name: "辅助技能"
      proficiency: "proficient"
      usage_priority: 2
```

### 熟练度等级

| 等级         | 说明   | 适用场景       |
| ------------ | ------ | -------------- |
| `expert`     | 专家级 | 主要执行的技能 |
| `proficient` | 熟练级 | 经常使用       |
| `familiar`   | 熟悉级 | 偶尔使用       |
| `basic`      | 基础级 | 了解即可       |

---

## 5. 行为参数

```yaml
behavior:
  # 创造力级别 (0.0 - 1.0)
  # 越高越倾向于产生新颖、独特的想法
  creativity_level: 0.7

  # 保守度 (0.0 - 1.0)
  # 越低越倾向于创新冒险
  conservatism: 0.3

  # 详细程度 (0.0 - 1.0)
  # 影响输出信息的详略
  verbosity: 0.6

  # 遵循规则程度 (0.0 - 1.0)
  # 越低越倾向于灵活变通
  rule_adherence: 0.8

  # 最大迭代次数
  # 单次任务最大循环次数
  max_iterations: 5

  # 超时时间(秒)
  timeout: 300
```

### 行为参数建议

| Agent 类型  | creativity | conservatism | verbosity | rule_adherence |
| ----------- | ---------- | ------------ | --------- | -------------- |
| Coordinator | 0.4-0.6    | 0.5-0.7      | 0.6-0.8   | 0.8-0.95       |
| Specialist  | 0.6-0.9    | 0.2-0.4      | 0.5-0.7   | 0.6-0.8        |
| Analyst     | 0.3-0.5    | 0.6-0.8      | 0.7-0.9   | 0.85-0.95      |
| Executor    | 0.1-0.3    | 0.7-0.9      | 0.3-0.5   | 0.9-1.0        |

---

## 6. 通信配置

```yaml
communication:
  # 接收的消息类型
  subscribe:
    - "task" # 任务消息
    - "event" # 事件通知
    - "query" # 查询请求
    - "control" # 控制指令

  # 发送的消息类型
  publish:
    - "task" # 任务分发
    - "result" # 结果返回
    - "event" # 事件通知
    - "response" # 查询响应
    - "progress" # 进度报告

  # 点对点通信的默认目标
  default_peers:
    - "agent-process-coordinator"
    - "agent-[相关智能体]"
```

### 消息类型定义

| 类型       | 说明          | 方向      |
| ---------- | ------------- | --------- |
| `task`     | 任务分配/执行 | 双向      |
| `event`    | 事件通知      | 双向      |
| `query`    | 查询请求      | 请求→响应 |
| `response` | 查询响应      | 响应→请求 |
| `control`  | 控制指令      | 双向      |
| `progress` | 进度报告      | 单向      |

---

## 7. 状态管理

```yaml
state:
  # 是否持久化状态
  persist: true

  # 状态存储位置
  storage_path: "states/agent-[id].json"

  # 需要追踪的关键状态
  tracked_fields:
    - "current_task"
    - "progress"
    - "pending_items"
    - "completed_items"
```

### 状态字段规范

| 字段              | 类型   | 说明               |
| ----------------- | ------ | ------------------ |
| `current_task`    | object | 当前执行的任务     |
| `progress`        | number | 进度百分比 (0-100) |
| `pending_items`   | array  | 待处理项           |
| `completed_items` | array  | 已完成项           |
| `failed_items`    | array  | 失败项             |
| `metadata`        | object | 元数据             |

---

## 8. 依赖关系

```yaml
dependencies:
  # 依赖的其他 Agent
  depends_on:
    - "agent-xxx"
    - "agent-yyy"

  # 依赖的外部服务
  external_services:
    - name: "服务名称"
      endpoint: "http://xxx"
      auth_required: true
      retry_times: 3
```

---

## 9. 完整配置示例

### 创意探索师 Agent

```yaml
agent:
  # ============ 元数据 ============
  id: "agent-creative-ie"
  name: "创意探索师"
  name_en: "Idea Explorer"
  version: "v1.0"
  created_date: "2026-01-01"
  last_updated: "2026-04-10"
  maintainer: "NovelFlow Team"

  # ============ 部门分类 ============
  department:
    id: "dept-creative"
    name: "创意研发部"
    priority: "core"

  # ============ 角色定义 ============
  role:
    type: "specialist"
    description: "负责小说创意的发散性思考、概念探索和灵感挖掘"
    responsibilities:
      - 头脑风暴
      - 概念扩展
      - 创意反转
      - 趋势分析
      - 创意评估

  # ============ 技能绑定 ============
  skills:
    primary:
      - skill_id: "skill-creative-001"
        name: "创意探索技能"
        proficiency: "expert"
        usage_priority: 1

    supporting:
      - skill_id: "skill-creative-002"
        name: "市场分析技能"
        proficiency: "proficient"
        usage_priority: 2

  # ============ 行为参数 ============
  behavior:
    creativity_level: 0.9
    conservatism: 0.2
    verbosity: 0.7
    rule_adherence: 0.6
    max_iterations: 10
    timeout: 180

  # ============ 通信配置 ============
  communication:
    subscribe:
      - "task"
      - "event"
    publish:
      - "result"
      - "event"
      - "progress"
    default_peers:
      - "agent-process-coordinator"
      - "agent-creative-ma"
      - "agent-creative-iev"

  # ============ 状态管理 ============
  state:
    persist: true
    storage_path: "states/agent-creative-ie.json"
    tracked_fields:
      - "current_exploration"
      - "generated_ideas"
      - "exploration_depth"
      - "iteration_count"

  # ============ 依赖关系 ============
  dependencies:
    depends_on:
      - "agent-process-coordinator"
    external_services: []

  # ============ 标签 ============
  tags:
    - "创意"
    - "探索"
    - "头脑风暴"
```

---

## 10. 合规检查清单

创建新 Agent 配置时，确保：

```
□ 包含完整的元数据（id, name, version, dates）
□ 正确分类部门（core/support/background）
□ 明确定义角色类型（coordinator/specialist/analyst/executor）
□ 绑定主要技能（至少1个 primary skill）
□ 设置合理的 behavior 参数
□ 配置正确的通信协议（subscribe/publish）
□ 定义状态管理策略（persist, tracked_fields）
□ 列出所有依赖关系（depends_on）
□ 添加适当的 tags 标签
□ 通过配置文件验证
```

---

## 11. 验证规则

### 必填字段

| 字段                        | 验证规则             |
| --------------------------- | -------------------- |
| `id`                        | 必须以 `agent-` 开头 |
| `name`                      | 不能为空             |
| `department.id`             | 必须在部门定义列表中 |
| `role.type`                 | 必须是有效类型       |
| `skills.primary`            | 至少包含 1 个技能    |
| `behavior.creativity_level` | 必须在 0.0-1.0 范围  |

### 可选字段

| 字段                          | 默认值 |
| ----------------------------- | ------ |
| `behavior.max_iterations`     | 5      |
| `behavior.timeout`            | 300    |
| `state.persist`               | false  |
| `communication.default_peers` | []     |

---

## 12. 更新日志

```markdown
### v1.0 (2026-01-01)

- 初始版本

### v1.1 (2026-04-10)

- 完善 Agent 类型模板
- 增加行为参数建议表
- 添加验证规则
- 优化配置示例
```

---

_模板版本: v2.0_
_基于 NovelFlow 最佳实践_
_最后更新: 2026-04-10_
