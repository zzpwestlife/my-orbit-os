---
created: 2026-03-06
type: reference
area: [[AI编程]]
tags: [status/refactored, Claude-Code, 多智能体, 工具]
source: https://mp.weixin.qq.com/s/tTdejZ-qH7G6Gi8wFeTHRw
---
# oh-my-claudecode 多智能体编排

## 概述

**oh-my-claudecode (OMC)** 是一个 [[Claude Code]] 多智能体编排插件，核心理念是让用户无需学习复杂的提示词技巧，直接用自然语言描述需求，系统自动完成任务拆分、分配和验证。

> **Don't learn Claude Code. Just use OMC.**

## 核心价值

### 解决的痛点

传统使用 Claude Code 的问题：
- 需要反复回答框架、数据库、接口等配置问题
- 任务执行过程需要人工监督和干预
- 做到一半就停止，缺乏持续执行能力

OMC 的解决方案：
- 自动任务拆分和分配
- [[多智能体协作]]并行执行
- 持续验证直到任务完成

## 架构设计

### 1. 专业化 Agent 团队

OMC 内置 **32 个专业化 Agent**，模拟完整研发团队：

| Agent 类型 | 职责 |
|-----------|------|
| `planner` | 制定实施计划 |
| `architect` | 系统架构设计 |
| `executor` | 代码实现 |
| `code-reviewer` | 代码审查 |
| `security-reviewer` | 安全漏洞检测 |
| `test-engineer` | 测试策略制定 |
| `debugger` | 问题根因分析 |
| `designer` | UI/UX 设计 |

每个 Agent 专注于自己擅长的领域，自动被分配到最合适的任务。

### 2. 核心编排模式

#### Team 模式（推荐）

采用流水线式协作：

```
team-plan → team-prd → team-exec → team-verify → team-fix (loop)
```

使用方法：
```bash
# 启动 3 个 executor agent 并行工作
/team 3:executor "fix all TypeScript errors"
```

**启用条件**：在 `~/.claude/settings.json` 中添加：
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

#### Ralph 模式（持久执行）

解决 AI 助手"做到一半就停"的问题：

```bash
ralph: refactor the authentication module
→ 执行 → 验证 → 发现问题 → 修复 → 再验证 → 完成
```

持续工作，自动验证完成度，发现问题自动修复，直到任务真正完成。

#### Autopilot 模式（全自动）

最简单的使用方式：

```bash
autopilot: build a todo app with React and Node.js
```

端到端自主执行，用户只需描述需求。

#### 其他模式

| 模式 | 用途 |
|------|------|
| **Ultrawork** | 最大并行度，快速批量修复 |
| **Pipeline** | 严格顺序的多步骤流程 |
| **CCG** | 三模型协作（Claude + Codex + Gemini） |

### 3. 多模型协作

从 v4.4.0 开始，OMC 支持在 tmux 中启动真实的 [[Codex]] 和 [[Gemini]] CLI 进程：

```bash
# 用 Codex 做代码审查
omc team 2:codex "review auth module for security issues"

# 用 Gemini 做 UI 设计
omc team 2:gemini "redesign UI components for accessibility"

# 查看团队状态
omc team status auth-review

# 关闭团队
omc team shutdown auth-review
```

**三大模型的最佳分工**：

| 模型 | 擅长领域 |
|------|---------|
| **Claude** | 通用编程、复杂推理 |
| **Codex** | 架构审查、安全分析 |
| **Gemini** | UI/UX 设计、大上下文任务 |

## 关键特性

### 1. 自动并行化

复杂任务自动拆分并行执行：
- 同时分析多个文件
- 并行修复不同模块
- 自动验证修复结果

### 2. 智能成本优化

智能选择模型以优化成本：
- **Haiku**：简单查询、快速检索（90% 能力，成本更低）
- **Sonnet**：标准实现任务
- **Opus**：复杂架构决策、深度分析

据称能节省 **30-50% 的 Token 消耗**。

### 3. 需求澄清

**Deep Interview** 模式：苏格拉底式需求澄清

```bash
/deep-interview "我想做个App"
```

帮助理清思路，暴露隐藏假设，确保需求明确。

## 快速上手

### 安装

```bash
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode
```

### 配置

```bash
/omc-setup
```

### 使用

```bash
autopilot: build a todo app with React and Node.js
```

## 实用场景

### 场景一：全栈功能开发

```bash
autopilot: implement user authentication with JWT, including login, register, and password reset
```

OMC 自动完成：
1. 规划功能模块
2. 设计数据库 schema
3. 实现后端 API
4. 编写前端组件
5. 添加单元测试
6. 安全审查

### 场景二：代码质量提升

```bash
ralph: fix all linting errors and improve code coverage to 80%
```

Ralph 模式会：
- 分析所有问题
- 逐个修复
- 运行测试验证
- 循环直到达标

### 场景三：三模型协作

```bash
/ccg Review this PR — architecture (Codex) and UI components (Gemini)
```

Claude 综合 Codex 的架构建议和 Gemini 的 UI 建议，给出最终方案。

## 进阶功能

### 通知集成

完成任务后自动通知：

```bash
# Telegram 通知
omc config-stop-callback telegram --enable --token <bot_token> --chat <chat_id>

# Discord 通知
omc config-stop-callback discord --enable --webhook <url>

# Slack 通知
omc config-stop-callback slack --enable --webhook <url>
```

### 成本监控

```bash
# 查看每日成本
omc cost daily

# 查看周成本
omc cost weekly

# 查看会话历史
omc sessions
```

## 魔法关键词速查

| 关键词 | 效果 | 示例 |
|--------|------|------|
| `team` | Team 编排 | `/team 3:executor "重构认证模块"` |
| `autopilot` | 全自动执行 | `autopilot: build a todo app` |
| `ralph` | 持久模式 | `ralph: refactor auth` |
| `ulw` | 最大并行 | `ulw fix all errors` |
| `ralplan` | 共识规划 | `ralplan this feature` |
| `deep-interview` | 需求澄清 | `/deep-interview "我想做个App"` |
| `ccg` | 三模型综合建议 | `/ccg review this PR` |
| `stopomc` | 停止当前模式 | `stopomc` |

## 适用场景

### 强烈推荐

- 需要频繁开发新功能的独立开发者
- 想提升代码质量但时间有限的团队
- AI 辅助编程的重度用户

### 成本考虑

- 需要 Claude Max / Pro 订阅或 API Key
- 多模型协作需要 Codex / Gemini CLI（可选）

**成本参考**：
- Claude Pro：$20/月
- 完整三模型：约 $60/月（Claude + Gemini + ChatGPT Pro）

## 相关概念

- [[Claude Code]]
- [[多智能体协作]]
- [[Agentic Engineering]]
- [[Codex]]
- [[Gemini]]

## 参考资料

- GitHub 仓库：https://github.com/Yeachan-Heo/oh-my-claudecode
- 官方文档：https://yeachan-heo.github.io/oh-my-claudecode-website
- CLI 参考：https://yeachan-heo.github.io/oh-my-claudecode-website/docs.html#cli-reference
