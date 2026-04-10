# Skill: nf-dialogue-optimizer

## 描述
对白优化师技能，负责优化小说对话，使其符合人物性格、推动情节发展，并增加潜台词。**核心：让对话听起来像人说的，不是AI说的。**

## 调用方式
```
/nf-dialogue-optimizer <command> [options]
```

## 命令

### analyze
分析对话质量
```
/nf-dialogue-optimizer analyze --text <dialogue-text> --characters <char-profiles>
```

### optimize
优化对话
```
/nf-dialogue-optimizer optimize --text <dialogue-text> --goal <natural|witty|tense|emotional>
```

### character-fit
检查对话是否符合人物性格
```
/nf-dialogue-optimizer character-fit --dialogue <text> --profile <character-profile>
```

### subtext
增加潜台词
```
/nf-dialogue-optimizer subtext --dialogue <text> --context <scene-context>
```

### rhythm
优化对话节奏
```
/nf-dialogue-optimizer rhythm --dialogue <text> --pace <fast|moderate|slow>
```

## 优化维度
- **性格符合度**：对话是否符合人物背景、性格
- **推动情节**：对话是否推进故事发展
- **潜台词**：言外之意，增加层次感
- **节奏感**：长短句搭配，张弛有度
- **自然度**：避免说教，贴近真实
- **去AI味道**：避免完美对白

## AI对话特征检测

```markdown
### ❌ AI典型对话（必须避免）

1. 完整正式对白
   "你好，林逸，很高兴见到你。" vs "哟，林逸。"
   
2. 每次说"说"都用同义词
   "道"、"言"、"答"、"应"、"唤"交替 - 人类只用"说"/"问了"
   
3. 对话标签过于丰富
   "他皱着眉头说道" vs "他说"
   
4. 每句对白都完整
   人类说话经常不完整、被打断、欲言又止
   
5. 对白后全是陈述
   人类说话后经常没有描写，或者只有简单的动作

### ✅ 人类对话特征

1. 不完整 - 经常被打断或省略
2. 口语化 - 有口头语、语气词
3. 欲言又止 - 有话没说完
4. 有潜台词 - 真正的意思没说出口
5. 动作简单 - 可能就一个"哼"或"笑"
```

## 检查清单
- [ ] 对话符合人物性格
- [ ] 对话推动情节发展
- [ ] 存在潜台词或言外之意
- [ ] 节奏张弛有度
- [ ] 避免长篇说教
- [ ] 每个人物有独特语言风格
- [ ] 无AI对话模式（完整对白、替换"说"）

## 输出格式
优化报告包含：
- 原对话分析
- 优化后对话
- 修改说明
- 人物符合度评分
- AI味道去除率
