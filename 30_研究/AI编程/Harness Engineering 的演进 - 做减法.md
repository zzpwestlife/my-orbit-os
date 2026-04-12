---
area: "[[AI编程]]"
tags: [AI, Agent, Harness, Anthropic]
created: 2026-04-12
source: "[[Anthropic说：网传的Harness思路过时了，做这3件事就够！.md]]"
---
# Harness Engineering 的演进：做减法

## 核心问题

> 你的 Harness 里，在今天的模型面前有多少东西可以扔掉了？
> **What can I stop doing?**

Anthropic 第二篇 Harness 博客的核心观点：随着模型能力提升，需要定期评估 Harness 的每个组件是否还必要。

## 三个模式

### 1. 用 Claude 已经会的工具
- Claude 在 SWE-bench 上只靠 **bash + text editor** 两个工具就拿了 49%
- Claude 会把通用工具**组合出专用模式**：Agent Skills、Programmatic Tool Calling、Memory Tool 全是 bash + editor 的组合
- 不是给 Claude 造新工具，而是让它用已有工具自己组合出解法

### 2. 让模型自己编排
- 传统假设：每次工具调用结果都回到上下文窗口 → 浪费 token
- 新做法：给 Claude 代码执行工具（bash/REPL），让它**自己写代码**来调用工具、过滤结果、串联逻辑
- 编排权从 harness 转移到模型
- BrowseComp 准确率：45.3% → 61.6%（给了自过滤能力后）

### 3. 让模型自己管上下文和记忆
- **Skills**：YAML frontmatter 预加载概览，完整内容按需 read file 展开
- **Context editing**：选择性删除过时上下文
- **Subagent**：分叉干净的上下文窗口，隔离子任务
- **Compaction**：Claude 自己总结历史上下文（Opus 4.6 达 84%）
- **Memory folder**：给 Claude 可读写的文件夹，让它自己决定持久化什么

## 该保留的 Harness

"做减法"不等于什么都不管：

### 缓存设计
- 动态内容放 prompt 最后
- 新消息追加而非重写 prompt
- 不要中途切换模型（缓存失效）
- 谨慎管理工具增删
- 把 breakpoint 移到最新消息

### 声明式工具做边界
- 需要安全管控/用户交互/审计追踪的动作，从 bash 提出来做成独立工具
- 判断标准：**越难撤销的操作，越值得做成独立工具**
- 例：Claude Code 的 `edit` 工具可做 staleness check，bash 的 `sed` 做不到

## 核心结论

> Harness 的可能性空间不会随模型进步而缩小，它只是在不断变化。你的 harness 里每一个组件，都要定期问一遍：**这个，模型自己能做了吗？**

## 相关概念

- [[Harness Engineering 完整指南]]
- [[Agentic Engineering]]
- [[Claude Code]]
- [[Claude Skills]]
