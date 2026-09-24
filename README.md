# rigor

一个 Claude Code skill：严谨决策与交付流程。

第一性原理拆解 → 先查最佳实践 / 对标 → MECE 结构化 → 最简执行 → 对抗式审查 → 结论先行交付。

防四种常见错误：想当然、重复造轮子、结构混乱、自我感觉良好。

## 安装

个人全局（所有项目可用）：

```bash
git clone https://github.com/okjesse/rigor ~/.claude/skills/rigor
```

单个项目：

```bash
git clone https://github.com/okjesse/rigor .claude/skills/rigor
```

安装后在 Claude Code 里输入 `/rigor` 手动调用。涉及方案设计、技术选型、调研分析、上线或不可逆改动的任务，Claude 也会自动触发。

## 什么时候用

- 方案设计、架构决策、技术选型
- 调研、对标、商业判断
- 要花钱、上线、对外承诺、不可逆的开发改动

一次性、可逆、几分钟能做完的小事不用。

## 内容

见 [SKILL.md](SKILL.md)。
