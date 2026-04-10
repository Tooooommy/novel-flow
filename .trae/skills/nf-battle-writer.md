# Skill: nf-battle-writer

## 描述

战斗描写师技能，负责设计动作场景、战术逻辑和紧张感营造。

## 调用方式

```
/nf-battle-writer <command> [options]
```

## 命令

### full

**一键全量战斗描写**

```
/nf-battle-writer full --participants <char-list> --setting <environment>
```

**执行：** design → action → tactic

---

### design

设计战斗场景

```
/nf-battle-writer design --participants <char-list> --setting <environment> [--type <duel|group|siege>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| participants | string | 是 | - | 参战角色列表 |
| setting | string | 是 | - | 战斗环境 |
| type | string | 否 | - | 战斗类型 |

---

### action

生成动作描写

```
/nf-battle-writer action --move <action-description> [--style <realistic|fantasy|martial-arts>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| move | string | 是 | - | 动作描述 |
| style | string | 否 | - | 动作风格 |

---

### tactic

设计战术逻辑

```
/nf-battle-writer tactic --situation <battle-context> --capabilities <abilities>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| situation | string | 是 | - | 战斗情境 |
| capabilities | string | 是 | - | 能力设定 |

---

### tension

营造紧张感

```
/nf-battle-writer tension --scene <battle-scene> [--intensity <level>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| scene | string | 是 | - | 战斗场景 |
| intensity | string | 否 | - | 紧张程度 |

---

### pace

控制战斗节奏

```
/nf-battle-writer pace --scene <scene> --pattern <fast-slow-fast|building|sustained>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| scene | string | 是 | - | 场景内容 |
| pattern | string | 是 | - | 节奏模式 |

## 战斗要素

- **动作设计**：招式、移动、反应
- **战术逻辑**：策略选择、能力克制
- **空间感**：位置变化、环境利用
- **心理描写**：战斗中的思考、情绪
- **节奏控制**：快慢交替、高潮设计

## 战斗类型

- 单挑对决
- 群战混战
- 攻城守城
- 魔法对决
- 智斗博弈

## 检查清单

- [ ] 动作清晰可想象
- [ ] 战术逻辑合理
- [ ] 空间位置明确
- [ ] 节奏张弛有度
- [ ] 紧张感逐步升级
- [ ] 结果符合设定

## 输出格式

战斗设计文档包含：

- 战斗流程设计
- 动作分解
- 战术分析
- 描写建议
