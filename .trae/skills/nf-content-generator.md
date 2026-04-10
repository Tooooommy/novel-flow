# Skill: nf-content-generator

## 描述

内容生成师技能，负责根据大纲和设定生成小说正文内容。

## 调用方式

```
/nf-content-generator <command> [options]
```

## 命令

### full ⭐NEW

**一键生成完整章节**

```
/nf-content-generator full --chapter <chapter-outline>
```

**执行：** scene → chapter → dialogue → description → action → emotion → monologue

---

### scene

生成场景内容

```
/nf-content-generator scene --outline <scene-outline> [--style <writing-style>] [--length <word-count>]
```

### chapter

生成完整章节

```
/nf-content-generator chapter --outline <chapter-outline> [--previous <prev-chapter-summary>]
```

### dialogue

生成对话内容

```
/nf-content-generator dialogue --characters <char-list> --context <context> [--tone <tone>]
```

### description

生成描写内容

```
/nf-content-generator description --subject <subject> [--type <environment|character|action|emotion>]
```

### action

生成动作场景

```
/nf-content-generator action --event <action-event> [--intensity <level>] [--pov <character>]
```

### emotion

生成情感描写

```
/nf-content-generator emotion --character <character> --situation <situation> [--depth <level>]
```

### monologue

生成内心独白

```
/nf-content-generator monologue --character <character> --thought <thought-topic>
```

## 写作风格

### 核心原则：像人一样写作

AI生成内容最大的问题是"太完美"、"太套路"。要避免以下特征：

#### ❌ AI味道特征（必须避免）

| 特征       | AI典型表现                   | 改进方法                 |
| ---------- | ---------------------------- | ------------------------ |
| 过度解释   | "他很生气，他真的很生气"     | 用动作/细节暗示          |
| 过度修饰   | "璀璨的星光"、"明亮的阳光"   | 用具体细节代替           |
| 机械对仗   | "他微微一笑"、"缓缓睁开眼睛" | 用自然的表达             |
| 堆砌形容词 | "美丽的、善良的、温柔的"     | 用事件展现               |
| 总结性旁白 | "这一幕，让他终身难忘"       | 戛然而止，让读者自己感受 |
| 完美句式   | 每句都是主谓宾完整结构       | 长短句交错               |
| 情绪直白   | "他的内心充满了恐惧"         | 用身体反应：发抖、冷汗   |
| 场景罗列   | "天空是蓝的，草是绿的..."    | 只写与情节相关的细节     |

#### ✅ 人类写作特征（必须学习）

```
1. 不完美性 - 会有省略、留白、跳跃
2. 个人印记 - 有独特的用词习惯
3. 节奏变化 - 长短句交错，有呼吸感
4. 细节选择 - 只写重要的，省略无关的
5. 情绪克制 - 不直接写情绪，让读者体会
6. 对话自然 - 有停顿、有省略、有潜台词
```

### 写作风格类型

- **简洁明快** - 短句为主，动作干脆，适合快节奏网文
- **华丽细腻** - 描写丰富，但不堆砌，适合女频
- **冷峻客观** - 克制情感，用事件推动，适合悬疑
- **幽默诙谐** - 轻松吐槽，适合轻松文
- **悬疑紧张** - 留白、暗示、节奏快
- **温情治愈** - 细节打动人心

## 生成参数

- 字数控制
- 视角选择（第一/第三人称）
- 时态选择
- 语气风格
- 细节密度

## 去AI味道核心技巧

### 1. Show Don't Tell（展示而非陈述）

```markdown
# ❌ AI写法（直接陈述）

林逸感到非常愤怒。

# ✅ 人类写法（用动作展示）

林逸的手在发抖。他想说什么，喉咙却像被什么堵住了。

# ❌ AI写法

这是一个可怕的敌人。

# ✅ 人类写法

那人站在原地没动，林逸却觉得自己的膝盖在发软。
```

### 2. 具体而非抽象

```markdown
# ❌ AI写法（抽象）

陈玉楼脸上露出嘲讽的表情。

# ✅ 人类写法（具体）

陈玉楼嗤了一声，"就你？"
```

### 3. 省略不必要的修饰

```markdown
# ❌ AI写法（过度修饰）

夕阳的余晖洒在演武场上，金色的光芒照耀着林逸孤独的身影。

# ✅ 人类写法（简洁）

林逸站在演武场上，夕阳晒得后背发烫。
```

### 4. 对话要"不完整"

```markdown
# ❌ AI写法（完整对白）

"林逸，你连剑都握不稳，还想修炼？"陈玉楼嘲讽道。

# ✅ 人类写法（口语化、不完整）

"林逸，你连剑都——"陈玉楼笑了声，后面的话没必要说完。
```

### 5. 情绪用身体反应

```markdown
# ❌ AI写法（直接写情绪）

林逸感到悲伤。

# ✅ 人类写法（身体反应）

林逸没说话，转身走了。走出去几步才发现攥紧的拳头指甲已经掐进肉里。
```

## 输出格式

生成内容包含：

- 正文内容（自然流畅，无AI痕迹）
- 生成参数说明
- 与大纲对应关系
- 去AI味道自检标记
