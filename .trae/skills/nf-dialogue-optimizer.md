# Skill: nf-dialogue-optimizer

## 描述
对白优化师技能，负责优化小说对话，使其符合人物性格、推动情节发展，并增加潜台词。

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

## 检查清单
- [ ] 对话符合人物性格
- [ ] 对话推动情节发展
- [ ] 存在潜台词或言外之意
- [ ] 节奏张弛有度
- [ ] 避免长篇说教
- [ ] 每个人物有独特语言风格

## 输出格式
优化报告包含：
- 原对话分析
- 优化后对话
- 修改说明
- 人物符合度评分
