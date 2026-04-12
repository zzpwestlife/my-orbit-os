---
title: "Autoresearch 方法论"
type: wiki
created: 2026-03-26
tags: [知识卡片, AI编程, autoresearch, skills优化, 方法论]
related_project: "[[Claude-Code-工程实践]]"
---
# Autoresearch 方法论

## 核心概念

Autoresearch 是 Andrej Karpathy 提出的自动化迭代优化方法。核心思路：不让你手动改进，而是让 AI Agent 在循环中自动优化。试一个小改动 → 看结果 → 变好就留，没变好就撤 → 重复。任何能打分的东西，都能用这套方法。

## 关键要点

### Autoresearch 循环（改→测→留/撤）

1. **基准测试**: 运行当前 skill，用 checklist 打分，得到起始分数
2. **找薄弱项**: 定位得分最低的 checklist 项
3. **微调改动**: 针对薄弱项做一个小修改
4. **重新测试**: 用同一套 checklist 重新打分
5. **决策**: 分数升就保留改动，分数降就撤销
6. **循环**: 直到连续三次超过 95%，或手动停止

### Checklist 评分体系

- 用简单的**是/否问题**定义"什么叫好"
- **3-6 个问题**是最佳数量（超过 10 个会导致 skill 应付 checklist，输出反而更差）
- 每个问题检查输出的一个具体方面，通过或失败
- 示例：标题是否包含具体数字？CTA 是否说明下一步结果？是否存在零信息量词汇？

### 实际效果

- 落地页文案 skill 质量从 **56% → 92%**，4 轮改动，3 个保留 1 个撤销
- 网站速度优化：67 轮后从 1100ms 降至 67ms
- 全程零手动，Agent 自行在 autopilot 模式下完成

### 三种常见的 Skill 失效模式

1. **漂移失效**: prompt 未明确禁止的内容，模型输出逐渐变模糊、模板化
2. **选择性盲区**: 只看到"还不错"的输出，忽略悄悄失效的情况
3. **表面修复**: 手动改单次输出，但不改 skill 本身，问题反复出现

## 实践指南

1. 从表现最不稳定的 skill 开始（时好时坏的那个）
2. 定义 3-6 个是/否评分问题，切忌贪多
3. 在 Claude Code 中运行："对我的 [skill名称] skill 跑 autoresearch"
4. Agent 会引导你完成 checklist 定义，无需自己想问题
5. 跑完后保留 changelog —— 这是 skill 的"经验总结"，记录什么有用、什么没用
6. 规则：没跑过 autoresearch 的 skill，不拿出去用

## 来源

- 原文: [How to 10x your Claude Skills (using Karpathy's autoresearch method)](https://x.com/itsolelehmann/status/2033919415771713715)
- GitHub: [olelehmann100kMRR/autoresearch-skill](https://github.com/olelehmann100kMRR/autoresearch-skill)
- 收件箱: [[你搭的 Claude Skills，还能提升 10 倍效果 —— 使用 Karpathy 的 autoresearch 方法 【译】]]
