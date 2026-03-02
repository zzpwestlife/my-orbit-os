---
area: [[AI工作流]]
tags: [ai, communication, requirement]
created: 2026-03-03
---
# Context Alignment (上下文对齐)

## 定义

Context Alignment 是指在人机协作过程中，通过系统化的信息交换确保 AI 与用户在目标、约束条件、背景知识等方面达成一致的状态。它是高质量 AI 输出的前提条件。

## 要点

- **隐性需求显性化**：将用户未明确表达但期望的要素挖掘出来
- **双向确认**：AI 主动验证理解是否正确，而非假设
- **渐进式澄清**：通过多轮对话逐步完善上下文
- **文档化对齐**：将对齐结果固化为设计文档或计划文档

## 示例

- Interview 阶段：AskUserQuestion 工具强制进行需求澄清
- Plan 阶段：design.md 和 todo.md 记录已对齐的上下文
- Execute 阶段：基于已确认的计划执行，减少偏差

## 相关概念

- [[Interview-Plan-Execute模式]]
- [[Requirement Engineering]]
- [[FlowState]]

## 参考资料

- Learn Claude Code 项目实践
