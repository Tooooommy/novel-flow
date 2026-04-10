# Skill: nf-scene-describer

## 描述

场景描述师技能，负责优化环境描写，营造氛围，丰富感官细节。

## 调用方式

```
/nf-scene-describer <command> [options]
```

## 命令

### full

**一键全量场景描写**

```
/nf-scene-describer full --scene <scene-type> --mood <mood>
```

**执行：** describe → enhance → atmosphere

---

### describe

生成场景描述

```
/nf-scene-describer describe --scene <scene-type> --mood <mood> [--sensory <senses>]
```

### enhance

增强现有描写

```
/nf-scene-describer enhance --text <description-text> --aspect <atmosphere|sensory|emotion>
```

### atmosphere

营造特定氛围

```
/nf-scene-describer atmosphere --text <text> --target-mood <mood>
```

### sensory

增加感官细节

```
/nf-scene-describer sensory --text <text> --senses <visual,auditory,tactile,olfactory,gustatory>
```

### balance

平衡描写与叙事比例

```
/nf-scene-describer balance --text <text> --target-ratio <percentage>
```

## 感官维度

- **视觉**：颜色、形状、光影、动作
- **听觉**：声音、音量、音质、寂静
- **触觉**：温度、质地、触感
- **嗅觉**：气味、香味、臭味
- **味觉**：味道、口感

## 氛围类型

- 紧张压抑
- 轻松愉悦
- 神秘诡异
- 悲伤凄凉
- 温暖治愈
- 宏大壮丽

## 检查清单

- [ ] 描写生动具体
- [ ] 不冗余拖沓
- [ ] 多感官调动
- [ ] 氛围营造到位
- [ ] 与情节氛围匹配

## 输出格式

优化报告包含：

- 原描写分析
- 增强后描写
- 感官细节清单
- 氛围评分
