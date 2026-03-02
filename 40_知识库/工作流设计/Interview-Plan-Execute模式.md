---
area: [[AI工作流]]
tags: [workflow, ai, methodology]
created: 2026-03-03
---
# Interview-Plan-Execute 模式

## 定义

Interview-Plan-Execute（采访-计划-执行）是一种结构化的 AI 协作工作流程，要求 AI 在与用户达成充分共识之前不进入实施阶段。该模式借鉴了传统软件工程的最佳实践，强调"谋定而后动"。

## 要点

- **Interview（采访）**：使用 AskUserQuestion 等工具，全面理解用户需求、约束条件和背景
- **Plan（计划）**：基于采访结果制定详细方案，形成 design.md、todo.md 等文档
- **Execute（执行）**：严格按计划实施，减少偏离和返工
- **禁止脑补**：信息不足时强制追问，不自作主张

## 示例

1. **Interview 阶段**
   - "您想要什么类型的网站？"
   - "目标用户是谁？"
   - "有哪些必须的功能？"

2. **Plan 阶段**
   - 输出：design.md（设计文档）
   - 输出：todo.md（任务清单）
   - 用户确认后进入执行

3. **Execute 阶段**
   - 按计划编码
   - 阶段性交付
   - 基于已完成计划微调

## 优势

- 减少返工和方向偏离
- 提升用户满意度
- 保持 FlowState（零摩擦心流）
- 确保 design.md 和 todo.md 建立在坚实的事实基础上

## 相关概念

- [[Context Alignment]]
- [[Requirement Engineering]]
- [[FlowState]]
- [[Plan-First]]

## 参考资料

- Learn Claude Code 项目核心理念
