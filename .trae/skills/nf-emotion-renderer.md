# Skill: nf-emotion-renderer

## 描述

情感渲染师技能，负责优化情感表达、心理描写和情感转折。

## 调用方式

```
/nf-emotion-renderer <command> [options]
```

## 命令

### full

**一键全量情感渲染**

```
/nf-emotion-renderer full --scene <scene>
```

**执行：** express → psychology → transition

---

### express

优化情感表达

```
/nf-emotion-renderer express --scene <scene> --emotion <emotion-type> [--intensity <level>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| scene | string | 是 | - | 场景内容 |
| emotion | string | 是 | - | 情感类型 |
| intensity | string | 否 | - | 强烈程度 |

---

### psychology

增强心理描写

```
/nf-emotion-renderer psychology --character <char> --situation <context> [--depth <surface|deep>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| character | string | 是 | - | 角色名称 |
| situation | string | 是 | - | 情境上下文 |
| depth | string | 否 | - | 心理深度 |

---

### transition

设计情感转折

```
/nf-emotion-renderer transition --from <emotion-a> --to <emotion-b> [--pace <gradual|sudden>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| from | string | 是 | - | 起始情感 |
| to | string | 是 | - | 目标情感 |
| pace | string | 否 | - | 转折节奏 |

---

### resonance

增强情感共鸣

```
/nf-emotion-renderer resonance --scene <scene> --target-reader <demographic>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| scene | string | 是 | - | 场景内容 |
| target-reader | string | 是 | - | 目标读者 |

---

### subtlety

增加含蓄表达

```
/nf-emotion-renderer subtlety --text <text> --culture <cultural-context>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待处理文本 |
| culture | string | 是 | - | 文化背景 |

## 情感维度

- **基础情感**：喜、怒、哀、惧、爱、恶、欲
- **复杂情感**：嫉妒、愧疚、自豪、孤独、希望
- **情感层次**：表面情绪 → 深层感受 → 核心需求

## 表达方式

- **直接表达**：内心独白、直接陈述
- **间接表达**：动作暗示、环境烘托
- **对比表达**：前后对比、他人对比
- **象征表达**：物品象征、场景象征

## 检查清单

- [ ] 情感真实自然
- [ ] 有共鸣点
- [ ] 转折合理
- [ ] 层次丰富
- [ ] 不煽情过度
- [ ] 符合人物性格

## 输出格式

情感优化报告包含：

- 原情感描写分析
- 优化后描写
- 情感曲线图
- 共鸣点分析
