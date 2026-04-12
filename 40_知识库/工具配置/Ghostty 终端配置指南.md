---
title: "Ghostty 终端配置指南"
type: wiki
created: 2026-03-26
tags: [知识卡片, 工具配置, ghostty, 终端, terminal]
---
# Ghostty 终端配置指南

## 概述
[[Ghostty]] 是由 HashiCorp 创始人 Mitchell Hashimoto 开发的开源终端模拟器。GPU 加速渲染，速度快、内存省。纯文本 key=value 配置，内置分屏、下拉终端、窗口状态恢复。目前仅支持 macOS 和 Linux。

## 安装
```bash
brew install --cask ghostty
```

## 关键配置

### 配置文件位置
```
~/.config/ghostty/config
```
快捷键打开: `Cmd + ,`  |  重载配置: `Cmd + Shift + ,`

### 常用内置命令
```bash
ghostty +list-themes        # 列出 200+ 内置主题
ghostty +list-fonts          # 列出可用字体
ghostty +show-config --default --docs  # 完整配置手册
```

### 主题与外观
```yaml
# 跟随系统深色模式自动切换
theme = light:Catppuccin Latte,dark:Catppuccin Mocha
background-opacity = 0.88
background-blur = 20
macos-titlebar-style = tabs    # hidden 会导致 Cmd+T 开新窗口而非 Tab
unfocused-split-opacity = 0.9
```

### 字体
```bash
# 推荐：Maple Mono NF CN（连字+图标+中文全包）
brew install --cask font-maple-mono-nf-cn
# 备选：JetBrains Mono（Ghostty 内置 Nerd Font 图标渲染）
brew install --cask font-jetbrains-mono
```
```yaml
font-family = "Maple Mono NF CN"
font-size = 14
font-thicken = true
font-feature = calt
font-feature = liga
```

### 窗口行为
```yaml
window-save-state = always                 # 重启后恢复分屏布局
window-inherit-working-directory = true    # 新分屏继承当前目录
window-inherit-font-size = true
window-padding-x = 4
window-padding-y = 4
window-padding-balance = true
```

### Quick Terminal（下拉终端）
```yaml
keybind = global:ctrl+grave_accent=toggle_quick_terminal
quick-terminal-screen = main
quick-terminal-position = top
quick-terminal-size = 50%
quick-terminal-autohide = true
quick-terminal-animation-duration = 0.15
```

## 快捷键速查

### 分屏
| 操作 | 快捷键 |
|------|--------|
| 左右分屏 | `Cmd + D` |
| 上下分屏 | `Cmd + Shift + D` |
| 下一个/上一个分屏 | `Cmd + Shift + ]` / `[` |
| 放大/还原当前分屏 | `Cmd + Shift + Enter` |
| 关闭当前分屏 | `Cmd + W` |

### Tab 与窗口
| 操作 | 快捷键 |
|------|--------|
| 新建 Tab | `Cmd + T` |
| 切换 Tab | `Cmd + 数字键` |
| 全屏切换 | `Cmd + Enter` |

### 搜索与工具
| 操作 | 快捷键 |
|------|--------|
| 搜索终端输出 | `Cmd + F` |
| 命令面板 | `Cmd + Shift + P` |
| 打开配置 | `Cmd + ,` |
| 重载配置 | `Cmd + Shift + ,` |

### 可选：Vim 风格分屏跳转
```yaml
keybind = cmd+shift+h=goto_split:left
keybind = cmd+shift+j=goto_split:down
keybind = cmd+shift+k=goto_split:up
keybind = cmd+shift+l=goto_split:right
```

## 完整配置参考
```yaml
# --- 外观 ---
theme = light:Catppuccin Latte,dark:Catppuccin Mocha
background-opacity = 0.88
background-blur = 20
macos-titlebar-style = tabs
unfocused-split-opacity = 0.9

# --- 字体 ---
font-family = "Maple Mono NF CN"
font-size = 14
font-thicken = true
font-feature = calt
font-feature = liga

# --- 窗口行为 ---
window-save-state = always
window-inherit-working-directory = true
window-inherit-font-size = true
window-padding-x = 4
window-padding-y = 4
window-padding-balance = true

# --- Quick Terminal ---
keybind = global:ctrl+grave_accent=toggle_quick_terminal
quick-terminal-screen = main
quick-terminal-position = top
quick-terminal-size = 50%
quick-terminal-autohide = true
quick-terminal-animation-duration = 0.15

# --- Shell 集成 ---
shell-integration-features = cursor,sudo,title,ssh-terminfo,ssh-env

# --- 滚动 ---
scrollback-limit = 50000000

# --- 光标 ---
cursor-style = block
cursor-style-blink = false
mouse-hide-while-typing = true

# --- 剪贴板 ---
copy-on-select = clipboard
clipboard-trim-trailing-spaces = true

# --- macOS 专属 ---
confirm-close-surface = false
macos-option-as-alt = true
```

## 常见问题
- **hidden 模式下 Cmd+T 行为变化**: `macos-titlebar-style = hidden` 会导致 Cmd+T 开新窗口而非新 Tab，建议用 `tabs`
- **字体回退**: 使用 Maple Mono 前需先安装，否则回退到系统默认字体
- **Ghostty 内置 Nerd Font 渲染**: 即使用非 NF 字体（如 JetBrains Mono），终端图标也能正常显示

## 来源
- 原文: [Ghostty 终端入门指南：安装、配置、用起来](https://x.com/alin_zone/status/2033524177295274496)