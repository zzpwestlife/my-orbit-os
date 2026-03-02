---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://mp.weixin.qq.com/s/4oZlOw1qHD6AMHldTl_fKA"
created: 2026-03-02
archived: 2026-03-02
archive_reason: CLAUDE.md 编写最佳实践指南 - 已归档为参考资料
---
AK *2026 年 2 月 25 日 23:26*

## 编写优质的 CLAUDE.md 文件

*注意：这篇文章同样适用于 `AGENTS.md`* ，这是面向 OpenCode、Zed、Cursor 和 Codex 等 agents 和 harness 的开源版 `CLAUDE.md` 。

## 原则：LLM 基本上是无状态的

LLM 是无状态函数。在推理时，它们的权重已经被冻结，所以它们不会随着时间学习。模型对你的代码库唯一了解的就是你输入给它的 token。

同样，像 Claude Code 这样的 coding agent harness 通常需要你显式管理 agents 的记忆。默认情况下， `CLAUDE.md` （或 `AGENTS.md` ）是进入 *你与 agent 的每一次对话* 的唯一文件。

**这有三个重要含义：**

1. 1\. 在开始时，coding 每个会话 agents 对你的代码库一无所知。
2. 2\. 每次启动会话时，必须告诉 agent 任何重要的信息。
3. 3\. `CLAUDE.md` 是完成这件事的首选方式。

## CLAUDE.md 将 Claude 引入你的代码库

由于在每个会话开始时 Claude 对你的代码库一无所知，你应该使用 `CLAUDE.md` 将 Claude 引入你的代码库。从高层次来看，这意味着它应该涵盖：

- • **什么** ：告诉 Claude 你的技术栈、项目结构。给 Claude 一张代码库的地图。这在 monorepo 中尤其重要！告诉 Claude 有哪些应用、哪些共享包，以及它们的用途，这样它就知道在哪里查找东西。
- • **为什么** ：告诉 Claude 项目的 *目的* 以及仓库中一切的作用。项目的不同部分有什么目的和功能？
- • **怎么做** ：告诉 Claude 应该如何在这个项目上工作。例如，你使用 `bun` 而不是 `node` ？你想包含它需要的所有信息，以便实际在这个项目上做有意义的工作。Claude 如何验证它的更改？如何运行测试、类型检查和编译步骤？

但重要的是方式！不要试图把 Claude 可能需要运行的每一条命令都塞进 `CLAUDE.md` 文件 —— 否则你会得到次优结果。

## Claude 经常忽略 CLAUDE.md

无论你使用哪个模型，你可能会注意到 Claude 经常忽略你的 `CLAUDE.md` 文件内容。

你可以通过在 claude code CLI 和 Anthropic API 之间放置一个日志代理来自己调查这个问题，使用 `ANTHROPIC_BASE_URL` 。Claude Code 会将以下系统提醒与你的 `CLAUDE.md` 文件一起注入到用户消息中：

`<system-reminder>       IMPORTANT: this context may or may not be relevant to your tasks.        You should not respond to this context unless it is highly relevant to your task. </system-reminder>`

因此，如果 Claude 决定当前任务不相关，它就会忽略 `CLAUDE.md` 的内容。文件中包含的与当前任务不 *普遍适用* 的信息越多，Claude 忽略文件中指令的可能性就越大。

*为什么 Anthropic 要这样做？* 很难确切说，但我们可以推测一下。我们看到的大多数 `CLAUDE.md` 文件都包含了许多 *并非广泛适用* 的指令。许多用户把文件当作添加 "热修复" 的方式来使用，追加了很多不一定普遍适用的指令。

我们只能假设 Claude Code 团队发现，告诉 Claude 忽略那些不良指令后，harness 实际上产生了更好的结果。

## 创建优质的 CLAUDE.md 文件

以下部分提供了如何遵循上下文工程最佳实践编写优质 `CLAUDE.md` 文件的大量建议。

*你的情况可能不同* 。并非所有这些规则对每个设置都是最优的。和任何事情一样，一旦你理解了以下两点，就可以随意打破规则：

1. 1\. 什么时候以及为什么打破规则是可以的
2. 2\. 你有充分的理由这样做

### 少即是多（指令）

你可能会试图把 Claude 可能需要运行的每一条命令，以及你的代码标准和风格指南都塞进 `CLAUDE.md` 。 **我们不建议这样做。**

虽然这个话题还没有被非常严谨地研究，但一些研究已经表明：

1. 1\. \*\* 前沿思维模型可以一致地遵循约 150-200 条指令。\*\* 较小的模型能关注的指令比大模型少，非思维模型能关注的指令比思维模型少。
2. 2\. \*\* 较小的模型变差得更快、更严重。\*\* 具体来说，较小的模型在指令数量增加时会表现出指数级的指令遵循性能衰减，而较大的前沿思维模型表现出线性衰减（见下图）。因此，我们建议不要在多步骤任务或复杂实现计划中使用较小的模型。
3. 3\. **LLM 偏向于位于提示边缘的指令** ：最开头（Claude Code 系统消息和 `CLAUDE.md` ），以及最后（最新的用户消息）
4. 4\. **随着指令数量增加，指令遵循质量均匀下降。 **这意味着当你给 LLM 更多指令时，它不仅仅是忽略较新的（"文件中更靠后"）指令 —— 它开始** 均匀地忽略所有指令**

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

我们对 Claude Code harness 的分析表明， **Claude Code 的系统提示包含约 50 条独立指令** 。根据你使用的模型，这已经是你 agent 能可靠遵循的近三分之一指令 —— 而且这还没算上规则、插件、技能或用户消息。

