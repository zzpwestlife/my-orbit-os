---
created: 2026-04-21
type: reference
area: "[[AI编程]]"
tags: [status/refactored, Skill, 迭代优化, 自动化, Darwin]
sources:
  - "[[达尔文.skill 正式发布，一个无限进化的 skill 系统！]]"
---
# Darwin Skill 自进化系统

## 概述

达尔文.skill 是将 [[Autoresearch 方法论]] 的**棘轮迭代机制**迁移到 Skill 质量优化领域的系统。

核心逻辑：**随机变异 → 评估 → 保留改进 → 回滚退步** → 时间换质量。

> 女娲.skill 解决「从 0 到 1」（创建新 Skill）  
> 达尔文.skill 解决「从 1 到 N」（批量提升所有 Skill 质量）

## 与 Autoresearch 的映射关系

| Autoresearch | Darwin.skill |
|---|---|
| 训练代码 | SKILL.md 文件 |
| Loss 数值 | 8 维度加权总分 |
| Git commit | 优化 commit |
| Git revert | 质量回滚 |
| 全自主 | + Human in the Loop |

**关键新增**：Skill 质量无法纯粹用数字自动判断，加入了"人在回路"检查点。

## 8 维度评分体系（100分制）

### 结构维度（60分）

| 维度 | 分值 | 说明 |
|------|------|------|
| Frontmatter 规范性 | 8 | 字段是否完整规范 |
| 工作流步骤清晰度 | 15 | 流程是否可执行 |
| 异常处理 | 10 | 边界条件是否覆盖 |
| 用户确认检查点 | 7 | 关键决策前是否确认 |
| 指令具体性 | 15 | 是否可直接执行 |
| 引用文件有效性 | 5 | 路径是否真实存在 |

### 效果维度（40分）

| 维度 | 分值 | 说明 |
|------|------|------|
| 架构合理性 | 15 | 整体设计是否优秀 |
| **实测表现** | **25** | 真实 prompt 跑出的输出质量 |

> 实测权重最高（25分）：一个结构满分但跑出来差的 Skill，不如一个写得粗糙但实际好用的 Skill。

## 五条核心原则

1. **单一可编辑资产**：每次只改一个 SKILL.md，避免混合改动无法归因
2. **双重评估**：结构评分看"写得对不对"，实测评分看"用起来好不好"
3. **棘轮机制**：改后分数降低立即 git revert，有效基线只增不减
4. **独立评分**：改 Skill 的 Agent ≠ 评分的 Agent（参考安然审计独立性）
5. **人在回路**：机器做初筛，人做终审——每阶段都有人工确认检查点

## 优化循环（5个阶段）

```
Phase 0: 初始化环境
Phase 1: 为每个 Skill 设计测试 Prompt + 建立基线分数
Phase 2: [核心循环] 找最低分维度 → 改一处 → 独立 Agent 重新打分 → 保留/回滚（最多3轮/Skill）
Phase 3: 汇总 Before/After 分数表
[每阶段间均有人类确认检查点]
```

## 与 skill-creator 的区别

| | skill-creator | Darwin.skill |
|---|---|---|
| 定位 | 创建单个 Skill | 批量管理所有 Skill 质量 |
| 模式 | 人机一对一协作 | 自主批量 + 人工审核 |
| 适用 | 从零新建 | 已有大量 Skill 后 |

二者互补：女娲/skill-creator 出厂，达尔文做质检。（事实上女娲.skill Phase 5 已内嵌达尔文的8维度评估体系）

## 安装

```bash
npx skills add alchaincyf/darwin-skill
```

说「优化所有 skills」或「优化某个 skill」触发运行。

## 相关概念

- [[Autoresearch 方法论]] — 方法论来源，Karpathy 的棘轮迭代思想
- [[Claude Code]] — 运行环境
- [[Skill注入]] — Skill 在 Agent 中的使用方式
- [[Skill Hub]] — Skill 可视化管理工具
