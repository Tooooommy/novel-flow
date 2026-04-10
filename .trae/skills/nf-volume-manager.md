# Skill: nf-volume-manager

## 描述

分卷管理技能，为 `/nf outline` 命令提供分卷大纲生成能力。拆分总大纲为分卷大纲，管理各分卷创作状态。

## 调用方式

由主控技能 `/nf outline` 调用，无需直接使用。

---

## full

**生成分卷大纲**

```
/nf-volume-manager full --outline <总大纲> --volumes <卷数> --chapters <每卷章数>
```

**执行：** split → create → plan

**输出结构**:
```
novels/{project}/
├── outline.md          # 总大纲
├── volume-1.md         # 第一卷大纲
├── volume-2.md         # 第二卷大纲
└── volume-3.md         # 第三卷大纲
```

---

## 内部子命令

### split

**拆分大纲**

```
/nf-volume-manager split --outline <总大纲> --volumes <卷数>
```

### create

**创建分卷**

```
/nf-volume-manager create --volume-num <序号> --plot <情节>
```

### status

**分卷状态**

```
/nf-volume-manager status --project <项目>
```

---

## 错误处理

| 错误码 | 说明 | 处理方式 |
|--------|------|----------|
| VM-001 | 大纲为空 | 使用默认结构 |
| VM-002 | 卷数无效 | 默认3卷 |
