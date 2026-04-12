---
area: "[[AI编程]]"
tags: [AI, Agent, Memory, 个人维基, 知识管理]
created: 2026-04-12
source: "[[The 'File over App' Philosophy for AI Agent Memory.md]]"
---
# File over App：AI Agent 记忆的个人维基实践

## 背景

Andrej Karpathy 推荐了 Farza 的 **Farzapedia** 项目——一个用 LLM 从日记、Apple Notes、iMessage 中提取 2,500 条条目，生成 400 篇详细文章的个人维基。

## 核心理念："File over App" 哲学

个人维基作为 Agent 记忆系统，相比传统的"AI 越用越聪明"模式有四大优势：

### 1. 显式化（Explicit）
- 记忆工件是**显式且可导航的**（维基本身）
- 你可以清楚地看到 AI 知道什么、不知道什么
- 知识不是隐式的、未知的，而是可检查和管理的

### 2. 数据归你所有（Ownership）
- 数据存储在本地计算机，不在 AI 提供商的系统中
- 你完全掌控自己的信息

### 3. 文件优于应用（File over App）
- 以通用格式（Markdown、图像）存储
- 数据具有互操作性：可用任何工具/CLI 处理
- Agent 可以原生读取和理解文件
- 可用 [[Obsidian]] 等工具查看，或自定义查看器

### 4. 自带 AI（BYOAI）
- 可使用任何 AI（Claude、Codex、OpenCode 等）接入
- 甚至可以用开源 AI 在维基上微调

## Farzapedia 工作方式

1. LLM 提取个人数据源中的条目
2. 生成带 **反向链接（backlinks）** 的结构化文章
3. Agent 从 `index.md`（目录）开始，按需钻取到具体页面
4. 新内容加入时，系统自动更新 2-3 篇相关文章或创建新文章

## 为什么比 RAG 更好

Farza 一年前用 [[RAG]] 构建过类似系统，效果不好。原因：
> "一个能让 Agent 通过文件系统找到所需内容的知识库，效果就是更好。"

文件系统的结构化导航 > 向量相似度检索。

## 与 OrbitOS 的关联

OrbitOS 的设计理念与 File over App 高度一致：
- 使用 [[Obsidian]] + Markdown 作为通用格式
- Wikilinks 实现知识互联
- Agent（Claude Code）可原生读取和操作 vault

## 相关概念

- [[Agentic Memory]]
- [[RAG]]
- [[Obsidian]]
- [[知识工程]]
