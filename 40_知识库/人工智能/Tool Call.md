---
area: [[人工智能]]
tags: [AI-Agent, 工具调用, API]
created: 2026-03-05
---
# Tool Call

## 定义

Tool Call（工具调用）是大语言模型与外部工具交互的标准机制。模型通过输出特定格式的 JSON 来声明它想要调用某个工具，然后由运行时环境解析这个 JSON，执行相应的工具，并将结果返回给模型。

## 要点

- **标准协议**：OpenAI 和 Anthropic 都采用了类似的工具调用协议
- **JSON 格式**：模型输出结构化的 JSON，包含工具名称和参数
- **运行时执行**：由 Agent 框架负责截获 JSON 并执行实际操作
- **结果反馈**：工具执行结果（stdout/stderr）返回给模型继续推理

## 示例

**模型输出的 Tool Call JSON**：
```json
{
  "tool": "bash",
  "parameters": {
    "command": "ls -la"
  }
}
```

**运行时处理流程**：
1. Agent 框架截获这个 JSON
2. 解析出工具名称（bash）和参数（command: "ls -la"）
3. 在本地执行命令
4. 将输出返回给模型：
```
total 48
drwxr-xr-x  12 user  staff   384 Mar  5 10:00 .
drwxr-xr-x   8 user  staff   256 Mar  4 15:30 ..
-rw-r--r--   1 user  staff  1024 Mar  5 09:45 README.md
```

**典型的工具类型**：
- **Bash**：执行命令行命令
- **Read**：读取文件内容
- **Write**：写入文件
- **Search**：搜索代码库
- **HTTP Request**：调用外部 API

## 相关概念

- [[Tool Handler]]
- [[AI Agent]]
- [[Claude Code]]
- [[API]]

## 参考资料

- [[learn-claude-code架构拆解]]
- OpenAI Function Calling 文档
- Anthropic Tool Use 文档
