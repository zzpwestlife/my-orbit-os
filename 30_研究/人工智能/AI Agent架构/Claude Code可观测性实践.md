---
created: 2026-03-05
type: reference
area: [[人工智能]]
tags: [Claude-Code, 可观测性, OTEL, Grafana, 监控]
source: https://mp.weixin.qq.com/s/WqdJxdr-UBTvK12g4a4zmQ
author: 冯若航
---
# Claude Code可观测性实践

## 核心论点

虽然 Claude Code 不开源，但你可以通过它的监控指标和日志，分析出它的大概工作原理。Claude Code 提供 OTEL 格式的指标和日志，配置简单，可以推送到支持 OTEL 的监控系统，用 Grafana 进行可视化。

## 为什么需要可观测性

### 核心问题

我也挺好奇这个 Claude Code 内部到底是怎么工作的。

### 解决方案

通过监控指标和日志，你可以：
- 研究它是怎么做决策的
- 了解它如何使用工具
- 追踪它调用 API 花了多少钱
- 分析整个任务的处理流程

## 配置方法

### 基本配置

Claude Code 提供 OTEL 格式的指标和日志，配置起来其实挺简单：

1. 指定几个环境变量
2. 让它主动推送到支持 OTEL 的监控系统
3. 用 Grafana 进行可视化

### 开箱即用的沙箱环境

作者提供了一个开箱即用的配置模板：
- 找一台 Linux 服务器
- 运行几行命令把环境拉起来
- 自带一个 Claude Code 的环境
- 所有东西都帮你配好了（包括监控）
- 也可以直接把自己的 Claude Code 监控接进去

**最佳实践**：
如果你已经会用 Claude Code，并不需要了解太多细节。你只要告诉它有这么个东西、能干这么个事，并给它准备一台虚拟机，剩下的事它都应该能帮你自动干好。

## 监控面板说明

### 面板结构

监控面板很朴素：
- **上方**：可以选择会话（Session ID）
- **下方**：列出各种各样的事件
- **交互**：通过拖动来查看在处理任务的过程中都产生了哪些事件

### 四大核心事件类型

#### 1. User Prompt

**定义**：你对它说了什么，或者给了什么提示词

**示例**：
- 你给 Claude Code 发一条信息
- 就会有一个 User Prompt 事件

#### 2. API Request

**定义**：调用 API 的请求

**关键字段**：
- **model**：使用的模型（Claude 区分了快速模型和高质量模型）
  - 简单快速的请求：使用快速模型（如 GLM 4.5-air）
  - 复杂任务：使用高质量模型（如 GLM 4.7）
- **Cost**：API 调用开销
- **Token.In**：输入的 Token 数量
- **Token.Out**：输出的 Token 数量
- **Token.Cache.Read**：缓存命中的 Token 数量
- **Token.Cache.Write**：写入缓存的 Token 数量

**价值**：
- 追踪成本
- 分析 Token 使用效率
- 评估缓存命中率

#### 3. Tool Decision

**定义**：系统决定使用什么工具

**关键字段**：
- **Tool**：工具类型（Bash、Read、Write、Search 等）
- **Decision Source**：决策依据
  - 配置文件
  - 询问用户
  - 自动批准规则
- **Decision Result**：决策结果
  - 批准（Approved）
  - 拒绝（Rejected）

**流程**：
```
API Request 完成
→ Tool Decision 事件
→ 模型进行决策，选择工具
→ 根据标准判断是否批准
```

#### 4. Tool Result

**定义**：工具返回的具体结果

**关键字段**：
- **Tool**：使用的工具名称
- **Command**：执行的命令
- **Description**：命令说明
- **Error**：错误信息（如果有）
- **Parameters**：工具参数
- **UserID**：用户标识
- **Success**：是否成功

**流程**：
```
Tool Decision 事件
→ Tool Result 事件
→ 调用工具的关键事件
```

### 事件流程示例

典型的任务处理流程：

```
User Prompt（用户输入）
↓
API Request（调用模型）
↓
Tool Decision（决定使用工具）
↓
Tool Result（工具执行结果）
↓
API Request（将结果反馈给模型）
↓
...（循环）
```

## 沙箱环境的额外价值

### 不仅仅是监控

这个沙箱除了监控 Claude Code，还可以干很多有趣的事情：

**预配置的工具**：
- Claude Code
- VS Code
- Open Code

**基础设施**：
- PostgreSQL 数据库
- Nginx 服务器

**使用场景**：
- 如果你需要一个云服务器开发环境，可以直接使用

### 国内友好

- 可以直接使用不用翻墙的 GLM 模型
- 多配置一行参数就好了

### Vibe 哲学

关于 Claude Code 最美妙的就是：
> 既然你都已经用它了，那你大概也不需要操心这些细节都是怎么弄的，直接动嘴让它自己去 VIBE 自己就好了。

## 实践价值

### 理解 Agent 行为

通过监控面板，你可以：
- 看到 Agent 的决策过程
- 理解它为什么选择某个工具
- 发现性能瓶颈
- 优化 Prompt 和工具配置

### 成本控制

通过 API Request 事件：
- 追踪每次调用的成本
- 分析 Token 使用情况
- 评估缓存效果
- 优化成本结构

### 调试和优化

通过 Tool Decision 和 Tool Result：
- 发现工具调用失败的原因
- 优化工具的批准策略
- 改进错误处理逻辑

## 技术细节

### OTEL（OpenTelemetry）

**定义**：开放的可观测性标准
- 统一的指标、日志、追踪格式
- 支持多种监控系统
- 云原生标准

**优势**：
- 不绑定特定监控平台
- 易于集成
- 社区支持好

### Grafana

**定义**：开源的可视化平台
- 支持多种数据源
- 丰富的图表类型
- 强大的查询能力

**在本场景中的作用**：
- 可视化 Claude Code 的事件流
- 展示 Token 使用趋势
- 分析成本分布

### Victoria Metrics

**定义**：高性能的时序数据库
- 兼容 Prometheus
- 更低的资源消耗
- 更好的压缩率

**在沙箱中的作用**：
- 存储 OTEL 指标
- 提供给 Grafana 查询

## 核心洞察

### 可观测性的重要性

即使是不开源的系统，通过良好的可观测性设计，你也能：
- 理解系统的工作原理
- 优化使用方式
- 控制成本
- 发现问题

### 开箱即用的价值

- 降低学习门槛
- 快速上手
- 专注于使用而非配置

### Vibe 的终极形态

当工具足够智能时，你甚至可以让它自己配置自己的监控系统。

## 相关概念

- [[Claude Code]]
- [[OTEL]]
- [[Grafana]]
- [[可观测性]]
- [[AI Agent]]
- [[工具调用]]

## 参考资料

- Claude Code 监控文档: https://code.claude.com/docs/en/monitoring-usage
- [[learn-claude-code架构拆解]]
- [[从Vibe Coding到Agentic Engineering]]
