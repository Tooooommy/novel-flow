# Skill: nf-test-cases

## 描述
评测用例管理技能，为 NovelFlow 各技能模块提供测试用例设计、执行和报告功能。

## 调用方式
```
/nf-test-cases <command> [options]
```

## 命令

### create
创建测试用例
```
/nf-test-cases create --module <module-name> --type <test-type>
```

### run
执行测试用例
```
/nf-test-cases run --case-id <case-id> [--input <test-input>]
```

### batch
批量执行测试
```
/nf-test-cases batch --module <module> [--coverage <percentage>]
```

### report
生成测试报告
```
/nf-test-cases report --run-id <run-id> [--format <format>]
```

## 测试用例结构

### 基础模板

```yaml
test_case:
  metadata:
    id: "TEST-{module}-{number}"
    name: "测试用例名称"
    description: "详细描述"
    created_at: "2024-01-15"
    updated_at: "2024-01-15"
    version: "1.0"
    author: "创建者"
  
  target:
    module: "模块名称"
    skill: "技能名称"
    function: "具体功能"
  
  type: unit/integration/e2e/regression
  priority: critical/high/medium/low
  
  input:
    data: {}
    context: {}
    parameters: {}
  
  expected:
    output: {}
    metrics: {}
    constraints: []
  
  validation:
    assertions: []
    checks: []
  
  cleanup:
    required: true/false
    actions: []
```

## 各模块测试用例

### 1. 创意生成模块 (TEST-IDEA)

#### TEST-IDEA-001: 玄幻题材创意生成

```yaml
metadata:
  id: "TEST-IDEA-001"
  name: "玄幻题材创意生成测试"
  
target:
  module: "creative_rd"
  skill: "nf-idea-explorer"
  function: "brainstorm"

type: unit
priority: critical

input:
  data:
    topic: "废柴逆袭"
    genre: "玄幻"
    requirements: ["要有创新金手指", "要有情感线"]
  parameters:
    count: 5
    style: "traditional"

expected:
  output:
    ideas_count: 5
    each_idea_has:
      - concept
      - innovation_points
      - market_analysis
  metrics:
    novelty_score: ">= 0.7"
    market_match: ">= 0.6"
    feasibility: ">= 0.5"
  constraints:
    - "必须包含金手指元素"
    - "有明确目标读者"
    - "创新评分 >= 0.7"

validation:
  assertions:
    - "output.ideas.length == 5"
    - "all ideas have concept field"
    - "average novelty >= 0.7"
```

#### TEST-IDEA-002: 创意新颖度评估

```yaml
metadata:
  id: "TEST-IDEA-002"
  name: "创意新颖度评估测试"

target:
  module: "creative_rd"
  skill: "nf-innovation-evaluator"
  function: "score"

type: unit
priority: high

input:
  data:
    idea: "主角可以通过梦境进入他人记忆"
    criteria: ["novelty", "feasibility", "market_potential"]

expected:
  output:
    has_scores: true
    has_analysis: true
  metrics:
    novelty: ">= 0.6"
    feasibility: ">= 0.5"
    market_potential: ">= 0.6"
```

### 2. 市场分析模块 (TEST-MARKET)

#### TEST-MARKET-001: 类型市场分析

```yaml
metadata:
  id: "TEST-MARKET-001"
  name: "科幻类型市场分析测试"

target:
  module: "creative_rd"
  skill: "nf-market-analyzer"
  function: "genre"

type: unit
priority: high

input:
  data:
    genre: "科幻"
    period: "6m"

expected:
  output:
    has_trend_data: true
    has_competitor_analysis: true
    has_reader_insights: true
  metrics:
    data_completeness: "= 100%"
    analysis_depth: ">= 0.8"
```

### 3. 架构设计模块 (TEST-ARCH)

#### TEST-ARCH-001: 篇幅规划

```yaml
metadata:
  id: "TEST-ARCH-001"
  name: "长篇小说的篇幅规划测试"

target:
  module: "architecture"
  skill: "nf-length-planner"
  function: "plan"

type: unit
priority: critical

input:
  data:
    target_words: 1000000
    type: "long"

expected:
  output:
    chapter_count: ">= 250"
    words_per_chapter: "3000-4000"
    has_structure: true
  constraints:
    - "总字数接近100万"
    - "章节数合理"
    - "有分卷规划"
```

#### TEST-ARCH-002: 世界观一致性检查

```yaml
metadata:
  id: "TEST-ARCH-002"
  name: "世界观设定一致性检查"

target:
  module: "architecture"
  skill: "nf-world-builder"
  function: "consistency"

type: unit
priority: high

input:
  data:
    world_rules:
      magic_system: "消耗生命力"
      max_power: "毁灭城市级"
    story_events:
      - "主角使用魔法拯救村庄"
      - "反派使用魔法毁灭大陆"

expected:
  output:
    has_inconsistencies: true
    inconsistency_count: 1
  validation:
    - "反派行为超出max_power设定"
```

### 4. 内容生成模块 (TEST-CONTENT)

#### TEST-CONTENT-001: 开头章节质量

