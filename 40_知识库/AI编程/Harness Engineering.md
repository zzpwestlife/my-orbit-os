---
area: "[[AI编程]]"
tags: [AI, Agent, 工程化]
created: 2026-04-12
---
# Harness Engineering

## 定义

Harness Engineering 是为 AI Agent 构建**约束、引导与纠正机制**的工程体系。它是除了 LLM 本身之外，让 Agent 真正能干活的一切基础设施。

核心隐喻："马与缰绳" —— 为强大但方向不定的"野马"（AI Agent）套上"缰绳"（Harness），确保它能沿着预设轨道稳定前行。

## 要点

- **不是 Prompt Engineering**：Harness 是优化模型运行的环境与机制，而非更好的提示词
- **R.E.S.T 模型**：可靠性（Reliability）、效率（Efficiency）、安全性（Security）、可观测性（Traceability）
- **REPL 容器**：Read（上下文管理）→ Eval（工具执行）→ Print（反馈注入）→ Loop（持续循环）
- **核心挑战**：在"无限"的外部世界状态与"有限"的 LLM Token 之间建立双向映射
- **持续演进**：随着模型能力提升，部分 Harness 会被内化或更替

## Anthropic 2026 新思路

**核心问题**：What can I stop doing?（有多少东西可以扔掉了？）

1. **用 Claude 已经会的东西**：bash + text editor 组合出所有能力
2. **让模型自己编排**：给代码执行工具，让模型自己串联逻辑
3. **让模型自己管上下文与记忆**：Skills、Context editing、Subagent、Memory folder

## 示例

- **[[Claude Code]]**：用 bash + text editor + edit 工具构建的 Harness
- **Memory folder**：给 Agent 一个可读写文件夹，让它自己决定持久化什么
- **策略门控**：在规划器与执行层之间做权限检查、敏感数据过滤、指令注入防御

## 相关概念

- [[AI Agent]]
- [[Agentic Memory]]
- [[软件架构]]
- [[Tool Handler]]

## 参考资料

- [OpenAI: Harness Engineering](https://openai.com/zh-Hans-CN/index/harness-engineering/)
- Anthropic 博客：Harness 第二课
