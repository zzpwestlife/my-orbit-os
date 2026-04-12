---
type: "inbox"
status: "processed"
archived: 2026-03-26
source: "web-clipper"
url: "https://x.com/innomad_io/status/2032668443863073207"
created: 2026-03-16
---
每次换新 Mac，都是一个新的开始。我从来不食用 Mac 的迁移工具，从零开始的机会太难得了。

昨天发了一条 X 推文之后，评论区不少朋友推荐了很多好用的 App，我全部仔细看了一遍，趁热打铁按照我自己的需求整理了一份 Mac 软件清单，分享给大家。

> 3 月 13 日
> 
> M5 Air 到货，有什么新的必装推荐嘛？ 目前打算： SuperCmd 替代 Raycast Ghostty 替换 iTerm2 Obsidian 替换 Notion

> 这份清单是按照我当前的习惯整理的，暂时没有把评论区所有推荐的 App 都加进来。后续随着试用深入，可能会有增删调整。如果你有特别好用的 Mac 软件推荐，欢迎留言交流。

## 第一步：命令行环境

拿到新 Mac，第一件事不是装 App，而是把命令行搭好。后面大部分软件都靠它安装。

## 前置依赖

```text
# Xcode Command Line Tools — 编译工具链，很多开发工具的前置依赖，比如 git
xcode-select --install
```

这玩意不到 2GB，装完你就有了 git、clang、make 这些基础工具。和完整的 Xcode（30GB 起步）不是一回事，别搞混了。

其实如果手动执行这个，后面安装 Homebrew 的时候也会提示你安装的，所以也可以直接跳过这步，Homebrew 会帮你装。

## 包管理器

