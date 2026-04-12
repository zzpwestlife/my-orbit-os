---
area: [[软件架构]]
tags: [设计模式, Agent架构, 工具管理]
created: 2026-03-05
---
# Tool Handler

## 定义

Tool Handler（工具处理器）是 AI Agent 架构中的一个设计模式，用于管理和分发多个工具的调用。它通过动态分发机制（Dispatch），根据模型输出的工具名自动匹配对应的执行函数，保证了核心循环的稳定性。

## 要点

- **动态分发**：根据工具名称自动路由到对应的处理函数
- **JSON Schema**：每个工具都有自己的 JSON Schema 定义
- **解耦设计**：工具的增删不影响主循环逻辑
- **可扩展性**：后续增加再多能力也无需修改核心架构

## 示例

**没有 Tool Handler 的问题**：
```python
# 主循环中充斥着 if-else
if tool_name == "bash":
    result = execute_bash(params)
elif tool_name == "read":
    result = read_file(params)
elif tool_name == "write":
    result = write_file(params)
# ... 50 个工具就有 50 个 elif
```

**使用 Tool Handler 的优雅方案**：
```python
# 工具注册
tool_registry = {
    "bash": BashTool(),
    "read": ReadTool(),
    "write": WriteTool(),
    # ... 新增工具只需在这里注册
}

# 主循环保持简洁
def agent_loop():
    while True:
        response = llm.call(messages)
        tool_call = parse_tool_call(response)

        # 动态分发
        handler = tool_registry.get(tool_call.name)
        result = handler.execute(tool_call.parameters)

        messages.append({"role": "tool", "content": result})
```

**工具定义示例**：
```python
class BashTool:
    schema = {
        "name": "bash",
        "description": "Execute bash command",
        "parameters": {
            "command": {"type": "string", "required": True}
        }
    }

    def execute(self, params):
        return subprocess.run(
            params["command"],
            shell=True,
            capture_output=True
        ).stdout
```

**优势**：
- 主循环代码量不随工具数量增长
- 新增工具只需实现接口并注册
- 每个工具可以独立测试和维护
- 符合开闭原则（对扩展开放，对修改关闭）

## 相关概念

- [[Tool Call]]
- [[设计模式]]
- [[AI Agent]]
- [[动态分发]]

## 参考资料

- [[learn-claude-code架构拆解]]
- 《设计模式》- 策略模式
