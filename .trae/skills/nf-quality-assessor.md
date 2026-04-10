# Skill: nf-quality-assessor

## 描述

质量评估师技能，为 `/nf review` 命令提供质量评估能力。多维度评分：可读性、情感表达、节奏控制、人物塑造。

## 调用方式

由主控技能 `/nf review` 调用，无需直接使用。

---

## full

**质量评估**

```
/nf-quality-assessor full --chapter <章节号>
```

**执行：** readability → emotion → pacing → character

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
  "passed": true/false
}
```

---

## 内部子命令

### readability

**可读性评估**

```
/nf-quality-assessor readability --text <文本>
```

### emotion

**情感表达评估**

```
/nf-quality-assessor emotion --text <文本>
```

### pacing

**节奏评估**

```
/nf-quality-assessor pacing --text <文本>
```

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| QA-001 | 章节不存在 | 返回空结果 |
| QA-002 | 文本为空   | 跳过评估   |
