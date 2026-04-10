---
name: agent-template
description: |
  NovelFlow Agent 标准模板。当创建新Agent或修改现有Agent时参考此模板。
  标准结构：YAML frontmatter + 角色 + 职责 + 核心技能 + 工作流 + 输出。
---

# NovelFlow Agent 标准模板

## 结构规范

所有 NovelFlow Agent 必须包含以下结构：

1. **YAML frontmatter** - 名称和描述
2. **角色** - Agent 职责定位
3. **核心技能** - 绑定的 Skills
4. **工作流** - 执行流程
5. **输出** - 交付物

---

## 标准格式

```markdown
---
name: [agent-name]
description: |
  [Agent名称] → `/nf [command]` 命令
  [职责描述]。
---

# [Agent名称]

## 角色

[部门名称] → `/nf [command]` 命令

## 职责

[主要职责描述]

## 核心技能

- [Skill名称]（[整合内容]）

## 工作流
```

[流程图]

```

## 输出

- [输出物1]
- [输出物2]
```

---

## 部门映射

| Agent                             | 命令    | 核心Skill            |
| --------------------------------- | ------- | -------------------- |
| nf-process-coordinator            | 主控    | -                    |
| nf-creative-rd-dept               | idea    | nf-idea-explorer     |
| nf-architecture-design-dept       | outline | nf-story-architect   |
| nf-content-production-dept        | write   | nf-content-generator |
| nf-quality-assurance-dept         | review  | nf-logic-inspector等 |
| nf-publishing-ops-dept            | publish | nf-platform-adapter  |
| nf-retrospection-improvement-dept | auto    | nf-process-analyst   |

---

## 命名规范

- **Agent文件**: `nf-[dept-name].md`
- **Agent名称**: `nf-[dept-name]`
- **命令映射**: 对应 `/nf [command]`
