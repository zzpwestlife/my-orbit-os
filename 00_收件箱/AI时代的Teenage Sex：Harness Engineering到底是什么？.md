---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://mp.weixin.qq.com/s/I3kn-KJPMY2naquZg7C-qQ"
created: 2026-04-21
---
## AI 时代的 Teenage Sex：Harness Engineering 到底是什么？

2013 年 1 月，杜克大学教授 Dan Ariely 在推特上写了一段话：

Big data is like teenage sex: everyone talks about it, nobody really knows how to do it, everyone thinks everyone else is doing it, so everyone claims they are doing it.

大数据就像青少年的性生活 —— 每个人都在谈，没人真正知道怎么做，每个人都以为别人在做，所以每个人都说自己在做。

十三年后，我们把 Big Data 替换成 Harness Engineering，依旧成立。

Harness Engineering 这个词从 2025 年底冒头，到 2026 年初已经成了 AI 圈的顶流热词。OpenAI 官方博客写过，Martin Fowler 专门写了篇长文，Medium、Reddit 上更是铺天盖地。但你要是随便抓一个侃侃而谈的人，问他一句 "具体怎么做"，十有八九他会开始甩链接。

这篇文章就是想说清楚这件事。不是帮你成为布道师，而是让你下次听到这个词的时候，能分出谁在做实事，谁在放嘴炮。

从 Prompt Engineering 到 Harness Engineering：造词运动会

AI 行业有个不太好的 “传统”—— 每隔几个月就要发明一个新词，把旧概念重新包装一下，当新发现来卖。

2023 年，Prompt Engineering 横空出世，一时间写 prompt 成了 "工程学科"。有人出书、开课、办峰会，搞得好像掌握了某种咒语就能让 LLM 言听计从。结果不到一年，天花板肉眼可见 ——prompt 写得再花哨，随着模型升级被一一吞噬掉。

2025 年，Context Engineering 登场。逻辑是这样的：prompt 不够用了，因为你没给够上下文。于是给模型塞文档、塞代码库、塞知识图谱，统称 "上下文工程"。听起来高级，但干的活跟以前的 RAG 没有本质区别，只是换了个更好卖课的名字。

2025 年底到 2026 年初，Harness Engineering 接棒。

每一次造词都有一个共同点：旧概念换新衣，本质没变，热度重新炒一轮。

这不是新鲜事。从 "大数据" 到 "数字化转型" 到 "Web3" 到 "元宇宙" 再到 "AI Native"—— 每一轮都遵循同一个剧本：有人造词，有人布道，有人卖课，有人融资。最后大部分人在下个周期到来之前就忘了这个词。

那 Harness Engineering 到底是什么？

先把嘴炮放一边。这个词所指的东西，是有实质的。

最简洁的定义来自 Martin Fowler—— 一个在软件工程领域说话还有点分量的人。

他在 2026 年 4 月写了一篇文章，标题就叫 "Harness engineering for coding agent users"，定义极其简洁：

Agent = Model + Harness

一个 AI Agent 等于模型本身加上 "缰绳"—— 模型之外的一切东西。

用一个不太精确但足够直观的类比：如果模型是一匹马，Harness 就是缰绳、马鞍、马蹄铁、马厩、饲料配方，以及骑手的操控技术。

在 AI Agent 的语境下，Harness 包含几类东西：

- 工具和访问权限 ——Agent 能调用什么工具、读什么文件、连什么数据库
- 约束和边界 ——Agent 不能做什么、一次操作的上限、什么时候必须停下来
- 反馈循环 —— 做完一件事后怎么验证对错、错了怎么自动纠正
- 编排逻辑 —— 多个 Agent 怎么协作、任务怎么分配、结果怎么汇合
- 环境配置 —— 沙箱、CI / CD 集成、代码检查、测试框架

听起来是不是有点熟悉？