这意味着你的 `CLAUDE.md` 文件应该包含尽可能少的指令 —— 理想情况下只有那些普遍适用于你任务的指令。

### CLAUDE.md 文件长度和适用性

在其他条件相同的情况下， **当 LLM 的上下文窗口充满专注、相关的上下文时，它在任务上的表现会更好** ，包括示例、相关文件、工具调用和工具结果 —— 相比于上下文窗口中有大量不相关的情况。

由于 `CLAUDE.md` 会进入 *每一个会话* ，你应该确保其内容尽可能普遍适用。

例如，避免包含关于如何构建新数据库模式的指令 —— 当你做其他不相关的事情时，这不会有什么帮助，反而会分散模型的注意力！

在长度方面，"少即是多" 原则同样适用。虽然 Anthropic 没有官方建议你的 `CLAUDE.md` 文件应该多长，但普遍共识是少于 300 行最好，越短越好。

在 HumanLayer，我们的根 `CLAUDE.md` 文件 *不到六十行* 。

### 渐进式披露

编写一份涵盖你想让 Claude 知道的一切的简洁 `CLAUDE.md` 文件可能很有挑战性，尤其是在较大的项目中。

为此，我们可以利用 **渐进式披露** 原则，确保 Claude 只在需要时看到任务或项目特定的指令。

我们建议不要在 `CLAUDE.md` 文件中包含关于构建项目、运行测试、代码约定或其他重要上下文的所有不同指令，而是将任务特定的指令保存在项目中的 *独立 markdown 文件* 中，文件名要不言自明。

例如：

```
agent_docs/
  |- building_the_project.md
  |- running_tests.md
  |- code_conventions.md
  |- service_architecture.md
  |- database_schema.md
  |- service_communication_patterns.md
```

然后，在你的 `CLAUDE.md` 文件中，你可以包含这些文件的列表，并对每个文件做简要描述，指示 Claude 决定哪些（如果有的话）是相关的，并在开始工作之前读取它们。或者，要求 Claude 先向你展示它想要读取的文件，征得你的同意后再读取。

**优先使用指针而非副本** 。如果可能，不要在这些文件中包含代码片段 —— 它们会很快过时。相反，包含 `file:line` 引用来指向权威的上下文。

从概念上讲，这非常类似于 Claude Skills 的 intended 工作方式，尽管技能更侧重于工具使用而非指令。

### Claude 不是（昂贵的）linter

我们在 `CLAUDE.md` 文件中最常看到的内容之一是代码风格指南。 **永远不要让 LLM 做 linter 的工作** 。与传统 linter 和格式化工具相比，LLM 相当昂贵且 *极其缓慢* 。我们认为你 *应该尽可能使用确定性工具* 。

代码风格指南不可避免地会在你的上下文窗口中添加大量指令和大部分无关的代码片段，降低你的 LLM 性能和指令遵循能力，并消耗你的上下文窗口。

**LLM 是上下文学习者** ！如果你的代码遵循一定的风格指南或模式，你应该会发现，只要有几次代码库搜索（或一份好的研究文档！），你的 agent 就会倾向于遵循现有的代码模式和约定，而无需告诉它。

如果你非常坚持这一点，你甚至可以考虑设置一个 Claude Code `Stop` hook，运行你的格式化工具和 linter，并向 Claude 展示错误让它修复。不要让 Claude 自己发现格式问题。

**额外加分** ：使用可以自动修复问题的 linter（我们喜欢 Biome），仔细调整规则以确定什么可以安全地自动修复，从而获得最大（安全）覆盖。

你也可以创建一个斜杠命令，包含你的代码指南，并指向版本控制中的更改，或你的 `git status` ，或类似的内容。这样，你可以将实现和格式分开处理。 **你会发现两者一起使用效果更好** 。

### 不要使用 /init 或自动生成你的 CLAUDE.md

Claude Code 和其他带有 OpenCode 的 harness 都提供了自动生成 `CLAUDE.md` 文件（或 `AGENTS.md` ）的方法。

由于 `CLAUDE.md` 会进入与 Claude code 的 *每一个会话* ，它是 harness 的 **最高杠杆点** 之一 —— 无论你如何使用它，结果好坏取决于此。

糟糕的代码行就是糟糕的代码行。糟糕的实现计划行有可能产生 **很多** 糟糕的代码行。研究中的一行误解系统如何工作有可能导致计划中出现很多糟糕的行，因此结果 **会产生更多** 糟糕的代码行。

但 `CLAUDE.md` 文件影响 **你工作流程的每个阶段** 及其产生的每个产物。因此，我们认为你应该非常仔细地思考进入其中的每一行：

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

  

## 总结

1. 1\. `CLAUDE.md` 用于将 Claude 引入你的代码库。它应该定义你项目的 **为什么** 、 **什么** 和 **怎么做** 。
2. 2\. **少即是多（指令）** 。虽然你不应该省略必要的指令，但你应该在文件中包含尽可能少且合理的指令。
3. 3\. 保持你的 `CLAUDE.md` 内容 **简洁且普遍适用** 。
4. 4\. 使用 **渐进式披露** —— 不要告诉 Claude 所有你可能想让它知道的信息。相反，告诉它 *如何查找* 重要信息，这样它就可以在需要时找到并使用它，避免膨胀你的上下文窗口或指令数量。
5. 5\. Claude 不是 linter。使用 linter 和代码格式化工具，并根据需要使用其他功能如 Hooks 和 斜杠命令。
6. 6\. **`CLAUDE.md` 是 harness 的最高杠杆点** ，所以避免自动生成它。你应该仔细设计其内容以获得最佳结果。

  

继续滑动看下一个

AKclown

向上滑动看下一个

Clip to Feishu Docs