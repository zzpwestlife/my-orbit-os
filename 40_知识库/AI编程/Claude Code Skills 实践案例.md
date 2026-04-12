---
title: "Claude Code Skills 实践案例"
type: wiki
created: 2026-03-26
tags: [知识卡片, AI编程, claude-code, skills, 工程实践]
related_project: "[[Claude-Code-工程实践]]"
---
# Claude Code Skills 实践案例

## 核心概念

Skills 是将个人工程经验编码为可复用流程模块的方式。真正的差距不在于谁用了更好的模型，而在于谁把自己的工程经验系统化成了 Agent 可执行的操作合约。

## 关键要点

### Matt Pocock 的 5 个开源 Agent Skills

Matt Pocock（TypeScript 圈知名工程师）将日常使用的 5 个 skill 全部开源，三天内获得 1.2k star：

1. **`/grill-me`** — 方案追问：在动手写代码之前，对方案发起连续追问，逼出每个决策分支。作者被问了 24 个问题，花了一小时写 PRD
2. **`/write-a-prd`** — 需求文档生成：通过互动访谈 + 代码库分析，生成完整需求文档，自动以 GitHub Issue 归档
3. **`/prd-to-issues`** — 任务拆分：将 PRD 按「垂直切片」拆成独立可认领的 Issue，开箱即用
4. **`/tdd`** — 测试驱动开发：经典红-绿-重构循环，每次做一个切片，强制先写测试再实现
5. **`/improve-my-codebase`** — 代码库改进：扫描代码库，找架构改进点，重点加深"浅层模块"和提升可测试性

### 核心洞察

- 会 prompt 的人很多，能把经验系统化的人很少
- Skill 就是把工程师的判断力和流程变成 Agent 可反复执行的操作合约
- 你写给 Agent 的 skill，就是你在这个时代留下的**工程资产**

## 实践指南

1. 从自己最常用的工作流程开始，识别可复用的模式
2. 将工程决策逻辑编码为 skill，而非只写 prompt
3. 采用"垂直切片"思维拆分任务，确保每个 skill 职责单一
4. 参考 Matt Pocock 的开源实现，学习 skill 的设计范式

## 来源

- 原文: [Thread by @chenchengpro](https://x.com/chenchengpro/status/2033855423623925869)
- 收件箱: [[Thread by @chenchengpro]]
