---
area: "[[AI编程]]"
tags: [Skill, 迭代优化, 自动化, 棘轮机制]
created: 2026-04-21
---
# Darwin Skill

## 定义

达尔文.skill 是一个将 [[Autoresearch 方法论]] 的棘轮迭代机制应用于 [[Claude Code]] Skill 质量优化的自进化系统。它能批量评估、改进并验证 Skill 质量，只保留有效改进。

**类比**：女娲造人（skill-creator 创建 Skill），达尔文进化（darwin-skill 持续优化所有 Skill）。

## 要点

- **8 维度评分**：结构 60 分（Frontmatter、工作流、异常处理、检查点、指令具体性、路径有效性）+ 效果 40 分（架构合理性 + 实测表现）
- **实测权重最高（25/100分）**：结构满分但跑出来差的 Skill，价值不如结构粗糙但实际好用的
- **棘轮机制**：改后分数下降立即 git revert，基线只能向上
- **独立评分**：改 Skill 的 Agent ≠ 评分的 Agent（审计独立性原则）
- **Human in the Loop**：每个阶段都有人工确认检查点

## 示例

基线 72 → 第1轮 78（保留）→ 第2轮 75（回滚至78）→ 第3轮 87（保留）
净提升：72 → 87，中间失败不留痕迹。

## 相关概念

- [[Autoresearch 方法论]] — 核心思想来源
- [[Skill Hub]] — Skill 可视化管理工具
- [[Darwin Skill 自进化系统]] — 完整研究笔记

## 参考资料

- GitHub：https://github.com/alchaincyf/darwin-skill
- 安装：`npx skills add alchaincyf/darwin-skill`
