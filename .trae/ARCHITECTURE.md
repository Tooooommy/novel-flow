# NovelFlow 系统架构文档

## 一、系统架构图

### 1.1 核心智能体体系

```mermaid
graph TB
    subgraph "流程协调层"
        PC[流程协调智能体<br/>Process Coordinator]
    end

    subgraph "创意研发部"
        IE[创意探索师]
        MA[市场分析师]
        IEV[创新评估师]
    end

    subgraph "架构设计部"
        LP[篇幅规划师]
        WB[世界构建师]
        SA[故事架构师]
        CD[人物设计师]
    end

    subgraph "内容生产部"
        PE[节奏工程师]
        CG[内容生成师]
        SO[专业优化师]
    end

    subgraph "质量保证部"
        LI[逻辑审查官]
        CO[合规审查官]
        QA[质量评估师]
    end

    subgraph "发布运营部"
        PAD[平台适配师]
        PS[发布策略师]
    end

    subgraph "复盘改进部"
        PA[流程分析员]
        KC[知识库管理员]
    end

    PC --> IE
    PC --> MA
    PC --> IEV
    PC --> LP
    PC --> WB
    PC --> SA
    PC --> CD
    PC --> PE
    PC --> CG
    PC --> SO
    PC --> LI
    PC --> CO
    PC --> QA
    PC --> PAD
    PC --> PS
    PC --> PA
    PC --> KC
```

### 1.2 核心与辅助智能体分离

```mermaid
graph TB
    subgraph "⭐ 核心智能体（必须，主流程）"
        PC[流程协调智能体]
        IE[创意探索师]
        SA[故事架构师]
        CG[内容生成师]
        LI[逻辑审查官]
        QA[质量评估师]
    end

    subgraph "🔧 辅助智能体（可选，增强功能）"
        MA[市场分析师]
        IEV[创新评估师]
        LP[篇幅规划师]
        WB[世界构建师]
        CD[人物设计师]
        PE[节奏工程师]
        SO[专业优化师]
        CO[合规审查官]
        PAD[平台适配师]
        PS[发布策略师]
    end

    subgraph "🔄 后台智能体（异步，持续优化）"
        PA[流程分析员]
        KC[知识库管理员]
    end
```

---

## 二、核心流程时序图

### 2.1 章节生成流程

```mermaid
sequenceDiagram
    autonumber
    participant User as 用户
    participant PC as 流程协调智能体
    participant PE as 节奏工程师
    participant CG as 内容生成师
    participant SO as 专业优化师
    participant LI as 逻辑审查官
    participant QA as 质量评估师

    User->>PC: 请求生成章节

    rect rgb(200, 230, 200)
        Note over PC,PE: Phase 1: 节奏设计
        PC->>PE: 设计章节节奏
        PE-->>PC: 节奏方案
        PC->>User: 确认节奏方案
        User-->>PC: 确认/修改
    end

    rect rgb(200, 220, 255)
        Note over PC,CG: Phase 2: 内容生成
        PC->>CG: 生成章节草稿
        CG-->>PC: 草稿内容
    end

    rect rgb(255, 230, 200)
        Note over PC,SO: Phase 3: 优化处理
        PC->>SO: 优化草稿
        Note over SO: humanize → tighten → enhance → dialogue → polish
        SO-->>PC: 优化后内容
    end

    rect rgb(255, 200, 200)
        Note over PC,LI: Phase 4: 逻辑审查
        PC->>LI: 逻辑检查
        LI-->>PC: 审查报告
        alt 存在逻辑问题
            PC->>CG: 返回修改
            CG->>SO: 重新优化
            SO->>LI: 再次审查
        end
    end

    rect rgb(200, 255, 200)
        Note over PC,QA: Phase 5: 质量评估
        PC->>QA: 质量评分
        QA-->>PC: 评估报告
    end

    PC-->>User: 章节完成 + 质量报告
```

### 2.2 并行分卷创作流程

```mermaid
sequenceDiagram
    autonumber
    participant User as 用户
    participant PC as 流程协调智能体
    participant VM as 分卷管理器
    participant PE as 并行执行器
    participant CG1 as 内容生成师#1
    participant CG2 as 内容生成师#2
    participant CG3 as 内容生成师#3
    participant NM as 小说合并器

    User->>PC: 并行创作请求(3卷)

    rect rgb(200, 230, 200)
        Note over PC,NM: Phase 1: 规划(串行)
        PC->>VM: 拆分大纲
        VM-->>PC: 3个分卷大纲
        PC->>User: 确认分卷大纲
        User-->>PC: 确认
    end

    rect rgb(200, 220, 255)
        Note over PE,NM: Phase 2: 并行创作
        par 并行生成第1卷
            PE->>CG1: 生成第1卷
            CG1-->>PE: 第1卷完成
        and 并行生成第2卷
            PE->>CG2: 生成第2卷
            CG2-->>PE: 第2卷完成
        and 并行生成第3卷
            PE->>CG3: 生成第3卷
            CG3-->>PE: 第3卷完成
        end
    end

    rect rgb(255, 230, 200)
        Note over PC,NM: Phase 3: 合并(串行)
        PC->>NM: 合并分卷
        NM-->>PC: 完整小说
    end

    PC-->>User: 创作完成
```

### 2.3 创意到大纲流程

