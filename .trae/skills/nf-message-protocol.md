# Skill: nf-message-protocol

## 描述

消息传递协议技能，定义 NovelFlow 系统中各智能体之间的通信标准和消息格式。

## 调用方式

```
/nf-message-protocol <command> [options]
```

## 命令

### full

**一键完整消息处理**

```
/nf-message-protocol full --type <message-type> --sender <agent> --receiver <agent>
```

**执行：** create → validate → log

---

### create

创建新消息

```
/nf-message-protocol create --type <message-type> --sender <agent> --receiver <agent>
```

### validate

验证消息格式

```
/nf-message-protocol validate --message <message-data>
```

### log

记录消息日志

```
/nf-message-protocol log --message <message-id>
```

### query

查询消息历史

```
/nf-message-protocol query --filter <filters>
```

## 消息格式规范

### 基础消息结构

```yaml
message:
  # 元数据
  metadata:
    id: "MSG-{timestamp}-{uuid}" # 消息唯一标识
    timestamp: "2024-01-15T10:30:00Z" # ISO 8601 格式
    version: "1.0" # 协议版本

  # 路由信息
  routing:
    sender: "agent-id" # 发送方智能体ID
    receiver: "agent-id" # 接收方智能体ID
    cc: ["agent-id"] # 抄送列表
    priority: high/medium/low # 优先级

  # 消息类型
  type: task/notification/query/response/event

  # 消息内容
  payload:
    action: "specific-action" # 具体操作
    parameters: {} # 参数
    context: {} # 上下文信息
    attachments: [] # 附件列表

  # 控制信息
  control:
    require_ack: true/false # 是否需要确认
    timeout: 300 # 超时时间（秒）
    retry_count: 3 # 重试次数
    expires_at: "timestamp" # 过期时间
```

### 消息类型详解

#### 1. Task (任务消息)

```yaml
type: task
payload:
  action: "generate_chapter"
  parameters:
    chapter_number: 1
    word_count: 3000
    outline: "chapter_outline_id"
  deadline: "2024-01-16T10:00:00Z"
  dependencies: ["task-id-1", "task-id-2"]
```

#### 2. Notification (通知消息)

```yaml
type: notification
payload:
  level: info/warning/error/success
  title: "任务完成通知"
  content: "第3章生成已完成"
  related_tasks: ["task-id"]
```

#### 3. Query (查询消息)

```yaml
type: query
payload:
  query_type: "status/project/knowledge"
  query_params:
    project_id: "PROJ-001"
    fields: ["progress", "quality_score"]
```

#### 4. Response (响应消息)

```yaml
type: response
payload:
  status: success/failure/partial
  result: {}
  error: {} # 失败时包含
  execution_time: 120 # 执行时间（秒）
```

#### 5. Event (事件消息)

```yaml
type: event
payload:
  event_type: "phase_complete/chapter_publish/quality_alert"
  event_data: {}
  timestamp: "2024-01-15T10:30:00Z"
```

## 智能体ID规范

```
格式: {department}-{role}-{instance}

示例:
- 流程协调: coordinator-main-01
- 创意研发: creative-rd-idea-01
- 架构设计: arch-design-world-01
- 内容生产: content-prod-gen-01
- 质量保证: qa-inspect-logic-01
- 发布运营: pub-ops-platform-01
- 复盘改进: retro-analyst-process-01
```

## 错误处理消息

```yaml
type: response
payload:
  status: failure
  error:
    code: "ERR-001"
    type: "validation_error/execution_error/timeout_error"
    message: "详细错误信息"
    details: {}
    suggestion: "修复建议"
  stack_trace: "..." # 开发环境包含
```

## 确认机制

### 发送确认 (ACK)

```yaml
type: response
payload:
  status: acknowledged
  original_message_id: "MSG-xxx"
  estimated_completion: "2024-01-15T11:00:00Z"
```

### 完成确认 (DONE)

```yaml
type: response
payload:
  status: completed
  original_message_id: "MSG-xxx"
  result: {}
  metrics:
    execution_time: 300
    quality_score: 8.5
```

## 消息队列管理

### 优先级队列

```yaml
queues:
  high_priority:
    max_size: 100
    ttl: 3600
  medium_priority:
    max_size: 500
    ttl: 7200
  low_priority:
    max_size: 1000
    ttl: 14400
```

### 死信队列

```yaml
dead_letter_queue:
  trigger_conditions:
    - max_retries_exceeded
    - message_expired
    - validation_failed
  retention_period: 604800 # 7天
```

## 消息追踪

### 链路追踪

```yaml
trace:
  trace_id: "TRACE-xxx"
  span_id: "SPAN-xxx"
  parent_span_id: "SPAN-parent"
  path: ["agent-1", "agent-2", "agent-3"]
  timestamps:
    - agent: "agent-1"
      received: "..."
      processed: "..."
      sent: "..."
```

## 安全规范

### 消息签名

```yaml
security:
  signature: "..."
  algorithm: "HMAC-SHA256"
  timestamp_tolerance: 300 # 5分钟时间窗口
```

### 敏感信息处理

```yaml
sensitive_data:
  encryption: "AES-256"
  key_rotation: 86400 # 24小时轮换
  fields: ["user_data", "financial_info"]
```

## 使用示例

### 示例1：任务分配

```yaml
# 协调器 → 内容生成师
message:
  metadata:
    id: "MSG-20240115-001"
    timestamp: "2024-01-15T10:00:00Z"
  routing:
    sender: "coordinator-main-01"
    receiver: "content-prod-gen-01"
    priority: high
  type: task
  payload:
    action: "generate_chapter"
    parameters:
      chapter_number: 1
      title: "开篇"
      word_count: 3000
      outline: "OUTLINE-001"
    context:
      project_id: "PROJ-001"
      novel_title: "作品名称"
  control:
    require_ack: true
    timeout: 600
```

### 示例2：质量审查结果

```yaml
# 质量评估师 → 协调器
message:
  metadata:
    id: "MSG-20240115-002"
    timestamp: "2024-01-15T10:30:00Z"
  routing:
    sender: "qa-assess-quality-01"
    receiver: "coordinator-main-01"
    priority: high
  type: response
  payload:
    status: success
    result:
      chapter_id: "CH-001"
      quality_score: 8.5
      issues: []
      suggestions: ["可增加环境描写"]
    metrics:
      execution_time: 120
      words_analyzed: 3200
```

## 输出格式

消息协议文档包含：

- 消息格式规范
- 类型定义
- 错误代码表
- 使用示例
- 安全规范
