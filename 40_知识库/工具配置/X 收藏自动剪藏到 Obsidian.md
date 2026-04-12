---
title: "X 收藏自动剪藏到 Obsidian"
type: wiki
created: 2026-03-26
tags: [知识卡片, 工具配置, obsidian, chrome插件, 自动化, 知识管理]
---
# X 收藏自动剪藏到 Obsidian

## 概述
**x-bookmark-to-obsidian** 是一个 Chrome 浏览器插件，实现在 X (Twitter) 上点击"收藏"后，帖子内容自动抓取为 Markdown 并写入 [[Obsidian]]。解决了"先收藏、之后再搬运"这个知识管理中常见的动作断点问题。

相关项目: [[Obsidian剪藏配置指南]]

## 工作原理（三段式架构）
1. **Content Script** — 浏览器端监听 X 的收藏动作
2. **Background Script** — 将帖子 URL 和元数据发送给 Native Host
3. **Native Host** — 本地抓取帖子内容，转为 Markdown，写入 Obsidian 指定目录

关键设计：浏览器自动化真正难的不是前端点击，而是后面的抓取、写入、去重、后处理整条链路。

## 安装步骤

### 前置条件
- Chrome 浏览器
- Obsidian 已安装并有可用 Vault

### 安装流程（v2.2.0+）
1. 从 [GitHub Releases](https://github.com/zhaoscsc/x-bookmark-to-obsidian) 下载两个 ZIP：
   - `x-bookmark-to-obsidian-extension` — 扩展目录
   - `x-bookmark-to-obsidian-installer` — 本机安装器
2. 解压 extension.zip，在 `chrome://extensions` 中加载已解压扩展程序
3. 解压 installer.zip，双击 `install.command`
4. 重启 Chrome
5. 在扩展弹窗中选择 Obsidian 保存目录

### 注意事项
- macOS 安装器可能触发安全提醒（提示移到废纸篓），需在 **系统设置 → 隐私与安全性** 中允许
- v2.2.0 起使用固定扩展 ID，无需手动复制
- 单帖抓取能力已内置到发行包，不再依赖外部 `~/.agents` 环境

## 使用方式
在 X 上点击收藏即可，帖子会自动以 Markdown 格式保存到指定的 Obsidian 目录中。

## 常见问题
- **安全弹窗**: macOS 首次运行 install.command 时会有安全提示，需手动在系统设置中允许
- **为什么需要 Native Host**: 这是静默写入任意 Obsidian 路径的关键能力，纯浏览器扩展无法直接操作本地文件系统
- **与 Obsidian Web Clipper 的区别**: Web Clipper 需要手动触发剪藏，本插件是收藏即自动同步，零操作摩擦

## 来源
- 项目地址: [x-bookmark-to-obsidian](https://github.com/zhaoscsc/x-bookmark-to-obsidian)
- 原文: [我做了一个 chrome 浏览器插件，让 X 里的收藏自动进入 Obsidian](https://x.com/Chat24954Lip/status/2034876636542509438)