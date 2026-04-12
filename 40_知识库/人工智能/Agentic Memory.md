---
area: "[[人工智能]]"
tags: [AI, Agent, Memory]
created: 2026-04-12
---
# Agentic Memory

## 定义

Agentic Memory 是一种将记忆操作彻底**工具化**的 Agent 记忆架构，让模型像控制手臂一样主动控制记忆的读写与更新，而非被动接收上下文。它本质上是一个独立的 System 2 系统，拥有主动控制的回路。

## 要点

- Memory 的最小闭包是 **(Ledger, Views, Policy)** 三件套
  - **Raw Ledger**：追加式权威记录（event 序列）
  - **Derived Views**：派生的检索索引（向量、KG、timeline 等）
  - **Policy**：控制何时读/写/更新/遗忘的策略层
- 记忆能力与 LLM 通用 Agent 能力**相对正交**，可独立优化
- 非参数化 Memory 的上限由接口带宽、检索误差、Policy 可学习性三类瓶颈决定
- 时序是架构的结构维度，需要 bi-temporal 建模（valid_time + transaction_time）

## 示例

- **AgeMem**：通过 RL 训练让 LLM 学会 ADD/UPDATE/FILTER/SUMMARY 等记忆工具
- **ProcMEM**：将成功轨迹固化为 Skill-MDP，实现程序性记忆的可执行复用
- **Farzapedia**：用个人维基作为 Agent 的外部记忆，Claude Code 通过文件系统导航检索

## 相关概念

- [[AI Agent]]
- [[RAG]]
- [[知识图谱]]
- [[知识工程]]

## 参考资料

- [Memory Architecture Deep Dive](https://www.bestblogs.dev/en/article/0c853462)
- AgeMem、InfMem、SimpleMem、ProcMEM、JitRL 等论文
