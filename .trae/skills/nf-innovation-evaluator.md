# Skill: nf-innovation-evaluator

## 元数据

- **技能ID**: skill-creative-003
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-creative-rd-dept

---

## 描述

创新评估师技能，负责评估创意的新颖性、可行性和市场潜力，筛选最优创意方向。

## 调用方式

```
/nf-innovation-evaluator <command> [options]
```

## 命令

### full

**一键完整创意评估**

```
/nf-innovation-evaluator full --idea <idea-description>
```

**执行：** score → risk → compare

---

### score

对创意进行多维度评分

```
/nf-innovation-evaluator score --idea <idea-description> [--criteria <criteria-list>]
```

### compare

对比多个创意方案

```
/nf-innovation-evaluator compare --ideas <idea1;idea2;idea3...>
```

### risk

评估创意风险

```
/nf-innovation-evaluator risk --idea <idea-description> [--market <market-context>]
```

### feasibility

可行性分析

```
/nf-innovation-evaluator feasibility --idea <idea-description> [--resources <resource-constraints>]
```

### recommend

推荐最佳创意

```
/nf-innovation-evaluator recommend --ideas <idea-list> [--goal <goal-description>]
```

## 评估维度

- 新颖性 (Novelty): 1-10分
- 可行性 (Feasibility): 1-10分
- 市场潜力 (Market Potential): 1-10分
- 创作难度 (Difficulty): 1-10分
- 差异化 (Differentiation): 1-10分
- 延展性 (Scalability): 1-10分

## 输出格式

评估报告包含：

- 综合评分雷达图（文本形式）
- 各维度详细分析
- SWOT分析
- 最终推荐等级
