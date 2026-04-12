---
area: "[[AI编程]]"
tags: [AI, AI-Native, OpenSpec, 团队实践, 0-Coding]
created: 2026-04-12
source: "[[When the Entire Team Goes Zero-Manual Coding A 10,000-Wo....md]]"
---
# 团队 Zero-Manual Coding 落地实录

## 核心转变

从"辅助编码"到"0 人工 Coding"的 AI Native 研发模式：
> 把 AI 当打字员用，天花板很低。把 AI 当施工队用，才有真正的效率革命。

## 四大痛点

| 痛点 | 根因 |
|------|------|
| 人机协作无标准 | 没有统一的 AI 交互规范 |
| 流程断点 | 设计工具和编码工具之间数据隔离 |
| 上下文缺失 | AI 无法主动读取项目代码库和技术规范 |
| 文档脱节 | 文档和代码不在同一个版本控制系统 |

## OpenSpec 三步核心工作流

1. **`/propose`** — 先想清楚，再动手（生成 proposal.md + design.md + tasks.md）
2. **`/apply`** — 让 AI 按图施工（读取 tasks 逐步执行，每完成一项自动打钩）
3. **`/archive`** — 让规范活起来（规范增量合并到主目录，文档永远与代码同步）

## 三大武器库

| 机制 | 作用 | 效果 |
|------|------|------|
| **知识库** | 让 AI "知道"项目 | specs/ 活文档 + MCP 外部知识 |
| **MCP** | 让 AI "连接"工具 | 直接读 TAPD 需求、iWiki 文档 |
| **Skills** | 让 AI "掌握"方法 | 标准化 SOP 封装为可复用技能包 |

## openspec-installer 关键设计

- **Bridge Rule**：解决"AI 不知道要读 config.yaml"的链路断裂问题
- **Token 交互**：在 SKILL.md 指令层完成（非 TTY 环境无法用 `read -p`）
- **三级降级策略**：MCP 查询 → 本地读取 → 静默跳过（辅助功能不阻塞核心功能）

## 角色重新定义

> 人的核心角色只有三个：**决策、审批、把关**。其他的，让 AI 去干。

## 相关概念

- [[Agentic Engineering]]
- [[Harness Engineering]]
- [[Spec Coding]]
- [[Claude Skills]]
