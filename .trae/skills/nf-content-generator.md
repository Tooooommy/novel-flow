# Skill: nf-content-generator

## 描述
内容生成师技能，负责根据大纲和设定生成小说正文内容。

## 调用方式
```
/nf-content-generator <command> [options]
```

## 命令

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
- 简洁明快
- 华丽细腻
- 冷峻客观
- 幽默诙谐
- 悬疑紧张
- 温情治愈

## 生成参数
- 字数控制
- 视角选择（第一/第三人称）
- 时态选择
- 语气风格
- 细节密度

## 输出格式
生成内容包含：
- 正文内容
- 生成参数说明
- 与大纲对应关系
- 质量自检标记