没错。如果你是有经验的软件工程师，你可能已经发现了 —— 这些东西在过去几十年里一直存在，只是没被叫作 "Harness Engineering"。

测试驱动开发是反馈循环。持续集成是编排逻辑。代码审查是约束。Lint 工具是传感器。架构决策记录是导航。你以前做的每一件事，都是在给开发者套 "缰绳"—— 只不过那个开发者是人类，AI 时代的开发者则换成了 Coding Agent。

Martin Fowler 在文章里把 Harness 拆解得更精细。他提出了两个维度：

方向维度：

- 前馈（Feedforward）—— 在 Agent 行动之前预防问题，比如规范文档、lint 规则、项目模板
- 反馈（Feedback） —— 在 Agent 行动之后检查问题，比如测试结果、静态分析、代码审查

执行维度：

- 计算型（Computational） —— 确定性的、快速的，lint、类型检查、单元测试，毫秒到秒级完成，结果可靠
- 推理型（Inferential） —— 语义分析、AI 代码审查、"LLM 当裁判"，更慢更贵，结果有不确定性

|  | 前馈（预防） | 反馈（检查） |
| --- | --- | --- |
| 计算型 | LSP、脚本、Codemod | Lint、类型检查、测试覆盖率 |
| 推理型 | AGENTS.md、编码规范、Skill | AI Code Review、LLM as Judge |

坦白说，这套框架是合理的、有用的。如果你在认真做 AI 编程 的工程化落地，这套思路确实能帮你理清问题。

Harness Engineering 的问题不在概念本身，在于这个行业讨论它的方式。

概念是好的，炒作是坏的

这里有一个微妙的分界线。

Harness Engineering 作为一个概念框架 —— 用前馈和反馈来管控 AI Agent 的行为 —— 是合理且有价值的。Martin Fowler 的文章写得清楚、严谨、有结构，是一个资深工程师在认真思考问题。

但 Harness Engineering 作为一个热词被传播的方式，就完全是另一回事了。

你打开 Medium，一搜 "Harness Engineering"，满屏都是这种标题：

- Harness Engineering: What Every AI Engineer Needs to Know in 2026
- Why Harness Engineering Replaced Prompting in 2026
- Harness Engineering: The Skill That Will Define 2026 for Solo Devs

换掉年份和关键词，这些标题跟 2023 年吹 Prompt Engineering 的文章一模一样。连结构都一样 —— 先说旧概念已死，再说新概念是救世主，最后号召你赶紧上车。

这不是在传播知识。这是在制造焦虑。

更荒诞的是，有些文章连定义都给不对。有的把它等同于 prompt engineering 的升级版，有的说成一种新的编程范式，有的干脆定义为 "给 AI Agent 写说明书"。定义的混乱本身就是最好的证据 —— 证明这个领域还没成熟到值得拥有一个专属名词。

回到 Dan Ariely 的类比：大数据最终证明了自己的价值，但那是在炒作泡沫退潮之后。真正做大数据的人从不自称 "大数据专家"—— 他们叫数据工程师、数据科学家、分析师。Harness Engineering 大概率也会走同样的路。概念会被吸收进日常工程实践，热词会褪色，真正有价值的东西会留下来，只是不再需要这个花哨的名字。

为什么 AI 圈这么爱造词？

这个问题值得认真回答。造词不是随机发生的，背后有结构性原因。

第一，产品化速度远超概念化速度。

一个新模型、新工具出来，三个月内成千上万的开发者开始用，但真正理解它在工程学上意味着什么的人，可能只有几十个。这个认知落差制造了巨大的信息需求 —— 所有人都急着要 "正确答案"，于是任何听起来像答案的东西都会被迅速传播。

第二，造词是商业策略。

每一个新术语背后，都站着一批等着卖东西的人。卖课的、卖咨询的、卖工具的、卖订阅的。你需要一个新词来制造 "旧知识已经过时" 的紧迫感，否则谁会为已有的知识付费？Prompt Engineering 的课还没卖完呢，怎么着也得赶在过期之前炒热下一个概念。

