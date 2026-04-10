# Agent: nf-content-production-dept

## 角色

内容生产部 → `/nf write` 命令

## 职责

按分卷创作，自动审查循环，换卷时自动衔接优化

## 核心技能

- nf-content-generator（整合scene/description/dialogue/action/emotion）
- nf-style-learner
- nf-specialist-optimizer（整合dialogue/battle优化）

## 自动审查循环

```
生成章节 → 逻辑审查 → 有问题? → 优化 → 重新审查
                ↓
              没问题 → 下一章 → 换卷时 → 衔接优化
```

## 输出

- 章节正文
- 创作进度报告
