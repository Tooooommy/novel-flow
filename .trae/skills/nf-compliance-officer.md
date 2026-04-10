---
name: nf-compliance-officer
description: |
  合规审查技能。为 `/nf review` 命令提供能力。
  当用户要检查敏感内容、过滤违规词汇、检查平台规范时使用。
---

# 合规审查技能

## 使用场景

- 用户要检查敏感内容
- 用户要过滤违规词汇
- 用户要检查平台规范

---

## 命令

### full - 合规审查

```
/nf-compliance-officer full [--chapter <章节号>] [--level <standard|strict>]
```

| 参数    | 类型   | 必填 | 默认值   | 说明     |
| ------- | ------ | ---- | -------- | -------- |
| chapter | number | 否   | 当前     | 章节号   |
| level   | string | 否   | standard | 审查级别 |

**执行**: sensitive → vocabulary → platform

**审查内容**:

- 敏感内容检测
- 违规词汇过滤
- 平台规范检查

**输出**:

```json
{
  "issues": [],
  "passed": true
}
```

---

## 内部命令

### sensitive - 敏感内容

```
/nf-compliance-officer sensitive [--text <文本>]
```

### vocabulary - 词汇

```
/nf-compliance-officer vocabulary [--text <文本>]
```

### platform - 平台规范

```
/nf-compliance-officer platform [--platform <平台>]
```

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| CO-001 | 章节不存在 | 返回空结果 |
| CO-002 | 文本为空   | 跳过审查   |
