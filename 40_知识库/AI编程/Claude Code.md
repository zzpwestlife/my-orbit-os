---
area: [[AI编程]]
tags: [AI工具, 编程助手, Anthropic]
created: 2026-03-06
---
# Claude Code

## 定义

Claude Code 是 Anthropic 推出的 AI 编程助手，基于 Claude 大语言模型，能够在终端环境（TUI）中自主执行编程任务。它不仅能生成代码，还能操作文件系统、运行命令、管理项目，是一个具备完整工具调用能力的 [[Agentic Engineering]] 实践。

## 要点

- **终端原生**：运行在命令行界面，直接操作文件系统和执行命令
- **工具调用**：支持 Bash、文件读写、搜索、Git 等多种工具
- **自主规划**：能够分解复杂任务，制定执行计划
- **上下文管理**：通过渐进式披露（Progressive Disclosure）管理大型代码库
- **Skills 系统**：支持可复用的技能模块，按需加载专业能力
- **可观测性**：提供 OTEL 格式的监控指标和日志
- **多模型支持**：可配置使用不同的模型（Haiku、Sonnet、Opus）

## 示例

### 基本使用

```bash
# 启动 Claude Code
claude

# 自然语言描述任务
"帮我重构 auth 模块，提取公共逻辑"

# 使用 Skills
/research "深入研究这个 API 的实现"
```

### 可观测性配置

通过环境变量启用 OTEL 监控：

```bash
export OTEL_EXPORTER_OTLP_ENDPOINT="http://localhost:4318"
```

监控事件类型：
- **User Prompt**：用户输入
- **API Request**：模型调用（包含 Token 和成本）
- **Tool Decision**：工具选择决策
- **Tool Result**：工具执行结果

### 扩展插件

- **oh-my-claudecode**：多智能体编排插件
- **feature-dev**：功能开发专用插件

## 相关概念

- [[Agentic Engineering]]
- [[多智能体协作]]
- [[oh-my-claudecode多智能体编排]]
- [[Vibe Coding]]
- [[Agent 架构模式]]

## 参考资料

- 官方文档：https://code.claude.com/docs
- 监控文档：https://code.claude.com/docs/en/monitoring-usage
- learn-claude-code 项目：https://github.com/anthropics/learn-claude-code
