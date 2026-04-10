# Skill: nf-world-builder

## 元数据

- **技能ID**: skill-architecture-002
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-architecture-design-dept

---

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

### geography

设计地理环境

```
/nf-world-builder geography --type <world-type> [--features <feature-list>]
```

### history

构建历史时间线

```
/nf-world-builder history --span <time-span> [--eras <era-count>] [--events <key-events>]
```

### society

设计社会结构

```
/nf-world-builder society --aspects <aspects> [--complexity <simple|moderate|complex>]
```

### system

设计规则体系（魔法/科技/超能力）

```
/nf-world-builder system --type <magic|tech|super|mixed> [--constraints <constraints>]
```

### culture

构建文化体系

```
/nf-world-builder culture --elements <customs,languages,religions,arts...>
```

### consistency

检查世界观一致性

```
/nf-world-builder consistency --check <world-data>
```

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
