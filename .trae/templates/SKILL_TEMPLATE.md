---
name: skill-template
description: |
  NovelFlow Skill 标准模板。当创建新Skill或修改现有Skill时参考此模板。
  标准结构：YAML frontmatter + 使用场景 + 命令 + 内部命令 + 错误处理。
---

# NovelFlow Skill 标准模板

## 结构规范

所有 NovelFlow Skill 必须包含以下结构：

1. **YAML frontmatter** - 触发机制
2. **使用场景** - 何时使用此技能
3. **命令** - full 主命令
4. **内部命令** - 子命令
5. **错误处理** - 错误码定义

---

## 标准格式

```markdown
---
name: [skill-name]
description: |
  [技能名称]。为 `/nf [command]` 命令提供能力。
  当用户要[功能描述]时使用。
  [可选：整合的其他功能]。
---

# [技能名称]

## 使用场景

- 用户要[场景1]
- 用户要[场景2]

---

## 命令

### full - [命令说明]
```

/[nf-skill-name] full [--param1 <值>]

```

| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| param1 | string | 否 | default | 参数说明 |

**执行**: step1 → step2 → step3

---

## 内部命令

### [sub-command] - [说明]

```

/[nf-skill-name] [sub-command] [--param <值>]

```

---

## 错误处理

| 错误码 | 说明 | 处理方式 |
|--------|------|----------|
| XX-001 | [错误描述] | [处理方式] |
```

---

## 命名规范

- **Skill文件**: `nf-[feature-name].md`
- **Skill名称**: `nf-[feature-name]`
- **命令前缀**: `/nf-` 或 `/nf`
- **错误码**: `[前缀]-[序号]` (如 `SA-001`, `CG-002`)

---

## 触发原则

description 是主要触发机制，应包含：

1. 技能名称和用途
2. 对应的命令
3. 具体使用场景
4. 整合的功能（如果有）
