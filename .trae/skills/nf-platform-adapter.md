---
name: nf-platform-adapter
description: |
  平台适配技能。为 `/nf publish` 命令提供能力。
  当用户要将小说发布到特定平台、转换格式、检查敏感词时使用。
  支持5大网文平台。
---

# 平台适配技能

## 使用场景

- 用户要将小说发布到特定平台
- 用户要转换格式
- 用户要检查敏感词
- 用户要生成封面文案

---

## 支持平台

| 平台        | 特点       | 更新周期  |
| ----------- | ---------- | --------- |
| qidian      | 起点中文网 | 3000字/天 |
| qidian-free | 起点免费版 | 5000字/天 |
| zongheng    | 纵横中文网 | 3000字/天 |
| 17k         | 17K小说网  | 3000字/天 |
| jinjiang    | 晋江文学城 | 2000字/天 |

---

## 命令

### full - 平台适配

```
/nf-platform-adapter full --platform <平台> --content <内容>
```

| 参数     | 类型   | 必填 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| platform | string | 是   | -      | 目标平台 |
| content  | string | 是   | -      | 小说内容 |

**执行**: format → sensitive → metadata → strategy

---

## 内部命令

### format - 格式转换

```
/nf-platform-adapter format --text <文本> --platform <平台>
```

### sensitive - 敏感词

```
/nf-platform-adapter sensitive --text <文本>
```

### metadata - 元数据

```
/nf-platform-adapter metadata --novel <信息> --platform <平台>
```

### strategy - 发布策略

```
/nf-platform-adapter strategy --platform <平台> --cycle <周期>
```

---

## 错误处理

| 错误码 | 说明       | 处理方式     |
| ------ | ---------- | ------------ |
| PA-001 | 平台不支持 | 使用通用格式 |
| PA-002 | 内容为空   | 返回空结果   |
