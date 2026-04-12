---
title: "md2wechat 公众号发布工具"
type: wiki
created: 2026-03-27
tags: [知识卡片, AI编程, Claude-Code, Skills, 公众号, 工具]
---
# md2wechat 公众号发布工具

开源 Skill，将 Markdown 自动排版并发送到微信公众号草稿，零成本实现从写作到发布的自动化流程。

## 核心价值

解决创作者的排版痛苦 —— 在 X/Twitter 上发的内容常被搬运，但自己排版发公众号又太麻烦。md2wechat 让 AI Agent 一句话完成：排版 + 上传图片 + 推送草稿。

## 安装方式

在任何支持 Skill 的 Agent 工具中执行：

```
请帮我安装 md2wechat 并验证可用。按这个顺序执行：
1. 运行：curl -fsSL https://github.com/geekjourneyx/md2wechat-skill/releases/download/v2.0.4/install.sh | bash
2. 运行：npx skills add https://github.com/geekjourneyx/md2wechat-skill --skill md2wechat
3. 运行：export PATH="$HOME/.local/bin:$PATH"
4. 运行：md2wechat version --json
5. 运行：md2wechat config init
6. 运行：md2wechat capabilities --json
```

## 配置微信密钥

需要从[微信开发者平台](https://developers.weixin.qq.com/platform)获取两个密钥：
- **WECHAT_APPID**
- **WECHAT_SECRET**

配置方式：告诉 AI `WECHAT_APPID：xxx，WECHAT_SECRET：xx，帮我配置一下`，自动完成。

## 发布流程

使用命令：`使用 AI 模式 html，上传图片后，更新图片地址，发布到草稿`

两种模式：
- **AI 模式（免费）**：本地排版 + html 生成，零成本
- **API 模式（付费）**：调用作者提供的 API 服务

发布后进入公众号后台，改标题、改封面即可发布。

## 关键信息

- **GitHub**: [geekjourneyx/md2wechat-skill](https://github.com/geekjourneyx/md2wechat-skill)
- **作者**: [@lxfater](https://x.com/lxfater)（推友生态作品）
- **版本**: v2.0.4（截至 2026-03-27）
- **适用**: Claude Code、OpenClaw 等支持 Agent Skill 的工具

## 来源
- 原文: [开源 Skill 自动排版发送公众号](https://x.com/lxfater/status/2037047059384328315)
