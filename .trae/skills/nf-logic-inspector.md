# Skill: nf-logic-inspector

## 描述

逻辑审查官技能，负责检查小说内容的逻辑一致性、情节合理性和设定连贯性。

## 调用方式

```
/nf-logic-inspector <command> [options]
```

## 命令

### full

**一键全量逻辑审查**

```
/nf-logic-inspector full --text <text-content>
```

**执行：** check → timeline → consistency

---

### check

全面逻辑检查

```
/nf-logic-inspector check --text <text-content> [--scope <chapter|act|full>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待检查文本 |
| scope | string | 否 | chapter | 检查范围 |

---

### timeline

时间线检查

```
/nf-logic-inspector timeline --events <event-list> [--format <linear|parallel>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| events | string | 是 | - | 事件列表 |
| format | string | 否 | linear | 时间线格式 |

---

### consistency

设定一致性检查

```
/nf-logic-inspector consistency --text <text> --world-rules <rules>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待检查文本 |
| world-rules | string | 是 | - | 世界规则 |

---

### character

角色行为一致性

```
/nf-logic-inspector character --actions <action-list> --profile <character-profile>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| actions | string | 是 | - | 行为列表 |
| profile | string | 是 | - | 角色档案 |

---

### plot

情节逻辑检查

```
/nf-logic-inspector plot --plot-points <plot-list> [--check <causality|motivation>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| plot-points | string | 是 | - | 情节点列表 |
| check | string | 否 | - | 检查类型 |

---

### causality

因果关系检查

```
/nf-logic-inspector causality --events <event-chain>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| events | string | 是 | - | 事件链 |

## 检查维度

- 时间逻辑：时间顺序、时间跨度
- 空间逻辑：地理位置、移动合理性
- 设定逻辑：世界观规则一致性
- 角色逻辑：行为与性格一致性
- 情节逻辑：因果关系、动机合理性
- 对话逻辑：信息一致性

## 问题等级

- 严重 (Critical)：影响故事理解的逻辑错误
- 重要 (Major)：影响阅读体验的 inconsistency
- 轻微 (Minor)：可忽略的小问题

## 输出格式

审查报告包含：

- 问题清单（按等级分类）
- 问题位置定位
- 修改建议
- 逻辑关系图谱
