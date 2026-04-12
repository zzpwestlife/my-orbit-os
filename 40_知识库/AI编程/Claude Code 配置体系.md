---
title: "Claude Code 配置体系"
type: wiki
created: 2026-03-26
tags: [知识卡片, AI编程, claude-code, 配置, dotclaude]
related_project: "[[Claude-Code-工程实践]]"
---
# Claude Code 配置体系

## 核心概念

`.claude` 文件夹是 Claude Code 的控制中心，管理指令理解、命令权限、记忆和工作流。存在两个层级：**项目级** `.claude/`（团队共享，提交到 git）和**全局级** `~/.claude/`（个人偏好，本地状态）。

## 关键要点

### CLAUDE.md — 三层指令系统

| 层级 | 路径 | 作用 |
|------|------|------|
| 全局 | `~/.claude/CLAUDE.md` | 个人偏好，所有项目生效 |
| 项目 | `项目根目录/CLAUDE.md` | 团队指令，提交到 git |
| 子目录 | `子文件夹/CLAUDE.md` | 局部规则，特定目录生效 |

- `CLAUDE.local.md` 用于个人覆盖，不提交到 git
- 建议不超过 200 行，保持简短直接

### 核心配置组件

1. **`rules/`** — 模块化指令拆分
   - 规则按类别分文件（api-conventions.md、testing.md、security.md）
   - 支持 `paths` frontmatter 限定生效目录
2. **`commands/`** — 自定义斜杠命令
   - 文件名即命令名（review.md → `/project:review`）
   - 支持 `!` 反引号执行 shell 命令，结果注入 prompt
   - 支持 `$$ARGUMENTS` 参数传递
3. **`skills/`** — 自动触发的工作流
   - 每个 skill 独立子文件夹，包含 `SKILL.md` + 辅助文件
   - 任务匹配时自动调用，也可手动 `/skill-name` 触发
   - 与 commands 区别：commands 手动触发，skills 自动匹配
4. **`agents/`** — 后台专家子代理
   - `tools` 字段限制可用工具（最小权限原则）
   - `model` 字段选择模型（简单任务用 Haiku 省成本）
   - 后台执行，不刷屏主对话
5. **`settings.json`** — 权限控制
   - `allow` 列表：无需确认的操作
   - `deny` 列表：禁止执行的操作
   - `settings.local.json` 用于个人权限覆盖

### 完整目录结构

```
项目级 (.claude/)
├── CLAUDE.md              # 团队指令
├── CLAUDE.local.md        # 个人覆盖 (gitignored)
├── settings.json          # 团队权限
├── settings.local.json    # 个人权限 (gitignored)
├── rules/                 # 模块化指令
├── commands/              # 自定义命令
├── skills/                # 可复用工作流
└── agents/                # 专业子代理

全局级 (~/.claude/)
├── CLAUDE.md              # 全局偏好
├── projects/              # 会话历史和记忆
├── commands/              # 个人命令
├── skills/                # 个人 skills
└── agents/                # 个人 agents
```

## 实践指南 — 五步上手

1. **`/init` 生成起点** — 让 Claude 自动生成 CLAUDE.md，精简保留关键规则
2. **设置权限** — 创建 settings.json，允许项目命令，禁止读 .env
3. **做快捷命令** — 将高频操作（审查代码、修 bug）封装为 commands
4. **拆分规则** — CLAUDE.md 过长时拆到 rules/ 文件夹
5. **个人偏好** — 在 `~/.claude/CLAUDE.md` 写全局习惯

> 95% 的项目只需要这五步。Skills 和 agents 是有复杂重复工作时的高级功能。

## 来源

- 原文: [Claude Code 深度配置指南](https://x.com/imaxichuhai/status/2036044036772135279)
- 参考: [Akshay Pachaar 原始分享](https://x.com/akshay_pachaar/status/2035341800739877091)
- 收件箱: [[Claude Code 深度配置指南，90% 的人其实都不会用]]
