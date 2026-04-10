# Skill: nf-compliance-officer

## 描述

安全合规官技能，为 `/nf review` 命令提供合规检查能力。检测敏感内容、违规词汇、平台规范。

## 调用方式

由主控技能 `/nf review` 调用，无需直接使用。

---

## full

**合规审查**

```
/nf-compliance-officer full --chapter <章节号> --level <standard|strict>
```

**执行：** sensitive → vocabulary → platform

**审查内容**:

- 敏感内容检测
- 违规词汇过滤
- 平台规范检查

**输出**:

```json
{
  "issues": [
    {"type": "SENSITIVE", "chapter": 11, "description": "敏感词..."}
  ],
  "passed": true/false
}
```

---

## 内部子命令

### sensitive

**敏感内容检测**

```
/nf-compliance-officer sensitive --text <文本>
```

### vocabulary

**违规词汇检测**

```
/nf-compliance-officer vocabulary --text <文本>
```

---

## 错误处理

| 错误码 | 说明       | 处理方式   |
| ------ | ---------- | ---------- |
| CO-001 | 章节不存在 | 返回空结果 |
| CO-002 | 文本为空   | 跳过审查   |
