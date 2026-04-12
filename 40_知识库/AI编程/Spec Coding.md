---
area: "[[AI编程]]"
tags: [AI, 方法论, Spec-Coding]
created: 2026-04-12
---
# Spec Coding

## 定义

Spec Coding 是一种 AI 编程方法论：在让 AI 写代码之前，先用结构化文档（Spec）把"要做什么、怎么做、有什么约束"说清楚，然后 AI 围绕这份文档编码。核心理念是 **"Code is Cheap, Context is Expensive"**。

## 要点

- 三条铁律：**No Spec, No Code**（没有文档不准写代码）、**Spec is Truth**（文档优先于代码）、**Reverse Sync**（发现偏差先修文档再修代码）
- 渐进式复杂度：简单需求不承担复杂流程的成本，流程是可选增强而非强制前提
- 标准工作流：**Propose → Apply → Review → Archive**
- 人的角色从"全干"变成"管和验"：管控（控制 AI 看什么）、指挥（选方案、审计划）、评价（验收结果）
- 知识底座（领域知识积累）才是真正的护城河，而非 Prompt 或 Rules

## 示例

- 阿里团队的 code_copilot 框架：rules/ + knowledge/ + changes/ 三目录结构
- OpenSpec 的 /propose → /apply → /archive 三步工作流
- 编排层（强模型做决策）+ 执行层（编码模型写代码）的两层 AI 架构

## 相关概念

- [[Agentic Engineering]]
- [[Vibe Coding]]
- [[Harness Engineering]]
- [[Claude Code]]

## 参考资料

- 阿里妹技术分享：渐进式 Spec Coding 实践
- OpenSpec + CodeBuddy 团队实录
