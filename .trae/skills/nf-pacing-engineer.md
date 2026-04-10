# Skill: nf-pacing-engineer

## 元数据

- **技能ID**: skill-content-001
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-content-production-dept

---

## 描述

节奏工程师技能，负责设计和优化小说的叙事节奏，控制情节推进速度和读者阅读体验。

## 调用方式

```
/nf-pacing-engineer <command> [options]
```

## 命令

### full

**一键设计完整章节节奏**

```
/nf-pacing-engineer full --chapter <chapter-outline>
```

**执行：** analyze → design → tension

---

### analyze

分析现有文本节奏

```
/nf-pacing-engineer analyze --text <text-content> [--chapter <chapter-num>]
```

### design

设计章节节奏方案

```
/nf-pacing-engineer design --chapter <chapter-outline> [--mood <mood-type>]
```

### tension

构建张力曲线

```
/nf-pacing-engineer tension --scene <scene-list> [--target <climax-position>]
```

### transition

设计场景过渡

```
/nf-pacing-engineer transition --from <scene-a> --to <scene-b> [--type <time|space|mood>]
```

### hook

设计章末钩子

```
/nf-pacing-engineer hook --chapter <chapter-content> [--intensity <subtle|moderate|strong>]
```

### balance

平衡叙述与对话比例

```
/nf-pacing-engineer balance --text <text-content> [--target-ratio <ratio>]
```

## 节奏要素

- 场景长度控制
- 句子长度变化
- 段落密度调整
- 对话节奏设计
- 描述与行动比例
- 悬念设置频率

## 节奏类型

- 快节奏：动作场景、追逐、战斗
- 中节奏：对话、探索、发展
- 慢节奏：情感、描写、反思

## 输出格式

节奏分析报告包含：

- 当前节奏分析
- 节奏曲线图
- 优化建议
- 具体修改方案
