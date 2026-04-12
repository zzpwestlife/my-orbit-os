---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://mp.weixin.qq.com/s/nYPGR1vHcDNFIGSAH0rGwA"
created: 2026-03-04
processed_to: "[[learn-claude-code架构拆解]]"
processed_date: 2026-03-05
---
Original itadn *2026 年 2 月 26 日 23:22*

2026 年伊始，开发者们的终端里出现了一个幽灵 ——Claude Code。

在它出现之前，我们对 AI 编程的理解大多停留在 Cursor 或 IDE 插件。但 Claude Code 的爆发证明了一件事：当 LLM 获得了完整的终端权限（TUI）、具备了自主规划能力（Agentic Thinking）并能操作文件系统时，它就不再是一个助手，而是一个数字雇员。

最近，GitHub 上一个名为 learn-claude-code 的项目在短短 4 天内狂揽 2 万 Star。它火爆的原因很简单：它把 Claude Code 那个复杂的、带有黑盒性质的 Agent 逻辑，拆解成了 12 个循序渐进的 Python 实现。

![Image](https://mmbiz.qpic.cn/mmbiz_jpg/Bvz4ia0cFWEoXHtW7OKWQowP76DI1qb1Gia5wps84Dm57JoOG0VG6c8lhOyvUd7iah8Sric1rAmMa6Ao2knHbA6DepgmFWFQoGd1JF5gh1KUREA/640?wx_fmt=jpeg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

  

如果你想真正理解什么是 Agent，而不是只会调 API，那么这篇 4000 字的深度解析，将带你走完从 0 到 1 的进化之路。

## 第一部分：Agent 的底层哲学 —— 为什么是 TUI？

在进入代码之前，我们需要回答一个工程问题：为什么 Claude Code 选择了命令行（TUI）而不是图形界面（GUI）？

协议天然对齐： LLM 输出的是文本，而终端命令本质也是文本。

权限原子化： 命令行环境下，每一个 Bash 指令都是一个原子操作，模型可以通过 ls 观察，通过 grep 检索，通过 sed 修改。这种 “观察 - 行动” 的反馈回路在终端里最短。

上下文密度： 终端不包含冗余的 UI 渲染信息，每一位 Token 都花在刀刃上。

learn-claude-code 的核心哲学即源于此：模型本身就是 Agent，开发者需要做的，是构建一套能够承载模型思考的 “基础设施”。

## 第二部分：12 阶阶梯 —— 从最小循环到自治团队

项目将 Agent 的进化分为 12 个阶段（S01-S12），每一节都是一次工程维度的跃迁。

![Image](https://mmbiz.qpic.cn/sz_mmbiz_jpg/Bvz4ia0cFWEop77QxfI6yFCalibqHNKyiamSS5ibjxtovicvHWata1YnNFz1NEtMxkTB8Svb5NcHz0R3n6dIDZibdIxdUYBcXstGMTvKSicGH8CibH4/640?wx_fmt=jpeg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

## S01：最小 Agent 循环（The Agent Loop）

这是所有 Agent 的原点。

它的核心是一个简单的 while True 循环。在这个循环中，系统通过 System Prompt 告诉模型：“你拥有调用 Bash 的能力”。模型输出一个特定格式的 JSON（Tool Call），Python 脚本截获该 JSON，在本地执行命令，并将 stdout 返回给模型。

\* 事实依据： 这是 OpenAI 和 Anthropic 工具调用协议的标准实现。

\* 心智模型： 观察（User Input） \\rightarrow 思考（LLM） \\rightarrow 行动（Bash） \\rightarrow 结果（Output）。

## S02：多工具扩展（Tool Use）

当工具变多（读文件、网络搜索、Git 操作），代码极易混乱。S02 引入了 Tool Handler 机制。

\* 技术细节： 每一项工具都有自己的 JSON Schema 定义。主循环通过动态分发机制（Dispatch），根据模型输出的工具名自动匹配对应的 Python 函数。

\* 工程意义： 保证了 agent\_loop 的稳定性，后续增加再多能力也无需修改核心架构。

## S03：显式规划（Structured Planning）

对抗幻觉。

模型在执行长任务时容易迷失方向。S03 引入了 Todo List 工具。

\* 事实依据： 这参考了 Claude Code 里的 /todo 指令。

\* 实现方式： 强制模型在调用 Bash 之前，先调用一个 update\_todo 工具。这相当于在 LLM 的外部存储器中维护了一个状态机，显著提升了处理多步骤任务（如重构整个目录）的成功率。

## S04：子 Agent 机制（Subagent）

上下文隔离。

当一个对话涉及上百个文件时，上下文窗口（Context Window）会迅速爆炸。S04 教会主 Agent “雇佣小弟”。

\* 技术路径： 主 Agent 可以开启一个全新的会话（新的 Message List），让子 Agent 去处理特定的子任务（如 “查阅并总结该库的所有 API”）。

\* 优势： 子任务产生的冗余日志不会污染主会话，且每个子 Agent 可以拥有不同的 System Prompt。

## S05：技能按需加载（Skill Loading）

Token 经济学。

你不能把 50 个工具的所有说明文档都塞进 System Prompt。

\* 方案： 将复杂技能写在 skills/\*.json 中。当 Agent 发现自己不会某个操作时，它会主动调用 load\_skill 工具。

\* 事实依据： 这是一种 “即时上下文填充” 技术，类似于 RAG（检索增强生成），但检索的是 “能力” 而非 “知识”。

## S06：上下文压缩（Context Compact）

战略性遗忘。

为了支持无限时长的对话，必须处理 Context 溢出。

\* 技术实现： 采用一种 “摘要递归” 算法。当 Token 达到阈值（如 128k），系统会自动触发 compact 动作：将早期的聊天记录通过模型总结为几行关键事实，然后丢弃原始消息，仅保留摘要和最近的 10 轮对话。

## S07：任务持久化（Task System）

稳定性工程。

内存是不可靠的。S07 引入了文件级持久化。

\* 方案： 将 Agent 的当前计划、已完成步骤和关键中间变量实时写入 task.jsonl。

\* 价值： 即便脚本崩溃或模型 API 报错，重启后 Agent 能通过读取文件瞬间找回进度。这让 Agent 具备了 “跨进程生命”。

## S08：后台异步任务（Background Tasks）

非阻塞交互。

在现实场景中，运行测试集可能需要十分钟。

\* 技术实现： 使用 Python 的 threading 或 asyncio。Agent 发起一个任务后，会得到一个 task\_id，然后主循环继续。

\* 心智模型： 模拟程序员的行为 ——“我先跑着测试，你（用户）可以继续让我改别的代码，跑完我再弹窗通知”。

## S09-S10：协作协议（Agent Teams & Protocols）

分布式治理。

从单打独斗转向 “Agent 团队”。

\* 技术细节： 引入类似 Actor 模型的 Mailbox（邮箱）机制。Agent A 通过 send\_message (agent\_b, task) 进行通信。

\* 协议层（S10）： 引入有限状态机（FSM）。一个任务必须经过 “申请 - 审批 - 执行 - 确认” 的闭环。通过 request\_id 追踪每一次跨 Agent 的请求，解决了多模型协作时的时序混乱问题。

## S11：自治 Agent 团队（Autonomous Agents）

去中心化架构。

这是 Agent 进化的最终形态之一。

\* 实现模式： 任务池（Task Pool）模式。不再由主 Agent 强行分配，而是由一堆功能 Agent（测试专家、代码专家、重构专家）轮询任务队列。谁的匹配度高，谁就认领（Claim）任务。

## S12：环境隔离与 Worktree（Task Isolation）

物理级安全与并行。

这是 Claude Code 最硬核的特性之一，S12 完整复现了它。

\* 技术事实： 传统的 Agent 在当前目录下改代码，一旦改坏了很难回滚。

\* 方案： 利用 git worktree。Agent 在接收到任务后，自动创建一个独立的物理目录副本。

\* 优势： 多个 Agent 可以并行处理不同分支的任务，互不干扰。这在处理大型单体仓库（Monorepo）时是救命的特性。

## 第三部分：实战进阶 —— 如何深度压榨该项目？

## 方法一：快速体感法（适合想先看效果的）

如果你想立刻看到这些 Agent 是怎么 “动起来” 的，直接跑示例代码是最快的：

\* 克隆仓库：

\* 配置环境（核心）：

```bash
pip install -r requirements.txtcp .env.example .env
编辑 .env，填入 ANTHROPIC_API_KEY（推荐）或 OpenAI 的 Key
```

\* 运行 S01 或 S11：

```bash
看最小循环python agents/s01_agent_loop.py# 看最强形态python agents/s11_autonomous_agents.py
```

## 方法二：可视化进阶法（强烈推荐）

这个项目最牛的地方在于它自带了一个 Web 学习平台。如果你直接看 Python 代码觉得抽象，先跑这个：

```bash
cd webnpm installnpm run dev
访问 http://localhost:3000
```

在这个平台上，你可以看到每一节对应的 ASCII 架构图。边看前端的可视化演示，边对照 agents/ 目录下的源码，你会瞬间明白模型是如何在不同工具之间跳转的。

## 方法三：深度拆解法（适合想手搓自己框架的）

如果你想真正吸收这些知识，建议你按照以下步骤：

\* 对比 Diff： 拿 s01\_agent\_loop.py 和 s02\_tool\_use.py 做代码 Diff。你会发现增加工具的能力其实只需要改动极少量的注册逻辑。

\* 观察.env.example： 这里列出了所有环境变量。去研究一下模型 ID 是如何影响 Agent 行为的（你会发现 Claude 3.5 在复杂协议下的稳定性确实更高）。

\* 修改 Motto： 尝试修改 docs/ 里的文档或代码里的心智模型，看看如果你给 Agent 换一套 “工作习惯”，它的任务成功率会发生什么变化。

## 第四部分：Agent 架构的三个 “深坑” 与对策

在复刻 Claude Code 的过程中，你会遇到三个该项目已经给出解法的工程痛点：

| 痛点 | 项目给出的解法 | 技术细节 |
| --- | --- | --- |
| 幻觉导致的死循环 | S03 显式规划 | 强制要求模型输出 current\_plan，逻辑不通时由系统拦截。 |
| 长任务导致的上下文丢失 | S07 持久化状态 | 状态不依赖于 messages 列表，而是写入硬盘 JSONL。 |
| 环境破坏不可逆 | S12 Worktree 隔离 | 物理目录隔离，让 Agent 在沙盒中折腾，坏了直接销毁。 |

## 结语：程序员的下一站，是 “Agent 架构师”

learn-claude-code 之所以能火，是因为它戳破了 AI 编程的最后一次泡沫：Agent 不是魔法，而是严谨的软件工程。

当我们把 Agent 拆解为 12 个步骤时，你会发现，所谓的 “智能”，其实是：

\* 30% 的模型推理能力

\* 70% 的工程基础设施（工具、隔离、状态、协作协议）

如果你还在纠结怎么写 Prompt，不如花一个周末，把这个项目的 12 个 Python 脚本逐行敲一遍。当你亲手实现 git worktree 隔离下的多 Agent 协作时，你对未来编程的理解，将领先同行整整一个身位。

这个 GitHub 仓库，就是你通往 “Agent 架构师” 的入场券。

继续滑动看下一个

ITADN 技术智库

向上滑动看下一个

Clip to Feishu Docs