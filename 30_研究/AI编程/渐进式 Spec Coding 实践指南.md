---
area: "[[AI编程]]"
tags: [AI, Spec-Coding, 工作流, 阿里]
created: 2026-04-12
source: "[[A Practical Guide to 'Progressive Spec' for AI Coding in ....md]]"
---
# 渐进式 Spec Coding 实践指南

## 核心理念

> **Code is Cheap, Context is Expensive**

在让 AI 写代码之前，先用结构化文档（Spec）把"要做什么、怎么做、有什么约束"说清楚，然后 AI 围绕这份文档编码。

## Spec Coding 三条铁律

1. **No Spec, No Code** — 没有文档，不准写代码
2. **Spec is Truth** — 文档和代码冲突时，错的一定是代码
3. **Reverse Sync** — 发现偏差，先修文档，再修代码

## 渐进式复杂度（核心差异化）

不同复杂度的需求，暴露不同深度的流程：
- **简单需求**（改字段、修 Bug）：只用 Rules，不需要写 Spec
- **中等需求**：Rules + 轻量 Spec
- **复杂需求**：完整 Spec + Tasks + Review

> 简单需求不承担复杂流程的成本，流程是可选增强而非强制前提

## 工作流：Propose → Apply → Review → Archive

| 阶段 | 主导方 | 核心活动 |
|------|--------|---------|
| **Propose** | 人主导，AI 辅助 | Research → 逐个提问 → 分段生成 Spec → HARD-GATE 确认 |
| **Apply** | AI 主导，人审查 | 逐 Task 执行，展示验证证据，零偏差原则 |
| **Fix** | 增量修正 | Review 后的增量修正 + 文档同步铁律 |
| **Review** | Sub Agent | 两阶段：Spec Compliance → Code Quality |
| **Archive** | 知识沉淀 | 展示 log.md 发现，确认后沉淀到 knowledge/ |

## 编排层 + 执行层的两层 AI 架构

| 层 | 擅长 | 模型选择 |
|----|------|---------|
| 编排层 | 理解模糊需求、生成 Spec、审查决策 | 强模型（Claude Opus） |
| 执行层 | 读写代码、执行命令、快速迭代 | 编码优化模型（Sonnet） |

## 自由度曲线

| 阶段 | 自由度 | 原因 |
|------|--------|------|
| 调研 | 中 | 让 AI 自由探索，但必须给证据 |
| 方案设计 | 高 | 唯一鼓励 AI 充分想象的阶段 |
| 规划 | 低 | 精确到文件路径和函数签名 |
| 执行 | 零 | 严格按计划施工 |
| 验收 | 中 | 自由检查，结论要有依据 |

## 知识底座才是护城河

> AI 编码工具会越来越同质化，团队之间的差距不在于用什么工具，而在于积累了多少高质量的、结构化的领域知识。

## 相关概念

- [[Agentic Engineering]]
- [[Harness Engineering]]
- [[Claude Code]]
- [[Vibe Coding]]
