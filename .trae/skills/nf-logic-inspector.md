# Skill: nf-logic-inspector

## 描述

逻辑审查官技能，为 `/nf review` 命令提供逻辑审查能力。检查情节合理性、设定连贯性、伏笔呼应。

## 调用方式

由主控技能 `/nf review` 调用，无需直接使用。

---

## full

**逻辑审查**

```
/nf-logic-inspector full --chapter <章节号>
```

**执行：** consistency → timeline → plot-holes

**审查内容**:

- 情节逻辑矛盾
- 人物行为合理
- 时间线连贯
- 设定一致
- 伏笔呼应

**输出**:

```json
{
  "issues": [
    {"type": "LOGIC", "chapter": 5, "description": "..."}
  ],
  "passed": true/false
}
```

---

## 内部子命令

### consistency

**检查连贯性**

```
/nf-logic-inspector consistency --text <文本>
```

### timeline

**检查时间线**

```
/nf-logic-inspector timeline --events <事件列表>
```

### plotholes

**检查伏笔**

```
/nf-logic-inspector plotholes --chapter <章节号>
```

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| LI-001 | 章节不存在 | 返回空结果 |
| LI-002 | 文本为空   | 跳过审查   |
