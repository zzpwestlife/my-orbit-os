---
title: "Superpowers 结构化工作流系统"
type: wiki
created: 2026-03-27
tags: [知识卡片, AI编程, Claude-Code, Skills, 工作流, Superpowers]
related_project: "[[Claude-Code-工程实践]]"
---
# Superpowers 结构化工作流系统

Superpowers 不是一个传统工具，而是**一套指导 Agent 如何完成任务的系统** —— 由 14 个 Skills 组成的结构化工作流，强行在 Agent 链路中插入设计、测试、审查环节，从根本上提升产出质量。

## 基本信息

- **GitHub**: [obra/superpowers](https://github.com/obra/superpowers)（11 万+ Star）
- **安装量**: 23 万，Anthropic 官方插件市场排名第二（仅次于 Frontend Design）
- **适配**: Claude Code、Codex、OpenCode、Cursor 等所有支持 Agent Skill 的工具
- **安装**: `帮我下载并安装这个插件：https://github.com/obra/superpowers`（安装后需重启）

## 核心理念

> **规划 2 小时，执行 10 分钟，审查 1 小时。**

Agent 天然倾向于拿到任务就写代码，跳过设计、测试、review，产出不可维护的代码。Superpowers 通过强制流程纠正这个问题。

## 14 个 Skills 工作流

整体流程遵循：**规划 → 拆解 → 执行 → 审查 → 复盘**

### 1. Brainstorming（头脑风暴）

苏格拉底式提问 —— **一次只问一个问题**，根据回答决定下一个问什么，层层深入直到需求透彻。与 Plan 模式的并行提问完全不同：
- Plan 模式：一口气甩出多个不痛不痒的问题
- Superpowers：逐个追问，确保问题深入而非浮于表面

还会主动做调研（如查阅 ADHD 阅读辅助研究），给出功能优先级建议，最后提出 **3 个架构方案**，列明优缺点让你选择。

### 2. Using Git Worktrees（版本隔离）

从主分支拉出新分支，所有开发在隔离工作区进行，避免"直接在项目上改 → 改炸了"的常见问题。

### 3. Writing Plans（任务拆解）

把设计文档拆成 **2-5 分钟可完成的开发任务清单**。设计原则：
> "让一个没有品味、没有判断力、没有项目上下文、而且厌恶测试的热情初级工程师也能照着做。"

拆细的好处：
- 能力一般的模型也能执行 → 不依赖顶级模型
- 每完成一个小任务就能验证，出问题马上发现

### 4. Subagent-Driven Development（子 Agent 并行开发）

开多个子 Agent 并行执行任务。每个任务完成后经过**两道检查**：
- **第一轮审查**: 需求符合度 —— 该做的有没有做到，不该做的有没有瞎加，有没有过度设计
- **第二轮审查**: 代码质量 —— 规范性、可维护性

不通过就打回修改，循环直到通过。

### 5. Requesting Code Review（全局审查）

所有任务完成后，派最终审查 Agent 通看全部代码：
- 前面的审查盯**局部**，这一轮盯**全局**
- 检查模块集成、遗漏、整体一致性

最后跑验证、合并回主分支、清理工作区。

## 关键洞察

- **不只适用于开发**：创造任何东西的本质都是 规划-拆解-执行-审查-复盘，也可用于营销方案、PPT、数据分析等
- **弱模型受益更大**：任务拆得足够细、流程足够结构化，非顶级模型也能产出高质量结果
- **AI 时代正确姿势**：执行已经够快了，真正该花时间的是动手之前的规划和之后的审查

## 与现有知识的关联

- [[Claude Code 配置体系]] — .claude 文件夹与 Skills 配置
- [[Claude Code Skills 实践案例]] — Skills 实际使用案例
- [[Autoresearch 方法论]] — 另一种 Skills 自动优化方法

## 来源
- 原文: [@Khazix0918 推文](https://x.com/Khazix0918/status/2037015170091016257)
