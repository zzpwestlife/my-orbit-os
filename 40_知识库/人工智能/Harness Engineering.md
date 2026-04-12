---
area: "[[人工智能]]"
tags: [AI, Agent, Harness, 工程化]
created: 2026-04-12
---
# Harness Engineering

## 定义

Harness Engineering 是一套将 AI 的"智能"转化为可靠、可控、可规模化"生产力"的工程哲学与实践框架。Harness = 除了 LLM 本身之外，让 Agent 真正能干活的一切**基础设施**。

核心隐喻："马与缰绳"——不是改变马的基因（模型本身），而是设计一套专业的马具和训练方法。

## 要点

- 本质是一个带边界控制的 **REPL 容器**（Read-Eval-Print Loop），包裹在 LLM 之外
- 核心目标遵循 **R.E.S.T 模型**：可靠性、效率、安全性、可观测性
- 六大设计原则：为失败而设计、契约优先、默认安全、决策与执行分离、万物皆可度量、数据驱动进化
- 架构分为**控制平面**（决定做什么）和**数据平面**（如何去做）
- 随着模型能力提升，Harness 需要持续做减法——定期评估每个组件是否还必要

## 示例

- Claude Code 的 `edit` 工具：从 bash 中提出来做成独立工具，支持 staleness check
- Sprint + context reset：为 Opus 4.5 的"上下文焦虑"设计，Opus 4.6 后被砍掉
- Skills 机制：YAML frontmatter 预加载概览，完整内容按需展开

## 相关概念

- [[Agentic Engineering]]
- [[AI Agent]]
- [[Claude Code]]
- [[Agentic Memory]]

## 参考资料

- [Anthropic Harness Engineering Blog](https://www.anthropic.com)
- [OpenAI Harness Engineering Report](https://openai.com/zh-Hans-CN/index/harness-engineering/)
