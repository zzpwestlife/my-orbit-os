---
area: "[[AI编程]]"
tags: [Skill, 工具, 管理, Claude Code]
created: 2026-04-21
---
# Skill Hub

## 定义

Skill Hub 是一个 npm 工具，提供可视化界面统一管理本地所有 [[Claude Code]] Skill，解决 Skill 数量超过 20 个后的散乱管理问题。

## 要点

- **一键扫描**：覆盖全局目录、插件目录（递归）、注册项目目录、常见开发路径，100+ Skill 一次聚合
- **可视化展示**：按来源/作用域/项目分组，支持关键词搜索
- **浏览器内编辑**：直接改 SKILL.md，每次保存前自动拍快照版本
- **版本回滚**：点击回退按钮即可，无需学 Git
- **相似检测**：自动识别内容重叠度高的 Skill，辅助去重
- **Git 多设备同步**：用 GitHub 私有仓库做后端，push/pull 实现多台设备同步，不需要懂 Git 命令

## 示例

```bash
# 安装并启动
npm install -g https://github.com/Backtthefuture/skillmanager/raw/main/release/claude-skill-hub.tgz
skill-hub
# 自动打开 localhost:3456
```

## 相关概念

- [[Darwin Skill]] — Skill 质量自动优化工具
- [[Claude Code]] — Skill 运行环境
- [[dotclaude 插件生态]] — Skill 的组织体系

## 参考资料

- GitHub：https://github.com/Backtthefuture/huangshu