```mermaid
sequenceDiagram
    autonumber
    participant User as 用户
    participant PC as 流程协调智能体
    participant IE as 创意探索师
    participant MA as 市场分析师
    participant IEV as 创新评估师
    participant SA as 故事架构师
    participant WB as 世界构建师
    participant CD as 人物设计师

    User->>PC: 原始创意/想法

    rect rgb(200, 230, 200)
        Note over PC,IEV: Think 阶段
        PC->>IE: 头脑风暴
        IE-->>PC: 3个创意方向
        PC->>MA: 市场分析
        MA-->>PC: 市场报告
        PC->>IEV: 创新评估
        IEV-->>PC: 评估结果
        PC->>User: 推荐最佳创意
        User-->>PC: 选择创意A
    end

    rect rgb(200, 220, 255)
        Note over PC,CD: Plan 阶段
        PC->>SA: 设计故事架构
        SA-->>PC: 大纲框架
        PC->>WB: 构建世界观
        WB-->>PC: 世界设定
        PC->>CD: 设计人物
        CD-->>PC: 人物档案
        PC->>User: 确认完整大纲
        User-->>PC: 确认/修改
    end

    PC-->>User: 完整项目方案
```

---

## 三、消息总线架构

### 3.1 消息总线设计

```mermaid
graph LR
    subgraph "智能体节点"
        IE[创意探索师]
        MA[市场分析师]
        CG[内容生成师]
        SO[专业优化师]
        QA[质量评估师]
    end

    subgraph "消息总线(Message Bus)"
        MB[中央消息路由器]
        Q1[任务队列]
        Q2[事件队列]
        Q3[结果队列]
    end

    subgraph "存储层"
        KB[(知识库)]
        SB[(状态存储)]
    end

    IE -->|发布任务| MB
    MA -->|发布任务| MB
    CG -->|订阅任务| MB
    CG -->|发布结果| MB
    SO -->|订阅任务| MB
    SO -->|发布结果| MB
    QA -->|订阅任务| MB
    QA -->|发布结果| MB

    MB --> Q1
    MB --> Q2
    MB --> Q3

    Q1 --> KB
    Q3 --> SB
    SB --> MB
```

### 3.2 消息格式标准

```yaml
消息类型:
  task: 任务消息
  event: 事件消息
  result: 结果消息
  query: 查询消息
  response: 响应消息

消息结构:
  id: "msg-uuid-xxx"
  timestamp: "2026-01-01T10:00:00Z"
  type: "task"  # task|event|result|query|response
  sender: "agent-name"
  receiver: "agent-name" | "broadcast"
  priority: "high" | "medium" | "low"
  payload:
    action: "generate_chapter"
    parameters: {}
    context: {}
  require_ack: true
  timeout: 300
```

---

## 四、技能效能评估

### 4.1 评估指标体系

| 指标         | 说明                           | 计算方式                  |
| ------------ | ------------------------------ | ------------------------- |
| 首次通过率   | 一次生成即通过质量评估的比例   | 通过数/总生成数           |
| 平均修改次数 | 达到发布标准需要的平均修改次数 | 总修改次数/章节数         |
| AI味道残留率 | 优化后AI特征的平均残留程度     | 检测到的AI特征数/总检查点 |
| 用户满意度   | 用户对生成内容的满意程度       | 满意评价数/总评价数       |

### 4.2 各技能基准值

| 技能     | 首次通过率基准 | AI味道残留率基准 |
| -------- | -------------- | ---------------- |
| 章节生成 | ≥60%           | <15%             |
| 对话优化 | ≥70%           | <10%             |
| 场景描写 | ≥65%           | <12%             |
| 战斗描写 | ≥60%           | <15%             |
| 情感渲染 | ≥55%           | <18%             |

---

## 五、作者干预节点

### 5.1 强制干预点

```mermaid
graph LR
    A[创意方向] --> B{用户确认?}
    B -->|通过| C[大纲设计]
    B -->|修改| A
    C --> D{用户确认?}
    D -->|通过| E[分卷大纲]
    D -->|修改| C
    E --> F{用户确认?}
    F -->|通过| G[正式创作]
    F -->|修改| E
    G --> H{章节审核?}
    H -->|通过| I[下一章]
    H -->|修改| G
```

### 5.2 干预节点配置

| 节点     | 阶段  | 干预方式               | 超时处理         |
| -------- | ----- | ---------------------- | ---------------- |
| 创意确认 | Think | 选择/修改/重新生成     | 自动通过推荐方案 |
| 大纲确认 | Plan  | 确认/局部修改/重新设计 | 暂停等待         |
| 人物确认 | Plan  | 确认/修改/新增         | 暂停等待         |
| 分卷大纲 | Split | 确认/调整分卷点        | 暂停等待         |
| 章节审核 | Build | 通过/打回修改          | 自动进入下一章   |

---

## 六、知识管理结构

### 6.1 问题记录模板

```yaml
问题记录:
  id: "ISSUE-001"
  类型: "逻辑矛盾" | "AI味道" | "节奏问题" | "其他"
  场景: "第X章-Y场景"
  错误代码: "LOGIC-001"  # 预定义错误码
  描述: "问题详细描述"
  原因分析: "为什么会出错"
  解决方案: "如何修复"
  关联技能: ["logic-inspector", "specialist-optimizer"]
  预防措施: "如何避免同类问题"
  创建时间: "2026-01-01"
  状态: "open" | "resolved" | "closed"
```

### 6.2 经验沉淀模板

```yaml
经验记录:
  id: "EXP-001"
  类型: "成功经验" | "失败教训" | "最佳实践"
  适用场景: "玄幻题材战斗描写"
  核心内容: "具体方法或规则"
  效果验证: "应用后的效果数据"
  关联项目: ["项目A", "项目B"]
  创建时间: "2026-01-01"
  状态: "pending" | "verified" | "archived"
```

---

_文档版本: v1.1_
_更新时间: 2026-01-01_
_维护者: NovelFlow Architecture Team_
