# Skill: nf-battle-writer

## 元数据

- **技能ID**: skill-content-005
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-content-production-dept

---

## 描述

战斗描写师技能，负责设计动作场景、战术逻辑和紧张感营造。

## 调用方式

```
/nf-battle-writer <command> [options]
```

## 命令

### full

**一键全量战斗描写**

```
/nf-battle-writer full --participants <char-list> --setting <environment>
```

**执行：** design → action → tactic

---

### design

设计战斗场景

```
/nf-battle-writer design --participants <char-list> --setting <environment> [--type <duel|group|siege>]
```

### action

生成动作描写

```
/nf-battle-writer action --move <action-description> [--style <realistic|fantasy|martial-arts>]
```

### tactic

设计战术逻辑

```
/nf-battle-writer tactic --situation <battle-context> --capabilities <abilities>
```

### tension

营造紧张感

```
/nf-battle-writer tension --scene <battle-scene> [--intensity <level>]
```

### pace

控制战斗节奏

```
/nf-battle-writer pace --scene <scene> --pattern <fast-slow-fast|building|sustained>
```

## 战斗要素

- **动作设计**：招式、移动、反应
- **战术逻辑**：策略选择、能力克制
- **空间感**：位置变化、环境利用
- **心理描写**：战斗中的思考、情绪
- **节奏控制**：快慢交替、高潮设计

## 战斗类型

- 单挑对决
- 群战混战
- 攻城守城
- 魔法对决
- 智斗博弈

## 检查清单

- [ ] 动作清晰可想象
- [ ] 战术逻辑合理
- [ ] 空间位置明确
- [ ] 节奏张弛有度
- [ ] 紧张感逐步升级
- [ ] 结果符合设定

## 输出格式

战斗设计文档包含：

- 战斗流程设计
- 动作分解
- 战术分析
- 描写建议
