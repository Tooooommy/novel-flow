# Skill: nf-platform-adapter

## 元数据

- **技能ID**: skill-publishing-001
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-publishing-ops-dept

---

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

### optimize

平台优化

```
/nf-platform-adapter optimize --content <content> --platform <platform> [--goal <engagement|retention|conversion>]
```

### metadata

生成平台元数据

```
/nf-platform-adapter metadata --novel <novel-info> --platform <platform>
```

### preview

生成平台预览

```
/nf-platform-adapter preview --chapter <chapter> --platform <platform>
```

### batch

批量适配

```
/nf-platform-adapter batch --chapters <chapter-list> --platform <platform>
```

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
