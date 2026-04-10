---
name: nf-knowledge-curator
description: |
  知识库管理员技能。负责管理小说创作过程中的知识沉淀、经验总结和最佳实践。
  此技能由 nf-novel-flow 主控统一调度，用户可通过 `/nf learn` 和 `/nf query` 调用。
---

# 知识库管理员技能

## 系统定位

```
用户 → nf-novel-flow（主控） → nf-knowledge-curator（知识管理）
                              ├──→ /nf learn  收集知识
                              └──→ /nf query  查询知识
```

## 调用方式

通过主控技能调用：

```
/nf learn --collect --from 我的作品   # 收集知识
/nf query 战斗描写技巧                # 查询知识
```

直接调用（不推荐）：

```
/nf-knowledge-curator <command> [options]
```

## 命令

### full

**一键完整知识管理**

```
/nf-knowledge-curator full --source <source>
```

**执行：** collect → organize → search

---

### collect

收集知识条目

```
/nf-knowledge-curator collect --source <source> --type <lesson|pattern|template>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| source | string | 是 | - | 来源内容 |
| type | string | 是 | - | 知识类型 |

---

### organize

整理知识库

```
/nf-knowledge-curator organize --category <category> [--tag <tags>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| category | string | 是 | - | 知识分类 |
| tag | string | 否 | - | 标签 |

---

### search

搜索知识库

```
/nf-knowledge-curator search --query <query> [--filter <filters>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| query | string | 是 | - | 搜索查询 |
| filter | string | 否 | - | 过滤条件 |

---

### template

创建模板

```
/nf-knowledge-curator template --type <template-type> [--based-on <reference>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| type | string | 是 | - | 模板类型 |
| based-on | string | 否 | - | 参考模板 |

---

### summarize

总结项目经验

```
/nf-knowledge-curator summarize --project <project-id> [--depth <brief|detailed>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| project | string | 是 | - | 项目ID |
| depth | string | 否 | brief | 总结深度 |

---

### share

导出知识分享

```
/nf-knowledge-curator share --content <content-id> --format <md|pdf|html>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| content | string | 是 | - | 内容ID |
| format | string | 是 | - | 导出格式 |

## 知识类型

- 经验教训 (Lessons Learned)
- 最佳实践 (Best Practices)
- 创作模板 (Templates)
- 技巧方法 (Techniques)
- 工具资源 (Tools & Resources)
- 案例研究 (Case Studies)

## 知识分类

- 创意研发
- 架构设计
- 内容生产
- 质量保证
- 发布运营
- 流程管理

## 输出格式

知识库条目包含：

- 标题和摘要
- 详细内容
- 适用场景
- 使用示例
- 相关链接
- 创建/更新时间
