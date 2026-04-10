# Skill: nf-specialist-optimizer

## 描述

专业优化师技能，负责对生成内容进行专业化优化，包括文笔润色、风格统一和细节增强。**核心功能：去除AI味道**

## 调用方式

```
/nf-specialist-optimizer <command> [options]
```

## 命令

### full

**一键全量优化（推荐）**

```
/nf-specialist-optimizer full --text <text-content>
```

**执行：** humanize → tighten → enhance → dialogue → polish

---

### humanize

**去AI味道（核心功能）**

```
/nf-specialist-optimizer humanize --text <text-content>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待处理文本 |

**检查清单：**

- [ ] 删除过度解释性词语（"似乎"、"仿佛"、"不由得"）
- [ ] 替换机械化的副词（"缓缓"、"轻轻"、"微微"）
- [ ] 去除完美对仗句式
- [ ] 情绪用身体反应而非直接陈述
- [ ] 对话口语化，允许不完整
- [ ] 去除总结性旁白
- [ ] 长短句交错

---

### polish

润色文本

```
/nf-specialist-optimizer polish --text <text-content> [--focus <clarity|flow|vividness|emotion>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待润色文本 |
| focus | string | 否 | - | 润色重点 |

---

### unify

统一风格

```
/nf-specialist-optimizer unify --text <text-content> --style <target-style> [--samples <sample-texts>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待统一文本 |
| style | string | 是 | - | 目标风格 |
| samples | string | 否 | - | 风格样本 |

---

### enhance

增强细节

```
/nf-specialist-optimizer enhance --text <text-content> --aspect <sensory|emotional|descriptive>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待增强文本 |
| aspect | string | 是 | - | 增强方面 |

---

### tighten

精简冗余

```
/nf-specialist-optimizer tighten --text <text-content> [--target-reduction <percentage>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待精简文本 |
| target-reduction | number | 否 | 20 | 目标压缩比 |

---

### expand

扩展内容

```
/nf-specialist-optimizer expand --text <text-content> --direction <emotional|descriptive|action>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待扩展文本 |
| direction | string | 是 | - | 扩展方向 |

---

### dialogue

优化对话

```
/nf-specialist-optimizer dialogue --text <dialogue-text> [--goal <natural|witty|tense>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 对话文本 |
| goal | string | 否 | natural | 优化目标 |

---

### show-dont-tell

转换叙述方式

```
/nf-specialist-optimizer show-dont-tell --text <text-content>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待转换文本 |

## 优化维度

- 语言流畅度
- 用词精准度
- 句式多样性
- 画面感
- 情感共鸣
- 节奏韵律
- **去AI味道程度**

## AI味道检测清单

使用此清单检查文本是否还有AI味道：

```markdown
### 段落级检查

- [ ] 没有连续3个以上形容词堆砌
- [ ] 没有"不由得"、"似乎"、"仿佛"等缓冲词
- [ ] 没有"缓缓睁开眼睛"、"微微一笑"等机械动作
- [ ] 没有直接的情绪陈述（"他很愤怒"）
- [ ] 对话不是严格的"说"+"回答"格式

### 句子级检查

- [ ] 长短句交错（有呼吸感）
- [ ] 有省略句（符合口语习惯）
- [ ] 没有每句都是完整主谓宾
- [ ] 用具体细节替代抽象概括

### 用词级检查

- [ ] 删除了多余的副词
- [ ] 没有"璀璨的"、"明亮的"等过度修饰
- [ ] 用动词而非名词堆砌
```

## 输出格式

优化报告包含：

- 优化前后对比
- 修改说明
- 优化统计（修改点数量、字数变化）
- 质量评分提升
- AI味道残留率（目标<10%）
