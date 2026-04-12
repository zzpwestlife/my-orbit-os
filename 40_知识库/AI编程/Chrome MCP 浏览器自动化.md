---
title: "Chrome MCP 浏览器自动化"
type: wiki
created: 2026-03-26
tags: [知识卡片, AI编程, MCP, 浏览器自动化, Chrome]
---
# Chrome MCP 浏览器自动化

## 核心概念

Chrome 146 版本正式引入原生级 **Remote Debugging（远程调试）** 接口，完美支持 **MCP (Model Context Protocol)** 协议，使 AI Agent 能够直接控制浏览器进行自动化操作。

## 关键技术点

### Chrome DevTools MCP
- Chrome 146 在 `chrome://inspect/#remote-debugging` 页面提供官方远程调试开关
- 勾选 "Allow remote debugging for this browser instance" 即可开启
- 监听地址默认为 `127.0.0.1:9222`
- AI Agent（如 [[Claude Code]]、Codex、Antigravity）可通过标准协议直接连接

### Cookie 状态继承
- 连接后 Agent 可直接继承用户已登录的 Cookie 状态
- 无需重新登录即可操作各类需要认证的网站（微信网页版、内网 OA 系统、股票看板等）

### 操作方式
- **DOM 级精准打击**：直接读取网页无障碍树（AX Tree），100% 精准点击与文本输入
- **静默控制**：AI 在后台操作，不抢夺系统鼠标焦点，用户可同时进行其他工作
- 抛弃了传统的 "大模型截图猜坐标" 方式

## 官方包 vs 社区方案

### 官方 chrome-devtools-mcp 包的问题
- 每次执行指令都重新建立连接
- 安全提示疯狂弹出
- 多标签页时 Puppeteer 底层穷举 Target 易超时

### 推荐：chrome-cdp-skill（WebSocket 直连）
- 零弹窗、秒级响应、百级标签页不卡顿
- 每个标签页仅需授权一次
- 要求 Node.js 22+（使用原生 WebSocket API）
- Mac/Linux: `npx skills add https://github.com/pasky/chrome-cdp-skill -g --all --copy`

## 安全注意事项
- 开启远程调试后，外部应用拥有浏览器完全控制权
- 可任意读取保存的数据、Cookie、网站数据
- 使用完毕后应立即关闭调试端口
- 仅限个人学习和本地使用

## 与现有知识的关联
- [[AI编程方法论]] - Agent 工具链的一部分
- [[Claude-Code-工程实践]] - Claude Code 可通过此方式控制浏览器
- [[MCP]] - Model Context Protocol 的实际应用场景

## 来源
- 原文: [Google 掀牌了：Chrome "一键夺舍" 开启，AI 彻底接管浏览器](https://x.com/xiangxiang103/status/2033710786250739838)