第三，技术媒体需要流量。

每一次新词的出现都是流量盛宴。标题里带上热词，点击率直接翻倍。媒体不会等你把概念想清楚了再来报道 —— 它们要的是速度，不是深度。

第四，从众效应。

当你的 Twitter 时间线上、LinkedIn 动态里、技术社区中全是一个新词的时候，你很难不焦虑。"我是不是落后了？"" 我是不是应该学一下？" 这种焦虑不是自然产生的，是被制造的。

这些因素叠加在一起，形成了一个正反馈循环：有人造词，有人传播，有人焦虑，有人付费，更多的人有动力造更多的词。

打破循环的方法只有一个：搞清楚概念本身在说什么，然后自己判断它是不是新东西。

说到底就是软件工程

如果让我用一句话总结 Harness Engineering 的核心洞见：

Coding Agent 不需要新的工程方法论，它需要的是我们把已有的方法论执行得更好。

测试是 Harness。CI / CD 是 Harness。代码审查是 Harness。架构规范是 Harness。Lint 规则是 Harness。文档是 Harness。

这些东西不是新发明的。它们的原理、最佳实践、适用场景，软件工程社区已经积累了五十年。唯一的区别是：以前这些工具面向人类开发者，现在要给 Coding Agent 用，需要调整表达方式和自动化程度。

以前你写一份编码规范，面向的是人 —— 人有常识，有判断力，能读出言外之意。现在你要把同样的规范喂给 Coding Agent，就得写得更精确、更结构化、更少歧义。这不是一种新的工程学科，这是同一门学科的新场景。

以前 Code Review 是人看人的代码，现在可以是 AI 看 AI 的代码。但审查的标准没变：代码是否可读、是否符合架构约束、是否有测试覆盖、是否引入了不必要的复杂度。变的只是执行者，不是标准。

Martin Fowler 把这说得很到位：一个优秀的 Harness 不应该试图完全替代人类监督，而是把人类的注意力引导到最重要的地方。翻译成大白话 —— 工具能自动检查的就让工具查，人只看那些工具看不出来的问题。

这不是革命性洞察。这是工程常识。

但工程常识不卖课，不上热搜，拿不到融资。

所以你需要一个新名字。

Teenage Sex 的结局

大数据的故事后来怎么样了？

泡沫退了，热词冷了。但数据本身留下来了，而且变得比任何时候都重要。只是不再有人用 "大数据" 这个词 —— 它变成了基础设施，像水和电一样，存在但不被注意。

Harness Engineering 大概率也是这个结局。

三年后大概率没人会再提 “哈妮丝” 这个词，但 Martin Fowler 描述的那些东西 —— 前馈控制、反馈循环、计算型传感器、推理型审查 —— 会被融入每一个 Coding Agent 的开发流程，变成默认配置，变成不需要专门命名的基础操作。

到那时候，真正有价值的问题不是 "Harness Engineering 是什么"，而是：你的 Coding Agent 错误率是多少？测试覆盖率够不够？反馈循环有多快？代码审查有效率多高？

这些问题不需要新名词。它们需要的是认真回答。

而那些今天忙着上直播、画 PPT、出课程的人 —— 他们中的大多数，在下一个热词到来的时候，会毫不犹豫地换顶帽子，继续同样的表演。

旧酒装新瓶不可怕，可怕的是你真信了这是新酒。

参考来源：

- Dan Ariely 原始推文
- Martin Fowler: Harness engineering for coding agent users
- OpenAI: Harness Engineering
- Anthropic: Harness Design for Long-Running Application Development
- MindStudio: What Is Harness Engineering?
- Neo4j: Context Engineering vs Prompt Engineering
- Milvus: Harness Engineering: The Execution Layer AI Agents Actually Need
- Medium: Harness Engineering - The Oldest New Idea in AI

