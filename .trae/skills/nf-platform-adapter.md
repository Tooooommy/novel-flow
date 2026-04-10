# Skill: nf-platform-adapter

## 描述

平台适配师技能，为 `/nf publish` 命令提供平台适配能力。转换格式、检查规范、生成封面文案和发布策略。

## 调用方式

由主控技能 `/nf publish` 调用，无需直接使用。

---

## full

**平台适配**

```
/nf-platform-adapter full --platform <平台> --content <内容>
```

**执行：** format → sensitive → metadata → strategy

---

## 内部子命令

### format

**格式转换**

```
/nf-platform-adapter format --text <文本> --platform <平台>
```

### sensitive

**敏感词处理**

```
/nf-platform-adapter sensitive --text <文本>
```

### metadata

**生成元数据**

```
/nf-platform-adapter metadata --novel <小说信息> --platform <平台>
```

### strategy

**发布策略**

```
/nf-platform-adapter strategy --platform <平台> --update-cycle <更新周期>
```

---

## 支持平台

| 平台        | 特点       | 更新周期建议 |
| ----------- | ---------- | ------------ |
| qidian      | 起点中文网 | 3000字/天    |
| qidian-free | 起点免费版 | 5000字/天    |
| zongheng    | 纵横中文网 | 3000字/天    |
| 17k         | 17K小说网  | 3000字/天    |
| jinjiang    | 晋江文学城 | 2000字/天    |

---

## 错误处理

| 错误码 | 说明       | 处理方式     |
| ------ | ---------- | ------------ |
| PA-001 | 平台不支持 | 使用通用格式 |
| PA-002 | 内容为空   | 返回空结果   |