```yaml
metadata:
  id: "TEST-CONTENT-001"
  name: "开头章节质量检查"

target:
  module: "content_prod"
  skill: "nf-content-generator"
  function: "chapter"

type: integration
priority: critical

input:
  data:
    chapter_number: 1
    outline: "主角登场，展示金手指"
    word_count: 3000

expected:
  checks:
    - "300字内出现主角"
    - "800字内引入冲突"
    - "1500字内亮出金手指"
    - "结尾有悬念"
    - "可读性评分 >= 7"
  metrics:
    word_count: "2800-3200"
    readability: ">= 7.0"
    hook_strength: ">= 0.8"
```

#### TEST-CONTENT-002: 对话优化

```yaml
metadata:
  id: "TEST-CONTENT-002"
  name: "对话符合人物性格测试"

target:
  module: "content_prod"
  skill: "nf-dialogue-optimizer"
  function: "character-fit"

type: unit
priority: high

input:
  data:
    dialogue: "今日天气甚好，吾欲外出游历"
    character_profile:
      age: 20
      background: "现代大学生"
      personality: "活泼开朗"

expected:
  output:
    fit_score: "<= 0.3"
    suggestions: ["语言过于古板，不符合现代大学生身份"]
```

### 5. 质量保证模块 (TEST-QA)

#### TEST-QA-001: 逻辑一致性检查

```yaml
metadata:
  id: "TEST-QA-001"
  name: "时间线逻辑检查"

target:
  module: "quality_assurance"
  skill: "nf-logic-inspector"
  function: "timeline"

type: unit
priority: critical

input:
  data:
    events:
      - { time: "Day 1", event: "主角出生" }
      - { time: "Day 365", event: "主角一岁生日" }
      - { time: "Day 300", event: "主角开始学习" }

expected:
  output:
    has_errors: true
    error_count: 1
    errors:
      - "Day 300 的事件发生在 Day 365 之前，但时间标记错误"
```

#### TEST-QA-002: 合规性检查

```yaml
metadata:
  id: "TEST-QA-002"
  name: "敏感内容检测"

target:
  module: "quality_assurance"
  skill: "nf-compliance-officer"
  function: "scan"

type: unit
priority: critical

input:
  data:
    text: "包含违规内容的文本"
    standard: "strict"

expected:
  output:
    passed: false
    violations: ">= 1"
    risk_level: "high"
```

#### TEST-QA-003: 质量评估

```yaml
metadata:
  id: "TEST-QA-003"
  name: "章节质量综合评估"

target:
  module: "quality_assurance"
  skill: "nf-quality-assessor"
  function: "evaluate"

type: integration
priority: high

input:
  data:
    chapter_text: "章节内容"
    criteria: ["readability", "plot", "character", "emotion"]

expected:
  metrics:
    readability: ">= 6.0"
    plot: ">= 6.0"
    character: ">= 6.0"
    emotion: ">= 6.0"
  overall_grade: ">= B"
```

### 6. 发布运营模块 (TEST-PUB)

#### TEST-PUB-001: 平台适配

```yaml
metadata:
  id: "TEST-PUB-001"
  name: "起点中文网格式适配"

target:
  module: "publishing_ops"
  skill: "nf-platform-adapter"
  function: "format"

type: unit
priority: high

input:
  data:
    content: "原始章节内容"
    platform: "qidian"

expected:
  output:
    format_compliant: true
    has_title_format: true
    word_count_valid: true
```

## 测试执行报告

### 报告模板

```markdown
# 测试执行报告

## 执行概况
- 执行时间: 2024-01-15 10:00:00
- 测试套件: NovelFlow v1.0
- 总用例数: 50
- 通过: 48
- 失败: 2
- 跳过: 0
- 通过率: 96%

## 详细结果

### 创意研发模块 (TEST-IDEA)
| 用例ID | 名称 | 状态 | 耗时 | 备注 |
|--------|------|------|------|------|
| TEST-IDEA-001 | 玄幻题材创意生成 | ✅ 通过 | 2.3s | - |
| TEST-IDEA-002 | 创意新颖度评估 | ✅ 通过 | 1.8s | - |

### 架构设计模块 (TEST-ARCH)
| 用例ID | 名称 | 状态 | 耗时 | 备注 |
|--------|------|------|------|------|
| TEST-ARCH-001 | 篇幅规划 | ✅ 通过 | 0.5s | - |
| TEST-ARCH-002 | 世界观一致性 | ❌ 失败 | 1.2s | 检测到不一致 |

## 失败分析

### TEST-ARCH-002
- **问题**: 世界观规则检测未通过
- **原因**: 魔法系统设定与剧情冲突
- **建议**: 调整剧情或修改设定

## 覆盖率统计
- 代码覆盖率: 87%
- 功能覆盖率: 95%
- 场景覆盖率: 82%
```

## 持续集成

### CI/CD 集成

```yaml
pipeline:
  stages:
    - name: "unit_tests"
      modules: ["idea", "market", "arch"]
      parallel: true
      
    - name: "integration_tests"
      modules: ["content", "qa"]
      depends_on: ["unit_tests"]
      
    - name: "e2e_tests"
      scenario: "full_workflow"
      depends_on: ["integration_tests"]
      
  triggers:
    - push
    - pull_request
    - scheduled: "0 2 * * *"  # 每天凌晨2点
```

## 输出格式
测试报告包含：
- 执行概况
- 详细结果
- 失败分析
- 覆盖率统计
- 改进建议
