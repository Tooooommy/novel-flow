# Skill: nf-idea-explorer

## 描述

创意探索师技能，负责小说创意的发散性思考、概念探索和灵感挖掘。

## 调用方式

```
/nf-idea-explorer <command> [options]
```

## 命令

### full

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

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| topic | string | 是 | - | 探索主题 |
| count | number | 否 | 5 | 生成创意数量 |
| style | string | 否 | - | 题材类型 |

---

### expand

扩展已有创意概念

```
/nf-idea-explorer expand --concept <concept> [--direction <direction>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| concept | string | 是 | - | 待扩展概念 |
| direction | string | 否 | - | 扩展方向 |

---

### combine

组合多个创意元素

```
/nf-idea-explorer combine --elements <elem1,elem2,elem3...> [--constraint <constraint>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| elements | string | 是 | - | 元素列表（逗号分隔） |
| constraint | string | 否 | - | 组合约束 |

---

### twist

为故事添加反转或新意

```
/nf-idea-explorer twist --plot <plot-summary> [--type <ending|character|setting|twist>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| plot | string | 是 | - | 剧情概要 |
| type | string | 否 | twist | 反转类型 |

---

### trend

分析当前创意趋势

```
/nf-idea-explorer trend [--genre <genre>] [--timeframe <recent|classic|future>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| genre | string | 否 | - | 题材类型 |
| timeframe | string | 否 | recent | 时间范围 |

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

---

## 输入输出

### 输入

- **类型**: 文本
- **格式**: 纯文本
- **来源**: 用户

### 输出

- **类型**: 文本
- **格式**: Markdown
- **去向**: 用户

---

## 执行上下文

### 前置条件

- 用户提供主题或初始概念

### 后置状态

- 生成创意概念列表

---

## 错误处理

| 错误码 | 说明         | 处理方式             |
| ------ | ------------ | -------------------- |
| IE-001 | 主题为空     | 提示用户输入有效主题 |
| IE-002 | 概念数量不足 | 提示调整count参数    |
