# Skill: nf-world-builder

## 描述

世界构建师技能，负责构建小说的世界观设定，包括地理环境、历史背景、社会制度、魔法/科技体系等。

## 调用方式

```
/nf-world-builder <command> [options]
```

## 命令

### full

**一键构建完整世界观**

```
/nf-world-builder full --genre <genre> --theme <theme>
```

**执行：** create → geography → history → society → system

---

### create

创建世界观框架

```
/nf-world-builder create --genre <genre> [--theme <theme>] [--scale <small|medium|large|cosmic>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| genre | string | 是 | - | 题材类型 |
| theme | string | 否 | - | 主题要素 |
| scale | string | 否 | medium | 世界规模 |

---

### geography

设计地理环境

```
/nf-world-builder geography --type <world-type> [--features <feature-list>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| type | string | 是 | - | 世界类型 |
| features | string | 否 | - | 地理特征 |

---

### history

构建历史时间线

```
/nf-world-builder history --span <time-span> [--eras <era-count>] [--events <key-events>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| span | string | 是 | - | 时间跨度 |
| eras | number | 否 | 3 | 时代数量 |
| events | string | 否 | - | 关键事件 |

---

### society

设计社会结构

```
/nf-world-builder society --aspects <aspects> [--complexity <simple|moderate|complex>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| aspects | string | 是 | - | 社会方面 |
| complexity | string | 否 | moderate | 复杂程度 |

---

### system

设计规则体系（魔法/科技/超能力）

```
/nf-world-builder system --type <magic|tech|super|mixed> [--constraints <constraints>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| type | string | 是 | - | 规则类型 |
| constraints | string | 否 | - | 限制条件 |

---

### culture

构建文化体系

```
/nf-world-builder culture --elements <customs,languages,religions,arts...>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| elements | string | 是 | - | 文化元素 |

---

### consistency

检查世界观一致性

```
/nf-world-builder consistency --check <world-data>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| check | string | 是 | - | 世界数据 |

## 构建维度

- 物理环境：地理、气候、生态
- 时间维度：历史、时代、未来
- 社会结构：政治、经济、阶级
- 文化体系：语言、宗教、习俗
- 规则体系：魔法、科技、物理法则

## 输出格式

世界设定文档包含：

- 世界观概述
- 详细设定条目
- 设定关系图谱
- 一致性检查报告
