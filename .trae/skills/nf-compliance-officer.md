# Skill: nf-compliance-officer

## 描述
安全合规官技能，负责检查小说内容的合规性，包括敏感内容、版权问题和平台规范。

## 调用方式
```
/nf-compliance-officer <command> [options]
```

## 命令

### full ⭐NEW
**一键全量合规审查**
```
/nf-compliance-officer full --text <text-content>
```
**执行：** scan → sensitive → copyright

---

### scan
内容合规扫描
```
/nf-compliance-officer scan --text <text-content> [--standard <platform|general|strict>]
```

### sensitive
敏感内容检测
```
/nf-compliance-officer sensitive --text <text> [--categories <category-list>]
```

### copyright
版权检查
```
/nf-compliance-officer copyright --text <text> [--check <quotes|references|similarity>]
```

### platform
平台规范检查
```
/nf-compliance-officer platform --text <text> --platform <platform-name>
```

### rating
内容分级评估
```
/nf-compliance-officer rating --text <text> [--system <age-rating|content-label>]
```

## 检查类别
- 政治敏感
- 暴力描写
- 性相关内容
- 歧视性内容
- 违法内容
- 版权侵权
- 隐私泄露
- 虚假信息

## 平台规范
- 起点中文网
- 晋江文学城
- 豆瓣阅读
- 微信公众号
- 出版规范

## 输出格式
合规报告包含：
- 风险等级评估
- 具体问题列表
- 位置定位
- 修改建议
- 合规评分
