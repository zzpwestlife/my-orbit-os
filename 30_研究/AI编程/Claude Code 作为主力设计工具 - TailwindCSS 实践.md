---
area: "[[AI编程]]"
tags: [AI, 设计, TailwindCSS, UI, Claude Code, 工作流]
created: 2026-04-13
source: "[[TailwindCSS 设计大神的这个视频强烈推荐.mp4.md]]"
---
# Claude Code 作为主力设计工具：TailwindCSS 实践

> 一个设计师（非程序员）用 Claude Code + TailwindCSS 从零构建营销页面，全程不依赖传统设计工具（Figma 等）。

## 核心洞见

**Claude Code 是设计工具，不只是编码工具。** 对于会 TailwindCSS 的设计师，结合 Claude Code 可以：
- 直接表达设计意图，由 AI 生成代码
- 在真实浏览器中即时预览
- 精确控制每一个像素值

## 工作流程

1. 从空白 Vite 项目模板启动（`npm run dev` → 本地预览）
2. 用提示词描述页面结构：导航栏 + Hero + 功能区 + 数据统计 + 评价 + CTA
3. 接受 AI 初稿，然后**逐层精调**

## 关键设计技巧

### 边框与阴影
- ❌ 避免纯色边框（会造成浑浊阴影效果）
- ✅ 透明边框：`ring-1 ring-zinc-950/10`（灰-950 + 10% 不透明度）
- 容器内的截图：内边距 8px + 同心圆角（`rounded-[calc(border-radius-2px)]`）

### 字体系统
- 使用 **Inter Variable**（可变字体），而非普通 Inter
- 字重精调：标题用 `font-[550]`（中等偏粗，界于 medium 和 semibold 之间）
- 大标题收紧字距：`tracking-tight`

### 按钮规范（Adam Wathan 风格）
- 高度：38px，字号：14px
- 形状：药丸形（`rounded-full`）
- 核心技巧：`inline-flex` 而非 `flex` 确保精确对齐
- 次级按钮：外环设计（`ring-1 ring-zinc-950/10`）

### 布局排版
- 分栏标题：主标题 3/5 + 辅助文本 2/5（顶部对齐）
- 容器最大宽度：1280px
- 段落字符数限制：约 40 字符（用 `max-w-[40ch]`）
- 辅助文本缩小至 16px

### 视觉标识系统
- 眉标（Eyebrow）：等宽字体（Geist Mono）+ 全大写 + 宽松字距 + `text-zinc-600`

### 截图展示技巧
- 3x 分辨率截图确保高清
- 统一圆角半径与中性灰配色
- 全屏截图后局部裁剪聚焦重点区域
- 边框增强：`outline outline-1 outline-zinc-950/5`

### 画布网格（参考 Stripe/Linear）
- 全宽边框 + 容器贴合
- 16px 顶部内边距调整

## 非程序员的使用心得

> "我对命令行操作还非常陌生，Adam Wathan 帮我配置了环境。现在我只会切换目录和启动开发服务器。"

关键心理转变：
- 不需要懂代码，只需要**会描述设计意图**
- Claude Code 理解 TailwindCSS 的语义（`ring-zinc-950/10` > `border border-zinc-200`）
- 错误和调整过程公开展示（"这个角落不太对劲"→ 调整），增加真实感

## 相关工具

- Ghostty（终端）
- Vite + TailwindCSS（项目模板）
- Ui.sh（作者正在开发的 AI 设计工具）

## 相关笔记

- [[AI Native 研发模式 - 从辅助编码到零人工 Coding]]
- [[渐进式 Spec Coding 实践指南]]
