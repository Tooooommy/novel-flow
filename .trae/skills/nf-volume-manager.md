# Skill: nf-volume-manager

## 元数据

- **技能ID**: skill-process-003
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-process-coordinator

---

## 描述

分卷管理技能，负责将小说整体大纲拆分为多个分卷大纲，并管理各分卷的创作状态。

## 调用方式

```
/nf-volume-manager <command> [options]
```

## 命令

### full

**一键完整分卷管理**

```
/nf-volume-manager full --outline <main-outline> --volumes <count>
```

**执行：** split → create → list

---

### split

拆分整体大纲为分卷大纲

```
/nf-volume-manager split --outline <main-outline> --volumes <count> [--strategy <equal|plot|character>]
```

### create

创建分卷大纲

```
/nf-volume-manager create --volume-number <n> --total-volumes <total> --main-plot <plot-points>
```

### list

列出所有分卷状态

```
/nf-volume-manager list [--project <project-id>] [--status <status>]
```

### update

更新分卷状态

```
/nf-volume-manager update --volume <n> --status <status> [--progress <percentage>]
```

### get

获取分卷大纲详情

```
/nf-volume-manager get --volume <n> [--format <full|summary>]
```

### validate

验证分卷大纲一致性

```
/nf-volume-manager validate [--check <continuity|character|plot>]
```

## 分卷策略

### 1. 等字数拆分 (equal)

按字数平均分配，适合篇幅固定的作品

```yaml
总字数: 900000
分卷数: 3
每卷字数: 300000
每卷章节: 100章
```

### 2. 剧情节点拆分 (plot)

按剧情高潮点拆分，适合情节驱动的作品

```yaml
第一卷: 铺垫 + 第一高潮
第二卷: 发展 + 第二高潮
第三卷: 决战 + 结局
```

### 3. 人物成长拆分 (character)

按主角成长阶段拆分，适合成长型作品

```yaml
第一卷: 入门期
第二卷: 成长期
第三卷: 巅峰期
```

## 分卷大纲结构

```yaml
volume_outline:
  metadata:
    volume_number: 1
    volume_title: "第一卷：觉醒"
    total_volumes: 3
    word_count: 300000
    chapters: 100

  plot_arc:
    theme: "本卷主题"
    starting_state: "主角初始状态"
    ending_state: "主角卷末状态"
    main_conflict: "核心冲突"
    climax_chapter: 85

  chapter_outlines:
    - chapter: 1
      title: "章节标题"
      word_count: 3000
      plot_point: "情节点"
      characters: ["主角", "配角A"]
      hook: "章末钩子"

  continuity:
    previous_volume: null
    next_volume: 2
    key_events_to_continue: []
    foreshadowing: []

  dependencies:
    requires: [] # 依赖其他卷的内容
    provides: [] # 为其他卷提供的内容
```

## 分卷状态管理

```yaml
volume_status:
  volume_1:
    status: completed # pending / in_progress / completed / failed
    progress: 100%
    chapters_completed: 100/100
    quality_score: 8.5
    assigned_agent: "content-prod-01"

  volume_2:
    status: in_progress
    progress: 45%
    chapters_completed: 45/100
    quality_score: null
    assigned_agent: "content-prod-02"

  volume_3:
    status: pending
    progress: 0%
    chapters_completed: 0/100
    quality_score: null
    assigned_agent: null
```

## 一致性检查

### 连续性检查

- [ ] 时间线连续
- [ ] 人物状态一致
- [ ] 剧情衔接自然
- [ ] 伏笔呼应完整

### 人物一致性

- [ ] 性格发展合理
- [ ] 能力成长符合设定
- [ ] 关系变化有依据

### 剧情逻辑

- [ ] 因果关系清晰
- [ ] 转折有铺垫
- [ ] 结局符合发展

## 输出格式

分卷管理报告包含：

- 分卷大纲列表
- 各卷状态概览
- 一致性检查结果
- 依赖关系图