[Homebrew](https://brew.sh/) — macOS 的包管理器，一切的起点，无论是命令行工具还是图形化应用，都可以用它安装，不用你自己去下载安装包了。后面你会看到大量 brew install，没它寸步难行。

## Shell 增强

[Oh My Zsh](https://ohmyz.sh/) — Zsh 配置框架，装完命令行立刻好看好用。curl 一行搞定。

[fnm](https://github.com/Schniz/fnm) — 快速 Node.js 版本管理，比 nvm 快得多。我是 nvm 老玩家了，这次换 fnm 试试，因为 fnm 不再是一堆脚本，不会有版本问题，可以直接 brew 安装。

```text
brew install fnm
```

## CLI 工具

这一堆全部 brew install 一把梭：

```text
brew install fzf zoxide eza ripgrep bat gh yt-dlp imagemagick ffmpeg
brew install --cask font-jetbrains-mono-nerd-font font-hack-nerd-font
```

逐个说下为什么装：

- **fzf** — 模糊搜索，Ctrl + R 搜历史命令从此告别痛苦
- **zoxide** — 智能目录跳转，用过就回不去 cd 了
- **eza** — 现代版 ls，带颜色带图标
- **ripgrep** — 极速文本搜索，代码库里找东西比 grep 快一个量级
- **bat** — 带语法高亮的 cat，看文件终于不用眯眼了
- **gh** — GitHub 官方 CLI，PR、Issue 全在终端里搞定
- **yt-dlp** — 视频下载神器，YouTube 和各种平台通吃
- **imagemagick** — 命令行图像处理，批量加水印、裁剪都靠它
- **ffmpeg** — 音视频转码瑞士军刀
- **JetBrains Mono / Hack Nerd Font** — 两款开发者等宽字体，终端和编辑器必备

## 开发工具

## AI 编程助手

无论是 Coding 还是创作，现在都离不开 AI Agent 了。目前来看没有哪家恒强或者可以一劳永逸的，所以我选了这些，轮着用。

[Claude Code](https://claude.ai/code) — Anthropic 出的 AI 编程 CLI，我目前的主力

```text
curl -fsSL https://claude.ai/install.sh | bash
```

[Codex CLI](https://github.com/openai/codex) — OpenAI 的终端编程助手

```text
npm install -g @openai/codex
```

[OpenCode](https://opencode.ai/) — 开源 AI 编码工具，做备用。

```text
curl -fsSL https://opencode.ai/install | bash
```

[GitHub Copilot CLI](https://github.com/features/copilot) — GitHub Copilot 的。Copilot 我是 Pro+ 套餐，装一个 cli 备用。主要还是在 VS Code 里用 Copilot。

```text
brew install --cask copilot-cli
```

[Codex App](https://github.com/openai/codex) — OpenAI 编程桌面端，比 CLI 多了可视化界面，逐渐成为主力中。

```text
brew install --cask codex-app
```

现在 AI 编程工具卷得飞起，目前 Claude Code、 Codex 和 Copilot 用的多一些，但这个赛道变化太快，半年后的答案可能完全不同。

## 编辑器 & IDE

[VS Code](https://code.visualstudio.com/) — 代码编辑器，又称「微软大战代码」，不用多介绍了

```text
brew install --cask visual-studio-code
```

[Xcode](https://developer.apple.com/xcode/) — Apple 开发 IDE，有了 AI 之后：老师，我也会 Swift 了！🤪 **App Store**

## 开发辅助

[CC Switch](https://github.com/farion1231/cc-switch) — Claude Code 配置切换，多账号 / 多模型随时切

```text
brew install --cask cc-switch
```

[ClaudeBar](https://github.com/tddworks/ClaudeBar) — 菜单栏监控 Claude 用量，防止月底超额

```text
brew install --cask claudebar
```

[OrbStack](https://orbstack.dev/) — Docker 容器管理，比 Docker Desktop 轻量太多

```text
brew install --cask orbstack
```

## 交易投资

作为一个业余交易员，交易软件当然少不了。

[IBKR Desktop](https://www.interactivebrokers.com/) — 盈透证券交易平台，娃出生之后，IB 账户作为娃的股票代持账户了。桌面端用的少。 **官网下载**

[thinkorswim](https://www.schwab.com/trading/thinkorswim) — 嘉信的交易分析平台，期权交易主力工具 **官网下载**

这两个都是 Java 开发，很庞大，很古早，直接官网下载，避免奇怪的问题。

## 效率工具

这一类装得最多，也是日常用得最频繁的。

[Raycast](https://raycast.com/) — 快捷启动器，替代系统自带的 Spotlight

```text
brew install --cask raycast
```

[Ice](https://icemenubar.app/) — 菜单栏图标管理，把不常用的图标藏起来（替换掉原来的 Hidden Bar）

```text
brew install --cask jordanbaird-ice
```

[Stats](https://github.com/exelban/stats) — 菜单栏系统监控，CPU、内存、网速一目了然

```text
brew install stats
```

[PicList](https://piclist.cn/) — 图床上传管理，写博客必备

```text
brew install --cask piclist
```

[Shottr](https://shottr.cc/) — 截图 & 标注，轻量好用，已掏钱购买。

```text
brew install --cask shottr
```

[Kap](https://getkap.co/) — 屏幕录制，导出 GIF 或视频

```text
brew install --cask kap
```

[OBS](https://obsproject.com/) — 直播推流 & 录制

```text
brew install --cask obs
```

[Mac Mouse Fix](https://macmousefix.com/) — 鼠标功能增强，第三方鼠标用户必装

```text
brew install --cask mac-mouse-fix
```

[Calibre](https://calibre-ebook.com/) — 电子书管理 & 格式转换

```powershell
brew install --cask calibre
```

[Dropover](https://dropoverapp.com/) — 文件拖放暂存区，拖文件不用精确对准窗口了，评论区 X 友推荐的，试用一下看看。

[Keka](https://www.keka.io/) — 文件压缩 / 解压

## 系统工具

[Ghostty](https://ghostty.org/) — 跨平台原生终端模拟器，用平台原生 UI + GPU 加速

```text
brew install --cask ghostty
```

[Chrome](https://www.google.com/chrome/) — 浏览器

```text
brew install --cask google-chrome
```

[Quantumult X](https://quantumult.app/) — 网络代理工具，很多人用小火箭。火箭很好，不过我习惯圈了。 **App Store**

[微信输入法](https://z.weixin.qq.com/) — 输入法，主要想用它的语音，如果豆包有 Mac 版本就好了。 **官网下载**

## 个人管理

[Obsidian](https://obsidian.md/) — Markdown 笔记 & 知识库，我所有的文章都在这里写

```text
brew install --cask obsidian
```

[滴答清单](https://ticktick.com/) — 任务管理 & GTD，随手记和任务安排，已经离不开了。年费会员用户。 **App Store**

## 社交通讯

[Telegram](https://telegram.org/) — 即时通讯 **App Store**

[微信](https://weixin.qq.com/) — 即时通讯 **App Store**

[网易 UU 远程](https://uuyc.163.com/) — 远程桌面控制，控制下原来的 Mac mini，不用占用显示器了。 **官网下载**

## 影音娱乐

[IINA](https://iina.io/) — 轻量视频播放器，macOS 原生设计

```text
brew install --cask iina
```

[Steam](https://store.steampowered.com/) — 游戏平台

```text
brew install --cask steam
```

[Infuse](https://firecore.com/infuse) — 全格式视频播放，NAS 用户必备 **App Store**

## 摄影后期

[Photoshop](https://www.adobe.com/products/photoshop.html) — 图像编辑 **官网下载**

[Lightroom](https://www.adobe.com/products/photoshop-lightroom.html) — 照片后期处理 **官网下载**

Adobe 全家桶只能走官网 Creative Cloud 装，没有 Homebrew 的命。

## 一挪迈的总结

整理完发现，大概 60% 的软件都能通过 Homebrew 安装。如果你也是 Mac 用户，强烈建议把 Homebrew 作为第一个装的东西。

这份清单是我当前的快照，半年后大概率会有变化，到时候看看要不要再更新一遍。

如果你有什么好用的 Mac 软件推荐，欢迎留言交流。

---

## 完整安装指南

### 第一步：安装 Xcode Command Line Tools

```bash
xcode-select --install
```

### 第二步：安装 Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 第三步：一键安装所有 Homebrew 软件

```bash
brew install fnm fzf zoxide eza ripgrep bat gh yt-dlp imagemagick ffmpeg && brew install --cask font-jetbrains-mono-nerd-font font-hack-nerd-font ghostty visual-studio-code cursor orbstack docker tableplus sequel-ace postman insomnia raycast supercmd alfred cleanshot-x shottr bartender stats istat-menus monitorcontrol rectangle magnet karabiner-elements bettertouchtool keyboard-maestro hazel dropover yoink paste cleanmymac sensei appcleaner google-chrome arc brave firefox microsoft-edge obsidian notion logseq bear typora ulysses drafts devonthink eagle pixave itsycal fantastical things omnifocus todoist ticktick notion-calendar cron mimestream spark airmail iina steam
```

### 第四步：安装 Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 第五步：安装 Claude Code

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

### 第六步：手动安装以下软件

**App Store：**
- Xcode
- 微信
- Infuse

**官网下载：**
- 网易 UU 远程
- Photoshop（Adobe Creative Cloud）
- Lightroom（Adobe Creative Cloud）