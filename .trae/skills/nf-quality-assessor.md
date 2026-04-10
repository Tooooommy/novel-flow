---
name: nf-quality-assessor
description: |
  质量评估技能。为 `/nf review` 命令提供能力。
  当用户要评估章节质量、评分可读性、评分情感表达、评分节奏控制时使用。
---

# 质量评估技能

## 使用场景

- 用户要评估章节质量
- 用户要评分可读性
- 用户要评分情感表达
- 用户要评分节奏控制

---

## 命令

### full - 质量评估

```
/nf-quality-assessor full [--chapter <章节号>]
```

**执行**: readability → emotion → pacing → character

**评估维度**:
- 可读性评分
- 情感表达评分
- 节奏控制评分
- 人物塑造评分

**输出**:
```json
{
  "scores": {
    "readability": 85,
    "emotion": 78,
    "pacing": 82,
    "character": 80
  },
  "overall": 81,
  "passed": true
}
```

---

## 内部命令

### readability - 可读性

```
/nf-quality-assessor readability [--text <文本>]
```

### emotion - 情感

```
/nf-quality-assessor emotion [--text <文本>]
```

### pacing - 节奏

```
/nf-quality-assessor pacing [--text <文本>]
```

### character - 人物

```
/nf-quality-assessor character [--text <文本>]
```

---

## 错误处理

| 错误码 | 说明 | 处理方式 |
|--------|------|----------|
| QA-001 | 章节不存在 | 返回空结果 |
| QA-002 | 文本为空 | 跳过评估 |
