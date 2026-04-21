---
created: 2026-04-21
type: reference
area: "[[AI工作流]]"
tags: [status/refactored, Obsidian, ClaudeCode, 第二大脑, 工作流]
sources:
  - "[[Claude Code + Obsidian 打造第二大脑]]"
---
# Claude Code + Obsidian 工作流实践

## 核心理念

Obsidian（Markdown 文件系统）+ Claude Code（CLI Agent）= 会思考的知识库

**Obsidian 是 AI 缺失的一环**：文件系统是完美的记忆载体——结构化、可引用、离线优先。Claude Code 赋予这些文件"被 Agent 主动读取和操作"的能力。

## 协同效应

- **Obsidian CLI**：让 Claude Code 能读取 Obsidian 的文件及其双向链接关系
- **图谱视图**：发现思维中隐藏的模式（你自己也未意识到的关联）
- **上下文传递**：笔记就是高质量上下文，直接传给 Agent 避免重复描述

## 核心命令模式

### 日常工作流命令

| 命令 | 功能 |
|------|------|
| `/context` | 加载完整生活上下文（项目、目标、关系等） |
| `/today` | 晨间回顾 + 优先级规划 |
| `/close-day` | 日终处理、回顾与捕获 |

### 反思与分析命令

| 命令 | 功能 |
|------|------|
| 幽灵提问 | 以用户自身风格回答问题（基于笔记模拟思维） |
| 信念压力测试 | 挑战当前观点，找出盲点 |
| 领域融合 | 从分散笔记中提取跨领域洞察 |
| 意图偏离 | 比较声明意图与实际行为的差距 |

### 知识发现命令

| 命令 | 功能 |
|------|------|
| `/trace` | 追踪一个想法/观点在所有笔记中的演变历程 |
| `/connect` | 连接两个看似不相关的领域，寻找概念桥梁 |
| `/graduate` | 扫描日记/日志，将值得升级的创意提取为正式笔记 |
| `/ideas-demo` | 基于完整知识库的创意分析 + 可执行建议 |

## 与 OrbitOS 的关联

这套工作流与 OrbitOS 高度契合：
- **`/today`** → 对应 OrbitOS 的 `/start-my-day`
- **`/context`** → 对应 CLAUDE.md 中的项目上下文
- **`/trace`** → 可用于追踪 OrbitOS 中某个项目/概念的演变
- **`/graduate`** → 类似 OrbitOS 的 `/kickoff`（日志条目升级为项目）

## 关键哲学

> **写作不只是输出，也是 Agent 上下文。** 你写给自己的笔记，同时也是 AI 伴侣理解你的训练数据。

> **文件即记忆。** Markdown 文件比任何专有数据库都更耐久、更可移植、更透明。

> **未来趋势**：不是管理 Agent，而是管理知识库——知识库的质量决定 Agent 的能力上限。

## 一个原则

**知识库仅包含人类思考**：只有你真实思考过、有主观判断的内容才进入知识库。AI 输出（会议总结、自动生成的内容）不直接存入——除非你审阅并标注了自己的判断。

## 相关概念

- [[Obsidian]] — 知识库工具
- [[Claude Code]] — CLI Agent 工具
- [[Harness Engineering]] — 构建 Agent 约束体系的思想
- [[File over App]] — 文件优于应用的哲学
