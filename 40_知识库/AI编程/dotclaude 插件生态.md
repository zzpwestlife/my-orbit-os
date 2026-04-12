---
title: "dotclaude 插件生态"
type: wiki
created: 2026-03-26
tags: [知识卡片, AI编程, claude-code, 插件, dotclaude]
related_project: "[[Claude-Code-工程实践]]"
---
# dotclaude 插件生态

## 核心概念

dotclaude 是 Claude Code 的插件生态系统，允许开发者通过 Plugin Marketplace 分享和安装 `.claude` 配置包，实现工程经验的模块化复用。

## 关键要点

### FradSer 的 superpowers 插件

- **组合方案**: superpowers + ralph-loop = `superpowers@frad-dotclaude`
- 实验发现 superpowers 与 ralph-loop 结合后效果显著提升
- 结合 agent team 支持，已接近完成品
- 开源地址: [github.com/FradSer/dotclaude](https://github.com/FradSer/dotclaude)

### 安装方式

通过 Claude Plugin Marketplace 安装：

```bash
claude plugin marketplace add FradSer/dotclaude
claude plugin install superpowers@frad-dotclaude
```

## 实践指南

1. 通过 `claude plugin marketplace` 浏览和安装社区插件
2. 关注 dotclaude 生态中的高星项目，获取优质配置
3. 将自己的 `.claude` 配置发布为插件，参与社区共建

## 来源

- 原文: [Thread by @FradSer](https://x.com/FradSer/status/2033990464781885947)
- 收件箱: [[Thread by @FradSer]]
