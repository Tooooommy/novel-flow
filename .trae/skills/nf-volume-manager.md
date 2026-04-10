---
name: nf-volume-manager
description: |
  分卷管理技能。为 `/nf outline` 命令提供能力。
  当用户要生成分卷大纲、管理分卷状态、拆分总大纲时使用。
---

# 分卷管理技能

## 使用场景

- 用户要生成分卷大纲
- 用户要管理分卷状态
- 用户要拆分总大纲

---

## 命令

### full - 生成分卷大纲

```
/nf-volume-manager full --outline <总大纲> --volumes <卷数> --chapters <每卷章数>
```

**执行**: split → create → plan

**输出**:

```
novels/{project}/
├── outline.md
├── volume-1.md
├── volume-2.md
└── volume-3.md
```

---

## 内部命令

### split - 拆分大纲

```
/nf-volume-manager split --outline <总大纲> --volumes <卷数>
```

### create - 创建分卷

```
/nf-volume-manager create --volume-num <序号> --plot <情节>
```

### status - 分卷状态

```
/nf-volume-manager status --project <项目>
```

---

## 错误处理

| 错误码 | 说明     | 处理方式     |
| ------ | -------- | ------------ |
| VM-001 | 大纲为空 | 使用默认结构 |
| VM-002 | 卷数无效 | 默认3卷      |
