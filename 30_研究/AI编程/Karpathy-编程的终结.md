---
title: "Karpathy：编程的终结"
type: research
created: 2026-03-26
tags: [研究, AI编程, Karpathy, Agent, AutoResearch, 未来预测]
---
# Karpathy：编程的终结

Andrej Karpathy 在 No Priors 播客中深度讨论了 AI Agent、AutoResearch、编程未来等话题。以下为核心观点提炼。

## 核心观点

**"编程（code）已经不是正确的动词了。我现在每天 16 小时向 Agent 表达意志。"**

自 2024 年 12 月起，Karpathy 从 80% 自己写代码 / 20% 委托 Agent，翻转为几乎 100% 委托 Agent。他称之为 "AI 精神症"（AI Psychosis）——一种持续探索无限可能性带来的焦虑与兴奋。

## 关键洞察

### 1. Agent 使用的新范式
- **宏操作（Macro Actions）**：不再是写一行代码或一个函数，而是委派完整功能给不同 Agent
- **并行化**：像 Peter Steinberg 那样同时管理多个 Agent，在多个 repo 之间切换分配任务
- **Token 吞吐量**：关键瓶颈已从 GPU 算力转向"你能驱动多少 token 吞吐量"
- **一切都是 Skill Issue**：当 Agent 做不好时，往往是指令不够好，而非能力不足

### 2. AutoResearch 方法论
- **核心理念**：把自己从循环中移除，最大化 token 吞吐量
- **实际效果**：在已经手动调优两周的 GPT-2 训练代码上，AutoResearch 一夜之间找到了 Karpathy 遗漏的优化（weight decay、Adam betas 的联合调优）
- **适用条件**：任何有客观可评估指标的任务都适用；无法评估的就无法 AutoResearch
- **Program.md**：用 Markdown 描述研究组织的运作方式，可以像代码一样被优化

### 3. 开放式协作研究（AutoResearch at Home）
- 类似 Folding@Home 的分布式模式：不可信的工作节点 + 可信的验证节点
- "找到好的 commit 很难，但验证一个 commit 是否有效很容易"
- 全球分布式算力可能超越 Frontier Labs 的集中算力
- 个人可以购买算力贡献给关心的研究方向（如某种癌症研究）

### 4. Agent 的"锯齿性"（Jaggedness）
- 同时像极其出色的 PhD 系统程序员和 10 岁小孩
- 在 RL 训练覆盖的领域（可验证任务）表现极强
- 在软性领域（理解意图、何时提问、幽默感）表现很弱
- "你要么在超级智能的轨道上，要么在轨道外，一切开始漫无目的"

### 5. 未来预测
- **数字空间先行**：比特比原子容易百万倍，数字空间将先经历巨大重构
- **物理世界滞后**：机器人/自动驾驶等原子操作会滞后，但市场更大
- **软件需求增长**：Jevons 悖论——软件变便宜后需求反而增加（类比 ATM 与银行柜员）
- **开源与闭源共存**：开源落后闭源约 6-8 个月，这种格局健康且会持续

### 6. 教育变革
- **不再直接教人，而是教 Agent**：Agent 理解后可以个性化教学
- **从 HTML 文档到 Markdown 文档**：面向 Agent 的文档取代面向人类的文档
- **Skills 即课程**：用 Skill 脚本化教学路径，让 Agent 引导学习
- **MicroGPT**：200 行 Python 浓缩 LLM 训练本质，Agent 能理解但创造不出来
- **"Agent 做不到的事才是你的工作"**

### 7. Claw（持久化 Agent）
- 比单次 Agent 会话更进一步的持久化实体
- 拥有独立沙箱、持续循环、更复杂的记忆系统
- Karpathy 的 "Dobby the Elf" 管理整个智能家居（Sonos、灯光、HVAC、泳池、安防摄像头）
- 六个 App 被一个 WhatsApp 自然语言接口取代

## 与现有知识的关联
- [[AI编程方法论]] - AutoResearch 是核心方法论的具体实践
- [[Claude-Code-工程实践]] - Agent 并行化工作流的参考
- [[Autoresearch 迭代方法论实践]] - AutoResearch 框架的通俗化应用

## 来源
- 原文: [The End of Coding: Andrej Karpathy on Agents, AutoResearch, and the Loopy Era of AI](https://www.youtube.com/watch?v=kwSVtQ7dziU)
