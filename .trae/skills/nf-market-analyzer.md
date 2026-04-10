# Skill: nf-market-analyzer

## 元数据

- **技能ID**: skill-creative-002
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-creative-rd-dept

---

## 描述

市场分析师技能，负责分析小说市场趋势、读者偏好和竞品情况，为创作决策提供数据支持。

## 调用方式

```
/nf-market-analyzer <command> [options]
```

## 命令

### full

**一键完整市场分析**

```
/nf-market-analyzer full --genre <genre>
```

**执行：** genre → audience → compete

---

### genre

分析特定类型市场

```
/nf-market-analyzer genre <genre-name> [--period <3m|6m|1y|all>]
```

### audience

分析目标读者群体

```
/nf-market-analyzer audience [--genre <genre>] [--demographic <age-group>]
```

### compete

竞品分析报告

```
/nf-market-analyzer compete --title <book-title> [--similar <count>]
```

### gap

发现市场空白机会

```
/nf-market-analyzer gap [--genre <genre>] [--theme <theme>]
```

### predict

预测趋势走向

```
/nf-market-analyzer predict --aspect <aspect> [--horizon <short|medium|long>]
```

## 分析维度

- 热门题材排行
- 读者评分分布
- 评论情感分析
- 价格区间分析
- 更新频率影响
- 平台差异对比

## 输出格式

市场报告包含：

- 市场概况摘要
- 数据可视化（文本图表）
- 机会点识别
- 风险提示
- 策略建议
