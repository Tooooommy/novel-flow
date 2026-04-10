# Skill: nf-idea-explorer

## 描述

创意探索师技能，负责小说创意的发散性思考、概念探索和灵感挖掘。

## 调用方式

```
/nf-idea-explorer <command> [options]
```

## 命令

### full ⭐NEW

**一键执行全部创意探索**

```
/nf-idea-explorer full --topic <topic>
```

**执行：** brainstorm → expand → twist → trend

---

### brainstorm

针对主题进行头脑风暴

```
/nf-idea-explorer brainstorm --topic <topic> [--count <number>] [--style <genre>]
```

### expand

扩展已有创意概念

```
/nf-idea-explorer expand --concept <concept> [--direction <direction>]
```

### combine

组合多个创意元素

```
/nf-idea-explorer combine --elements <elem1,elem2,elem3...> [--constraint <constraint>]
```

### twist

为故事添加反转或新意

```
/nf-idea-explorer twist --plot <plot-summary> [--type <ending|character|setting|twist>]
```

### trend

分析当前创意趋势

```
/nf-idea-explorer trend [--genre <genre>] [--timeframe <recent|classic|future>]
```

## 创意维度

- 核心概念（What if...）
- 世界观设定
- 角色原型
- 冲突类型
- 主题深度
- 叙事视角

## 输出格式

创意报告包含：

- 创意概念列表（含新颖度评分）
- 每个概念的发展潜力分析
- 推荐优先级
- 风险提示
