# Skill: nf-platform-adapter

## 描述

平台适配师技能，负责将小说内容适配到不同发布平台的格式和规范要求。

## 调用方式

```
/nf-platform-adapter <command> [options]
```

## 命令

### full

**一键全量平台适配**

```
/nf-platform-adapter full --novel <novel-info> --target <platform>
```

**执行：** format → optimize → metadata

---

### format

格式转换

```
/nf-platform-adapter format --text <text> --target <platform>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| text | string | 是 | - | 待转换文本 |
| target | string | 是 | - | 目标平台 |

---

### optimize

平台优化

```
/nf-platform-adapter optimize --content <content> --platform <platform> [--goal <engagement|retention|conversion>]
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| content | string | 是 | - | 待优化内容 |
| platform | string | 是 | - | 目标平台 |
| goal | string | 否 | - | 优化目标 |

---

### metadata

生成平台元数据

```
/nf-platform-adapter metadata --novel <novel-info> --platform <platform>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| novel | string | 是 | - | 小说信息 |
| platform | string | 是 | - | 目标平台 |

---

### preview

生成平台预览

```
/nf-platform-adapter preview --chapter <chapter> --platform <platform>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| chapter | string | 是 | - | 章节内容 |
| platform | string | 是 | - | 目标平台 |

---

### batch

批量适配

```
/nf-platform-adapter batch --chapters <chapter-list> --platform <platform>
```

**参数说明**:
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| chapters | string | 是 | - | 章节列表 |
| platform | string | 是 | - | 目标平台 |

## 支持平台

- 起点中文网
- 晋江文学城
- 豆瓣阅读
- 知乎盐选
- 微信公众号
- 番茄小说
- 七猫小说
- Kindle/ePub

## 适配维度

- 章节长度优化
- 标题格式调整
- 简介/文案优化
- 标签/分类选择
- 封面尺寸要求
- 更新频率建议

## 输出格式

适配报告包含：

- 平台规范摘要
- 适配后内容
- 元数据配置
- 发布建议
