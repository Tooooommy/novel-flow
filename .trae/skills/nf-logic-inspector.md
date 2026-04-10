---
name: nf-logic-inspector
description: |
  逻辑审查技能。为 `/nf review` 命令提供能力。
  当用户要审查章节逻辑、检查时间线、检查伏笔呼应、验证设定一致性时使用。
---

# 逻辑审查技能

## 使用场景

- 用户要审查章节逻辑
- 用户要检查时间线
- 用户要验证伏笔呼应
- 用户要检查设定一致性

---

## 命令

### full - 逻辑审查

```
/nf-logic-inspector full [--chapter <章节号>]
```

**执行**: consistency → timeline → plotholes

**审查内容**:

- 情节逻辑矛盾
- 人物行为合理
- 时间线连贯
- 设定一致
- 伏笔呼应

**输出**:

```json
{
  "issues": [],
  "passed": true
}
```

---

## 内部命令

### consistency - 连贯性

```
/nf-logic-inspector consistency [--chapter <章节号>]
```

### timeline - 时间线

```
/nf-logic-inspector timeline [--chapter <章节号>]
```

### plotholes - 伏笔

```
/nf-logic-inspector plotholes [--chapter <章节号>]
```

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| LI-001 | 章节不存在 | 返回空结果 |
| LI-002 | 文本为空   | 跳过审查   |
