# Skill: nf-novel-merger

## 元数据

- **技能ID**: skill-process-005
- **版本**: v1.0
- **维护者**: NovelFlow Team
- **创建日期**: 2026-01-01
- **最后更新**: 2026-04-10
- **依赖技能**: 无
- **依赖智能体**: nf-process-coordinator

---

## 描述

小说合并技能，负责将多个分卷内容合并为完整小说，处理衔接、统一风格和生成最终文档。

## 调用方式

```
/nf-novel-merger <command> [options]
```

## 命令

### full

**一键完整合并分卷**

```
/nf-novel-merger full --volumes <volume-files> --output <output-path>
```

**执行：** merge → preview → smooth

---

### merge

合并分卷为完整小说

```
/nf-novel-merger merge --volumes <volume-files> --output <output-path> [--format <format>]
```

### preview

预览合并效果

```
/nf-novel-merger preview --volumes <volume-files> [--sections <sections>]
```

### smooth

优化卷间衔接

```
/nf-novel-merger smooth --volume-a <file-a> --volume-b <file-b> [--strategy <strategy>]
```

### unify

统一全书法风格

```
/nf-novel-merger unify --novel <novel-path> [--aspects <aspects>]
```

### toc

生成目录

```
/nf-novel-merger toc --novel <novel-path> [--style <style>]
```

### export

导出最终文档

```
/nf-novel-merger export --novel <novel-path> --format <epub/mobi/pdf/txt> [--options <options>]
```

## 合并流程

### 1. 内容整合

```yaml
merge_steps:
  1_load:
    action: "加载所有分卷内容"
    validation: "检查文件完整性"

  2_order:
    action: "按卷号排序"
    check: "验证卷号连续性"

  3_connect:
    action: "处理卷间衔接"
    add_transitions: "添加过渡段落"

  4_unify:
    action: "统一全书风格"
    aspects: ["语言", "格式", "术语"]

  5_polish:
    action: "整体润色"
    focus: ["节奏", "连贯性"]

  6_finalize:
    action: "生成最终文档"
    outputs: ["正文", "目录", "元数据"]
```

### 2. 卷间衔接处理

#### 衔接检查清单

- [ ] 时间线连续
- [ ] 人物状态一致
- [ ] 剧情无断层
- [ ] 伏笔有呼应
- [ ] 情绪过渡自然

#### 自动修复策略

```yaml
auto_fix:
  time_gap:
    detection: "检测到时间跳跃"
    fix: "添加过渡章节或时间说明"

  character_inconsistency:
    detection: "人物状态不一致"
    fix: "统一人物状态或添加转变说明"

  plot_hole:
    detection: "剧情漏洞"
    fix: "标记待人工处理"
```

## 风格统一

### 统一维度

```yaml
unify_aspects:
  language:
    - "用词风格统一"
    - "句式结构统一"
    - "修辞手法统一"

  format:
    - "章节标题格式"
    - "段落间距"
    - "对话格式"

  terminology:
    - "专有名词统一"
    - "修炼体系术语"
    - "地名统一"

  tone:
    - "叙述语气统一"
    - "情感基调统一"
```

### 风格分析

```yaml
style_analysis:
  volume_1:
    word_choice: "简洁明快"
    sentence_length: "中等"
    emotion_density: "中等"

  volume_2:
    word_choice: "华丽细腻"
    sentence_length: "较长"
    emotion_density: "高"

  # 检测到风格差异，建议统一
```

## 目录生成

### 目录结构

```markdown
# 《小说名称》

## 目录

### 第一卷：卷名

- 第1章 章节名
- 第2章 章节名
- ...
- 第100章 章节名

### 第二卷：卷名

- 第101章 章节名
- 第102章 章节名
- ...

### 第三卷：卷名

...

## 番外

...
```

### 目录样式选项

```yaml
toc_styles:
  simple:
    format: "第X章 章节名"

  detailed:
    format: "第X章 章节名 - 简要内容"

  with_summary:
    format: "第X章 章节名\n    本章概要..."
```

## 导出格式

### 支持格式

```yaml
export_formats:
  txt:
    description: "纯文本格式"
    features: ["基本排版", "UTF-8编码"]

  epub:
    description: "电子书标准格式"
    features: ["目录导航", "字体调整", "多设备兼容"]

  mobi:
    description: "Kindle专用格式"
    features: ["Kindle优化", "字典支持"]

  pdf:
    description: "便携式文档格式"
    features: ["打印优化", "固定排版", "封面支持"]

  docx:
    description: "Word文档格式"
    features: ["可编辑", "便于修改"]
```

### 导出配置

```yaml
export_options:
  metadata:
    title: "小说名称"
    author: "作者名"
    description: "简介"
    cover: "封面图片路径"

  formatting:
    font: "宋体"
    font_size: 12
    line_spacing: 1.5
    paragraph_indent: 2

  chapters:
    page_break: true # 每章新页
    header: true # 页眉显示章节名
```

## 合并质量检查

### 自动检查项

```yaml
quality_checks:
  continuity:
    - "章节编号连续"
    - "页码连续"
    - "无重复内容"

  completeness:
    - "所有分卷已包含"
    - "无缺失章节"
    - "附件完整"

  consistency:
    - "术语统一"
    - "人名统一"
    - "地名统一"

  formatting:
    - "编码正确"
    - "格式规范"
    - "无乱码"
```

### 质量报告

```markdown
# 合并质量报告

## 基本信息

- 小说名称: XXX
- 总字数: 1,200,000
- 总章节: 300章
- 分卷数: 3卷

## 检查结果

✅ 章节编号连续
✅ 所有分卷已包含
⚠️ 术语不一致: 发现3处
✅ 格式规范

## 建议

1. 统一"修炼"与"修行"的用法
2. 检查第156章的时间线
3. 建议添加卷间过渡语
```

## 输出格式

合并报告包含：

- 合并过程日志
- 质量检查结果
- 风格统一报告
- 导出的文档列表
- 后续建议
