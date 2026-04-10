# Skill: nf-character-designer

## 描述

人物设计师技能，负责设计小说角色的性格、背景、动机和人物关系。

## 调用方式

```
/nf-character-designer <command> [options]
```

## 命令

### full

**一键设计完整角色**

```
/nf-character-designer full --role <role> --name <name>
```

**执行：** create → profile → arc → voice → relationship

---

### create

创建新角色

```
/nf-character-designer create --role <protagonist|antagonist|supporting|minor> [--archetype <archetype>]
```

### profile

生成角色档案

```
/nf-character-designer profile --name <character-name> [--depth <basic|detailed|deep>]
```

### arc

设计角色成长弧

```
/nf-character-designer arc --character <character> [--type <positive|negative|flat|transformation>]
```

### relationship

构建人物关系网

```
/nf-character-designer relationship --characters <char-list> [--map <relationship-types>]
```

### motivation

分析角色动机

```
/nf-character-designer motivation --character <character> [--goal <story-goal>]
```

### voice

设计角色语言风格

```
/nf-character-designer voice --character <character> [--samples <sample-count>]
```

### ensemble

设计角色群像

```
/nf-character-designer ensemble --count <character-count> [--diversity <diversity-level>]
```

## 角色维度

- 外在特征：外貌、身份、职业
- 内在特质：性格、价值观、恐惧
- 背景故事：过去经历、创伤、秘密
- 目标动机：欲望、需求、追求
- 成长弧线：变化轨迹、转折点
- 关系网络：与其他角色的互动

## 输出格式

角色设计文档包含：

- 角色档案卡
- 人物关系图谱
- 成长弧线图
- 语言风格样本
- 角色对比矩阵
