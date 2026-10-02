# continuation-prompt · 新对话接续提示词生成器

一个 AI Agent 技能（Skill）：为「新对话接续任务」自动生成或增量更新**新对话接续提示词**（接力提示词 / continuation prompt）。

用户把生成的提示词粘贴到新对话开头，新 AI 即可无缝接续项目上下文——已完成什么、卡在哪、做过什么决策及理由、踩过什么坑——无需翻聊天记录考古。

## 设计理念

参考 [MemTensor/memmy-agent](https://github.com/MemTensor/memmy-agent) 的记忆分层架构：

- **稳定认知 vs 过程状态分层**：关键位置、环境备忘等「稳定」内容与项目现状、待办等「易变」内容分开管理，更新时各按各的生命周期处理（易变改写、稳定慎改、经验只增不改）。
- **策略化避坑条目**：坑/铁律按「触发条件 → 避坑方法 → 验证方式」记录，新对话能按场景对号入座。
- **决策留痕**：记录「结论 + 当时的理由」，包括否决过的方案，防止新对话推翻已定决策或重复提议已否决方案。
- **去重合并**：更新模式增量修改、去重合并，不推倒重写。
- **零提问生成**：全程由 AI 从当前对话、已有提示词、项目文件中自主总结，不向用户提问。

## 使用方法

把本仓库的 `continuation-prompt/` 文件夹复制到你的 skills 目录：

- WorkBuddy：`~/.workbuddy/skills/continuation-prompt/`
- 其他支持 Skill 的 Agent：对应的 skills 目录

然后对 AI 说：

- 「给 XX 项目写个接续提示词」——新建
- 「更新 XX 的提示词」——增量更新已有提示词

## 目录结构

```
continuation-prompt/
├── SKILL.md            # 技能定义：五步工作流（判定模式 → 收集信息 → 定保存位置 → 生成/更新 → 交付）
└── assets/
    └── template.md     # 接续提示词模板：A/B 两种用法、十个章节、生命周期标签
```

## License

MIT License · © 2026 Alicifia

详见 [LICENSE](LICENSE) 文件。
