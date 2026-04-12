---
title: "Claude Code 工程实践"
type: project
created: 2026-03-26
status: active
area: "[[AI编程]]"
due:
priority: P2
tags: [project, AI编程, Claude-Code, 工程实践, 上下文工程]
---
# Claude Code 工程实践

## 背景

**痛点:**
- 大多数人把 Claude Code 当 ChatBot 用，上下文越来越乱
- 工具越多效果越差、规则越写越长却越不遵守
- 缺乏对 Claude Code 六层架构的系统理解和工程化治理

**解决方案:**
系统掌握 Claude Code 的六层架构（上下文工程、Skills 设计、工具设计、Hooks、Subagents、验证闭环），建立可复用的工程化配置实践，从"会用 Claude Code"进化到"能治理 Claude Code"。

**重要性:**
- 原文来自 Tw93 半年深度使用的实战经验，覆盖了从底层运行机制到上层工程实践的完整知识体系
- 每一节都有具体的配置示例、反模式警告和最佳实践
- 与 vault 中已有的 [[AI编程方法论]] 研究互补：方法论偏"认知层"（怎么想），本项目偏"工程层"（怎么做）
- 直接服务于 OrbitOS 自身的 Claude Code 配置优化

---

## 行动

### 阶段1: 知识提取与结构化（1 周）
从收件箱原文提取核心知识点，创建原子化知识卡片。

- [ ] 提取并创建知识卡片到 `40_知识库/AI编程/`：
  - [ ] [[Claude Code 代理循环]]（第1节：收集上下文 → 行动 → 验证 → 循环）
  - [ ] [[Claude Code 概念边界]]（第2节：MCP / Plugin / Tools / Skills / Hooks / Subagents）
  - [ ] [[上下文工程实践]]（第3节：200K 分解、分层加载、压缩陷阱、Compact Instructions）
  - [ ] [[Skills 设计模式]]（第4节：三种类型——检查清单、工作流、领域专家；反模式）
  - [ ] [[Agent 工具设计原则]]（第5节：好工具 vs 坏工具、AskUserQuestion 演进）
  - [ ] [[Hooks 工程实践]]（第6节：PostToolUse、Notification、三层叠加）
  - [ ] [[Subagents 使用指南]]（第7节：隔离 vs 并行、权限约束、反模式）
  - [ ] [[Prompt Caching 架构]]（第8节：前缀匹配、缓存破坏陷阱、defer_loading）
  - [ ] [[验证闭环设计]]（第9节：Verifier 层级、Definition of Done）
  - [ ] [[CLAUDE.md 编写指南]]（第11节：应放/不应放什么、高质量模板）
- [ ] 创建研究笔记到 `30_研究/AI编程/Claude-Code工程实践/`，整合以上知识点
- [ ] 更新 [[AI编程方法论]] 研究笔记，添加本项目的交叉引用

### 阶段2: 实践应用与配置优化（1-2 周）
将知识应用到 OrbitOS vault 自身的 Claude Code 配置。

- [ ] 审计当前 OrbitOS 的 CLAUDE.md，对照第11节模板优化
- [ ] 评估现有 Skills 配置
- [ ] 配置 Hooks
- [ ] 运行 `/health` 健康检查
- [ ] 记录优化前后的体感差异

### 阶段3: 总结沉淀与分享（1 周）
将实践经验沉淀为可复用的知识资产。

- [ ] 整理 Claude Code 工程化配置最佳实践清单
- [ ] 创建"Claude Code 工程化布局参考"
- [ ] 更新 [[Vibe-Coding-学习]] 项目，添加"工程化治理"阶段
- [ ] 编写项目总结到进展日志

---

## 进展

### 2026-03-26
- 项目启动，从收件箱 [[你不知道的 Claude Code：架构、治理与工程实践]] 创建项目
- 原文来自 @HiTw93（Tw93）：https://x.com/HiTw93/status/2032091246588518683
- 制定三阶段学习计划，预计 3-4 周完成
- 下一步：开始阶段1知识提取

---

## 成功指标

- [ ] 从原文 15 节内容中提取 ≥10 张原子化知识卡片
- [ ] OrbitOS 的 CLAUDE.md 通过 `/health` 检查无严重问题
- [ ] Skills 描述符总 token 消耗降低 ≥30%
- [ ] 配置至少 2 个 PostToolUse Hooks 并验证有效
- [ ] 建立个人 Claude Code 工程化配置模板，可复用到其他项目

---

## 相关

- 综合研究: [[AI编程方法论]]
- 关联项目: [[Vibe-Coding-学习]]
- 架构参考: [[learn-claude-code架构拆解]]
- Skills 战略: [[Anthropic的战略转向]]
- 可观测性: [[Claude Code可观测性实践]]
- 多智能体编排: [[oh-my-claudecode多智能体编排]]
- 认知框架: [[从Vibe Coding到Agentic Engineering]]
- 原文链接: https://x.com/HiTw93/status/2032091246588518683
- 领域: [[AI编程]]
