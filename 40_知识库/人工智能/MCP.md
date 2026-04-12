---
area: [[人工智能]]
tags: [协议, AI架构, 互操作性]
created: 2026-03-04
---
# MCP

## 定义

MCP（Model Context Protocol）是一种协议标准，用于解决 AI 模型与外部数据源和工具的连接问题。它定义了模型如何访问数据库、CRM、网盘等外部系统的标准化接口。

## 要点

- **连接层协议**：解决"能连什么"的问题（数据库、CRM、网盘等）
- **标准化接口**：提供统一的方式让模型访问不同的数据源
- **互操作性**：避免每个 AI 系统都需要自己实现数据连接
- **与 Skills 互补**：MCP 负责连接，Skills 负责业务逻辑

## 示例

**MCP 的应用场景**：

1. **数据库连接**
   - 通过 MCP 连接 PostgreSQL、MySQL
   - 模型可以查询数据，但不需要知道具体的连接细节

2. **企业系统集成**
   - 连接 Salesforce CRM
   - 连接 Google Drive
   - 连接内部 ERP 系统

3. **工具调用**
   - 调用计算器
   - 调用代码执行环境
   - 调用 API 服务

**MCP vs Skills**：
- **MCP**：解决"能连什么"（基础设施层）
- **Skills**：解决"怎么做对"（业务逻辑层）

例如：
- MCP 让模型能够连接财务数据库
- Skill 定义了如何正确地生成财务报表

## 相关概念

- [[Claude Skills]]
- [[AI Agent]]
- [[API 网关]]
- [[企业AI架构]]

## 参考资料

- [[Anthropic的战略转向]]
- Model Context Protocol 规范文档
