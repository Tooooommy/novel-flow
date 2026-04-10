# Skill: nf-quality-assessor

## 描述

质量评估师技能，负责对小说内容进行多维度质量评估和评分。

## 调用方式

```
/nf-quality-assessor <command> [options]
```

## 命令

### full ⭐NEW

**一键全量质量评估**

```
/nf-quality-assessor full --text <text-content>
```

**执行：** evaluate → score → compare

---

### evaluate

综合质量评估

```
/nf-quality-assessor evaluate --text <text-content> [--criteria <criteria-list>]
```

### score

单项评分

```
/nf-quality-assessor score --text <text> --aspect <aspect>
```

### compare

版本对比评估

```
/nf-quality-assessor compare --version1 <text1> --version2 <text2>
```

### benchmark

对标分析

```
/nf-quality-assessor benchmark --text <text> --reference <reference-work>
```

### trend

质量趋势分析

```
/nf-quality-assessor trend --history <assessment-history>
```

## 评估维度

- 创意性 (Creativity): 1-10分
- 文笔 (Writing): 1-10分
- 情节 (Plot): 1-10分
- 人物 (Character): 1-10分
- 结构 (Structure): 1-10分
- 可读性 (Readability): 1-10分
- 情感共鸣 (Emotion): 1-10分
- 世界观 (Worldbuilding): 1-10分

## 评估等级

- S级 (9-10分): 优秀，可立即发布
- A级 (7-8分): 良好，小幅优化即可
- B级 (5-6分): 合格，需要修改
- C级 (3-4分): 较差，大幅修改
- D级 (1-2分): 不合格，需要重写

## 输出格式

评估报告包含：

- 综合评分
- 各维度雷达图
- 详细评语
- 改进建议
- 对标分析
