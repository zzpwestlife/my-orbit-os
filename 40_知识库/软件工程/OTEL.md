---
area: [[软件工程]]
tags: [可观测性, 监控, OpenTelemetry]
created: 2026-03-05
---
# OTEL

## 定义

OTEL（OpenTelemetry）是一个开放的可观测性标准，提供统一的指标、日志、追踪格式。它是云原生计算基金会（CNCF）的项目，旨在为应用程序提供标准化的遥测数据收集和导出机制。

## 要点

- **统一标准**：统一的指标、日志、追踪格式
- **厂商中立**：不绑定特定监控平台
- **易于集成**：支持多种编程语言和框架
- **云原生**：CNCF 标准，广泛的社区支持

## 示例

**OTEL 的三大支柱**：

**1. Metrics（指标）**：
```
- API 调用次数
- 响应时间
- 错误率
- Token 使用量
```

**2. Logs（日志）**：
```
- 结构化日志
- 事件记录
- 错误信息
- 调试信息
```

**3. Traces（追踪）**：
```
- 请求链路
- 服务调用关系
- 性能瓶颈
- 依赖分析
```

**在 Claude Code 中的应用**：

```bash
# 配置环境变量
export OTEL_EXPORTER_OTLP_ENDPOINT="http://localhost:4318"
export OTEL_SERVICE_NAME="claude-code"

# Claude Code 自动推送遥测数据
# - User Prompt 事件
# - API Request 事件（包含 Token 和 Cost）
# - Tool Decision 事件
# - Tool Result 事件
```

**数据流**：
```
Claude Code
  ↓ (OTEL 协议)
OTEL Collector
  ↓
Victoria Metrics (存储)
  ↓
Grafana (可视化)
```

**优势**：
- **标准化**：一次集成，多平台使用
- **灵活性**：可以切换不同的后端存储
- **完整性**：覆盖指标、日志、追踪三大维度
- **生态系统**：丰富的工具和集成

**实际价值**：
- 理解系统行为
- 追踪性能问题
- 成本分析
- 调试和优化

## 相关概念

- [[可观测性]]
- [[Grafana]]
- [[监控系统]]
- [[Claude Code]]

## 参考资料

- [[Claude Code可观测性实践]]
- OpenTelemetry 官方文档
- CNCF OpenTelemetry 项目
