# Skill: nf-knowledge-curator

## 描述
知识库管理员技能，负责管理小说创作过程中的知识沉淀、经验总结和最佳实践。

## 调用方式
```
/nf-knowledge-curator <command> [options]
```

## 命令

### full ⭐NEW
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

### organize
整理知识库
```
/nf-knowledge-curator organize --category <category> [--tag <tags>]
```

### search
搜索知识库
```
/nf-knowledge-curator search --query <query> [--filter <filters>]
```

### template
创建模板
```
/nf-knowledge-curator template --type <template-type> [--based-on <reference>]
```

### summarize
总结项目经验
```
/nf-knowledge-curator summarize --project <project-id> [--depth <brief|detailed>]
```

### share
导出知识分享
```
/nf-knowledge-curator share --content <content-id> --format <md|pdf|html>
```

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
