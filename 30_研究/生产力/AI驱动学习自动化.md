---
created: 2026-04-21
type: reference
area: "[[生产力]]"
tags: [status/refactored, AI学习, 知识管理, 自动化闭环, 工具链]
sources:
  - "[[拥抱 AI 这一年：我的工具、实践和思考]]"
---
# AI 驱动学习自动化

## 核心理念

> 既然我学习不过来了，那 Agent 帮我学习吧。既然我应用得比较慢，Agent 帮我应用。

AI 时代的根本问题：技术迭代速度已超越个人学习能力上限。解法：**让 Agent 替代你站在信息采集第一线，你只审阅提炼后的精华版。**

## 三层架构：采集 → 提炼 → 应用

### 采集层

| Skill | 功能 |
|-------|------|
| `ai-news` | 11+ 并行源（HN/HF/GitHub/Reddit/36Kr/量子位等），评分 ≥4 分入选，自动去重 |
| `podcast-batch` | 批量转录 + 分析近期播客，腾讯 ASR 10h/月免费 |
| `web-collect` | 指定网页/站点采集整理 |
| `research` | 深度调研指定主题，多源交叉验证 |

### 提炼层

| Skill | 功能 |
|-------|------|
| `ai-practices` | 全自动提取可复用 AI 最佳实践，严格准入（需 URL + ≥50 字 + 可复用），子 Agent 生成避免同质化 |

### 应用层

| Skill | 功能 |
|-------|------|
| `workspace-evolve` | 审计工作空间配置（CLAUDE.md/rules/skills/settings），对比官方+社区最佳实践，输出优化报告并实施 |
| `doc-writer` | 撰写结构化文档 |
| `podcast-script` | 素材 → 播客对话脚本 → 音频合成（豆包中文语音 + Coze工作流） |
| `tool-builder` | 构建实用工具/脚本 |
| `create-shortcut` | 生成 macOS 快捷指令 |

### 闭环机制

```
外部信息 → 采集层 Agent → 提炼层 Agent → 最佳实践库
                                              ↓
                              workspace-evolve 反哺到工作空间配置
                                              ↓
                              下次 Agent 执行任务时已内化最新实践
```

## AI 编程范式演进路径

```
Prompt Engineering
    ↓（单轮对话 prompt 优化）
Context Engineering
    ↓（管理 Agent 看到的一切信息）
Spec-driven Development (SDD)
    ↓（先写契约，再让 Agent 动手）
Harness Engineering
    ↓（构建约束体系，对抗熵增）
```

关键洞察：**每一阶段都在解决上一阶段的核心痛点。**

## Mac 工具链（AI 时代适配）

| 工具 | 性质 | 核心能力 |
|------|------|----------|
| AeroSpace | 开源 | 窗口自动分屏、工作区管理、应用自动归位 |
| Raycast | 免费 | 应用快捷键启动、剪贴板历史 |
| Ghostty | 开源 | 命令行客户端 |
| Yazi | 开源 | TUI 三栏文件浏览器 |
| lazygit | 开源 | 命令行 Git 操作 |
| fzf | 开源 | 历史命令/文件/目录搜索 |
| tmux | 开源 | 远程终端复用、会话持久化 |
| Cockpit（自研）| 自研 | 跨机器 Agent 任务状态仪表盘 |

> 背景：多 Agent 并行任务时，需要即时关注各 Agent 状态，避免因等待审核/报错而长时间闲置。

## 核心态度

> 与其追求「深入理解每一个东西」，不如追求「快速沉淀和验证每一个有价值的东西」。

AI 时代高效学习的核心转变：
- **过去**：我要先学会它，然后再用它
- **现在**：Agent 帮我学，帮我用；我审阅、判断、迭代

## 相关概念

- [[Harness Engineering]] — AI 工程体系的当前最佳实践
- [[Spec-driven Development]] — 意图驱动的开发范式
- [[Claude Code]] — 核心 Agent 工具
- [[Autoresearch 方法论]] — 知识提炼的自动迭代思想
