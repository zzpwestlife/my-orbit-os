---
title: "Mac 软件清单"
type: wiki
created: 2026-03-26
tags: [知识卡片, 工具配置, mac, homebrew, 开发环境]
---
# Mac 软件清单

## 概述
新 Mac 到手后的完整软件安装清单，涵盖命令行环境、AI 编程、编辑器、效率工具、系统工具等多个类别。核心理念：从零开始配置，60% 以上软件通过 [[Homebrew]] 安装。

## 安装顺序

### 第一步：前置依赖
```bash
xcode-select --install
```

### 第二步：包管理器
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 第三步：Shell 增强
```bash
# Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
# fnm（Node.js 版本管理，替代 nvm）
brew install fnm
```

### 第四步：CLI 工具
```bash
brew install fzf zoxide eza ripgrep bat gh yt-dlp imagemagick ffmpeg
brew install --cask font-jetbrains-mono-nerd-font font-hack-nerd-font
```

| 工具 | 用途 |
|------|------|
| **fzf** | 模糊搜索，Ctrl+R 搜历史命令 |
| **zoxide** | 智能目录跳转，替代 cd |
| **eza** | 现代版 ls，带颜色和图标 |
| **ripgrep** | 极速文本搜索，替代 grep |
| **bat** | 带语法高亮的 cat |
| **gh** | GitHub 官方 CLI |
| **yt-dlp** | 视频下载（YouTube 等平台） |
| **imagemagick** | 命令行图像处理 |
| **ffmpeg** | 音视频转码 |

## 分类软件清单

### AI 编程助手
```bash
# Claude Code（主力）
curl -fsSL https://claude.ai/install.sh | bash
# Codex CLI
npm install -g @openai/codex
# OpenCode
curl -fsSL https://opencode.ai/install | bash
# Copilot CLI
brew install --cask copilot-cli
# Codex App（桌面端）
brew install --cask codex-app
```

### 编辑器 & IDE
```bash
brew install --cask visual-studio-code
# Xcode → App Store
```

### 开发辅助
```bash
brew install --cask cc-switch    # Claude Code 多账号切换
brew install --cask claudebar    # 菜单栏监控 Claude 用量
brew install --cask orbstack     # Docker 容器管理（替代 Docker Desktop）
```

### 效率工具
```bash
brew install --cask raycast          # 快捷启动器
brew install --cask jordanbaird-ice  # 菜单栏图标管理
brew install stats                   # 系统监控
brew install --cask piclist          # 图床上传
brew install --cask shottr           # 截图标注
brew install --cask kap              # 屏幕录制/GIF
brew install --cask obs              # 直播推流/录制
brew install --cask mac-mouse-fix    # 鼠标增强
brew install --cask calibre          # 电子书管理
```

### 系统工具
```bash
brew install --cask ghostty          # 终端模拟器（GPU 加速）
brew install --cask google-chrome    # 浏览器
# Quantumult X → App Store
# 微信输入法 → 官网下载
```

### 个人管理
```bash
brew install --cask obsidian         # 笔记 & 知识库
# 滴答清单 → App Store
```

### 影音娱乐
```bash
brew install --cask iina             # 视频播放器
brew install --cask steam            # 游戏平台
# Infuse → App Store
```

### 手动安装
- **App Store**: Xcode、微信、Infuse、Telegram、滴答清单、Quantumult X
- **官网下载**: IBKR Desktop、thinkorswim、网易 UU 远程、Photoshop、Lightroom（Adobe Creative Cloud）、微信输入法

## 常见问题
- Homebrew 安装时会自动提示安装 Xcode Command Line Tools，所以第一步可以跳过
- Adobe 全家桶只能通过官网 Creative Cloud 安装，没有 Homebrew 支持
- IBKR 和 thinkorswim 是 Java 开发，建议官网下载避免兼容问题

## 来源
- 原文: [新 Mac 到手，我打算装这些](https://x.com/innomad_io/status/2032668443863073207)