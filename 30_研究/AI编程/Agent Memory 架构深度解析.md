---
area: "[[AI编程]]"
tags: [AI, Agent, Memory, 架构]
created: 2026-04-12
source: "[[Deep Dive The Memory Architecture and Philosophy That Th....md]]"
---
# Agent Memory 架构深度解析

## 核心观点

Memory 不是简单的存储，而是一个**闭环系统**：Raw Ledger（权威记录）→ Views（可用能力）→ Policy（控制层）→ Commit（回写）→ Provenance（可回放）。

## 三大核心命题

### 命题 A：Memory 是可被决策利用的外部状态
Memory 的价值不在于"存了多少历史"，而在于**从历史到当前决策的通道**是否有效。它的输出要么进入上下文（证据/摘要/子图），要么直接参与决策（如对输出分布做调制）。

### 命题 B：最小闭包是 (Ledger, Views, Policy) 三件套
- **Raw Ledger**（权威记录）：追加式记录每次写入/更新/删除，像"账本/黑匣子"
- **Derived Views**（派生视图）：面向检索/推理的派生状态（向量索引、KG/TKG、timeline 等），像"缓存+索引+物化视图"
- **Policy**（控制层）：决定何时读、读多少、何时写、如何更新、如何遗忘，像"调度器/控制回路"

### 命题 C：基本单位是 event 序列
event 序列是"真相来源"，但它太底层。真正把历史变成能力的是 views（重组织/压缩/索引）和 policy（触发/更新策略）。

## System 1 + System 2 设计

- **System 1**：通用 LLM/Agent（推理、规划、工具调用）
- **System 2**：[[Agentic Memory]]（慢回路）—— 独立的记忆读写与检索系统，具备主动控制回路

记忆能力与 LLM 通用 Agent 能力**相对正交**，外置化的 System 2 带来可插拔、可迁移、可归因的工程好处。

## 非参数化 Memory 的上限

上限由三类瓶颈共同决定：

1. **接口带宽**：Memory → System 1 的注入容量（token 预算、注意力容量）
2. **检索与聚合误差**：Views 的近似误差（错检、漏检、时序冲突）
3. **Policy 可学习性**：何时写/读/忘的策略优化（往往最被低估）

## 时序记忆

时序不是 metadata，而是架构的**结构维度**：
- 采用 **bi-temporal**（valid_time + transaction_time）区分"世界真值"与"系统记账"
- 检索需 **time-sliced recall**，不能把旧事实当 current
- 遗忘分三层：validity gating（硬门控）→ tombstone（可审计抑制）→ decay（软信号）

## 程序性记忆（Procedural Memory）

[[ProcMEM]] 将交互历史形式化为 Skill-MDP，把成功的多步策略固化为可执行 skill：
- 三元结构：触发条件 + 执行步骤 + 终止条件
- 非参数化 PPO 验证：用环境回报而非语言自洽来评估技能
- 在线维护：基于评分剪枝过时技能，保持进化压力

## 架构五件套

| 模块 | 类比 | 职责 |
|------|------|------|
| 内核 | Kernel | 控制层/调度器，决定何时读写 |
| 文件系统 | Storage | Raw Ledger + Views，承载时序一致性 |
| 可执行文件 | Skill | 程序性记忆，可执行/可复用的技能单元 |
| 总线接口 | Context Bridge | Memory → LLM 的注入通道 |
| 学习引擎 | Online Adaptation | 持续将反馈转化为改进信号 |

## 关键论文

- **AgeMem**：Agentic Memory 的 RL 训练框架
- **InfMem**：PreThink-Retrieve-Write 协议与自适应早停
- **SimpleMem**：递归固化（Consolidation）机制
- **Zep/Graphiti**：时序知识图谱（TKG）
- **ProcMEM**：Skill-MDP 与非参数化 PPO
- **JitRL**：推理时用优势函数做 logits 加性调制
- **UMEM**：语义邻域级别的记忆迁移
- **MAGMA**：四正交图架构（语义、时间、因果、实体）
- **LycheeMemory**：潜层压缩与 KV-Cache 注入
- **MemAdapter**：异构记忆的对齐器

## 相关概念

- [[Agentic Memory]]
- [[RAG]]
- [[知识图谱]]
- [[Claude Code]]
