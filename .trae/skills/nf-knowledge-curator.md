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

## 知识模板

### 问题记录模板

```yaml
问题记录:
  id: "ISSUE-001"
  类型: "逻辑矛盾" | "AI味道" | "节奏问题" | "其他"
  场景: "第X章-Y场景"
  错误代码: "LOGIC-001"  # 预定义错误码
  描述: "问题详细描述"
  原因分析: "为什么会出错"
  解决方案: "如何修复"
  关联技能: ["logic-inspector", "specialist-optimizer"]
  预防措施: "如何避免同类问题"
  创建时间: "2026-01-01"
  状态: "open" | "resolved" | "closed"
```

### 经验记录模板

```yaml
经验记录:
  id: "EXP-001"
  类型: "成功经验" | "失败教训" | "最佳实践"
  适用场景: "玄幻题材战斗描写"
  核心内容: "具体方法或规则"
  效果验证: "应用后的效果数据"
  关联项目: ["项目A", "项目B"]
  创建时间: "2026-01-01"
  状态: "pending" | "verified" | "archived"
```

### 战斗描写模板

```yaml
战斗描写:
  id: "BATTLE-TPL-001"
  适用场景: "高强度对决"
  结构:
    - 开局: "招式名+起手动作"
    - 攻防: "3-5动作循环"
    - 高潮: "关键一击+心理"
    - 结束: "结果+余韵"
  技巧:
    - "动作连续不超过3个短句"
    - "每2-3动作插入环境/心理"
    - "用身体反应替代抽象感受"
```

### 对话模板

```yaml
对话模板:
  id: "DIALOG-TPL-001"
  类型: "试探对话"
  结构:
    - 第一层: "表面客气话"
    - 第二层: "试探性提问"
    - 第三层: "暗示/威胁"
    - 第四层: "沉默/转移"
  技巧:
    - "省略主语增加自然感"
    - "用反问代替直陈"
    - "动作配合台词"
```

---

## 输出格式

知识库条目包含：

- 标题和摘要
- 详细内容
- 适用场景
- 使用示例
- 相关链接
- 创建/更新时间
