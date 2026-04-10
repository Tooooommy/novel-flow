# Skill: nf-logic-inspector

## 描述
逻辑审查官技能，负责检查小说内容的逻辑一致性、情节合理性和设定连贯性。

## 调用方式
```
/nf-logic-inspector <command> [options]
```

## 命令

### full ⭐NEW
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

### timeline
时间线检查
```
/nf-logic-inspector timeline --events <event-list> [--format <linear|parallel>]
```

### consistency
设定一致性检查
```
/nf-logic-inspector consistency --text <text> --world-rules <rules>
```

### character
角色行为一致性
```
/nf-logic-inspector character --actions <action-list> --profile <character-profile>
```

### plot
情节逻辑检查
```
/nf-logic-inspector plot --plot-points <plot-list> [--check <causality|motivation>]
```

### causality
因果关系检查
```
/nf-logic-inspector causality --events <event-chain>
```

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
