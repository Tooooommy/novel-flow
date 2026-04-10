# Agent 配置模板

> 所有 NovelFlow Agent 必须遵循此模板创建，确保一致性和可维护性。

## Agent 配置文件结构

```yaml
# Agent 配置文件
agent:
  # 基本信息
  id: "agent-[部门]-[名称]"
  name: "智能体中文名称"
  name_en: "Agent English Name"
  version: "v1.0"
  
  # 所属部门
  department:
    id: "dept-[部门ID]"
    name: "部门名称"
    priority: "core" | "support" | "background"  # 核心/辅助/后台
  
  # 角色定义
  role:
    type: "coordinator" | "specialist" | "analyst" | "executor"
    description: "角色描述"
    responsibilities:
      - "职责1"
      - "职责2"
  
  # 绑定的 Skills
  skills:
    primary:
      - skill_id: "skill-xxx-001"
        name: "主要技能1"
        proficiency: "expert"  # expert/proficient/familiar/basic
      - skill_id: "skill-xxx-002"
        name: "主要技能2"
        proficiency: "proficient"
    
    supporting:
      - skill_id: "skill-yyy-001"
        name: "辅助技能"
        proficiency: "familiar"
  
  # 行为参数
  behavior:
    # 创造力级别 (0.0 - 1.0)
    creativity_level: 0.7
    
    # 保守度 (0.0 - 1.0) - 越低越倾向于创新
    conservatism: 0.3
    
    # 详细程度 (0.0 - 1.0)
    verbosity: 0.6
    
    # 遵循规则程度 (0.0 - 1.0)
    rule_adherence: 0.8
    
    # 最大迭代次数
    max_iterations: 5
    
    # 超时时间(秒)
    timeout: 300
  
  # 通信配置
  communication:
    # 接收的消息类型
    subscribe:
      - "task"
      - "event"
    
    # 发送的消息类型
    publish:
      - "task"
      - "result"
      - "event"
    
    # 点对点通信的默认目标
    default_peers:
      - "agent-process-coordinator"
      - "agent-[相关智能体]"
  
  # 状态管理
  state:
    # 状态持久化
    persist: true
    
    # 状态存储位置
    storage_path: "states/agent-[id].json"
    
    # 需要追踪的关键状态
    tracked_fields:
      - "current_task"
      - "progress"
      - "pending_items"
  
  # 依赖关系
  dependencies:
    # 依赖的其他 Agent
    depends_on:
      - "agent-xxx"
    
    # 依赖的外部服务
    external_services:
      - name: "服务名称"
        endpoint: "http://xxx"
        auth_required: true
  
  # 元数据
  metadata:
    created_date: "YYYY-MM-DD"
    last_updated: "YYYY-MM-DD"
    maintainer: "维护者"
    tags:
      - "标签1"
      - "标签2"
```

---

## Agent 类型定义

### 1. Coordinator (协调型)

```yaml
coordinator_template:
  role:
    type: "coordinator"
    description: "负责协调多个智能体的工作，管理任务分配和流程控制"
    responsibilities:
      - 任务调度
      - 流程控制
      - 结果汇总
      - 异常处理
  
  behavior:
    creativity_level: 0.5
    conservatism: 0.6
    verbosity: 0.7
    rule_adherence: 0.9
  
  communication:
    subscribe: ["task", "event", "query"]
    publish: ["task", "result", "event", "response"]
```

### 2. Specialist (专业型)

```yaml
specialist_template:
  role:
    type: "specialist"
    description: "专注于特定领域，负责执行具体任务"
    responsibilities:
      - 执行专业任务
      - 提供专业建议
      - 维护专业规则库
  
  behavior:
    creativity_level: 0.6
    conservatism: 0.4
    verbosity: 0.5
    rule_adherence: 0.85
  
  communication:
    subscribe: ["task"]
    publish: ["result", "event"]
```

### 3. Analyst (分析型)

```yaml
analyst_template:
  role:
    type: "analyst"
    description: "负责分析和评估，提供决策支持"
    responsibilities:
      - 数据分析
      - 质量评估
      - 风险识别
      - 建议生成
  
  behavior:
    creativity_level: 0.4
    conservatism: 0.7
    verbosity: 0.8
    rule_adherence: 0.9
  
  communication:
    subscribe: ["task", "query"]
    publish: ["result", "event", "response"]
```

### 4. Executor (执行型)

```yaml
executor_template:
  role:
    type: "executor"
    description: "负责具体执行任务，通常是批量处理"
    responsibilities:
      - 批量任务执行
      - 结果收集
      - 进度报告
  
  behavior:
    creativity_level: 0.3
    conservatism: 0.8
    verbosity: 0.4
    rule_adherence: 0.95
  
  communication:
    subscribe: ["task"]
    publish: ["result", "progress", "event"]
```

---

## 配置文件示例

### 创意探索师 Agent 配置

```yaml
agent:
  id: "agent-creative-ie"
  name: "创意探索师"
  name_en: "Idea Explorer"
  version: "v1.0"
  
  department:
    id: "dept-creative"
    name: "创意研发部"
    priority: "core"
  
  role:
    type: "specialist"
    description: "负责小说创意的发散性思考、概念探索和灵感挖掘"
    responsibilities:
      - 头脑风暴
      - 概念扩展
      - 创意反转
      - 趋势分析
  
  skills:
    primary:
      - skill_id: "skill-idea-explorer"
        name: "创意探索技能"
        proficiency: "expert"
    
    supporting:
      - skill_id: "skill-market-analyzer"
        name: "市场分析技能"
        proficiency: "proficient"
  
  behavior:
    creativity_level: 0.9
    conservatism: 0.2
    verbosity: 0.7
    rule_adherence: 0.6
    max_iterations: 10
    timeout: 180
  
  communication:
    subscribe: ["task"]
    publish: ["result", "event"]
    default_peers:
      - "agent-process-coordinator"
      - "agent-creative-ma"
      - "agent-creative-iev"
  
  state:
    persist: true
    storage_path: "states/agent-creative-ie.json"
    tracked_fields:
      - "current_exploration"
      - "generated_ideas"
      - "exploration_depth"
```

---

## 合规检查清单

创建新 Agent 配置时，确保：

- [ ] 包含完整的元数据
- [ ] 正确分类部门（核心/辅助/后台）
- [ ] 明确定义角色类型
- [ ] 绑定必需的 Skills
- [ ] 设置合理的 behavior 参数
- [ ] 配置正确的通信协议
- [ ] 定义状态管理策略
- [ ] 列出所有依赖关系

---

## 工具脚本

### 验证配置文件

```bash
# 验证 Agent 配置的 YAML 格式
python scripts/validate_agent_config.py --file .trae/agents/[agent-name].yaml

# 检查必需的字段
python scripts/check_required_fields.py --file .trae/agents/[agent-name].yaml
```

### 生成 Agent 文档

```bash
# 从 YAML 配置生成 Markdown 文档
python scripts/generate_agent_docs.py --dir .trae/agents --output .trae/docs/agents/
```

---

*模板版本: v1.0*
*基于 NovelFlow 最佳实践*
