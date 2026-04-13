# Harness Engineering是什么？和提示词工程和上下文工程有什么关系？

## 视频来源

https://www.bilibili.com/video/BV1dpQTB3EXg?p=1

## 大纲

- Harness Engineering的概念引入与核心问题(00:00:00)
    - 概念提出与现象观察(00:00:00)
        - Harness Engineering的起源与流行(00:00:00)
            - OpenAI在2026年博客中提出(00:00:00)
            - AI圈快速跟风但概念模糊(00:00:00)
        - 视频的核心目标与内容定位(00:00:00)
            - 厘清Harness Engineering、Prompt Engineering、上下文工程的关系(00:00:00)
            - 揭示AI Agent开发的本质(00:00:00)
    - Prompt Engineering（提示词工程）详解(00:00:33)
        - 大模型的基本工作原理(00:00:40)
            - 大模型服务的构成：参数文件、API、应用界面(00:00:51)
            - 核心任务：基于输入预测下一个词(00:01:00)
        - 提示词的必要性与构成(00:01:06)
            - 宽泛指令导致发散性回答(00:01:06)
            - 举例：补充指令以获得完整代码(00:01:15)
            - 提示词的组成部分：角色、背景、历史、文档、格式限制(00:01:24)
        - 提示词工程的定义与作用(00:01:31)
            - 定义：有意识地调整提示词以稳定输出(00:01:31)
            - 作用：解决大模型无引导乱说话的问题(00:01:31)
            - 原则：提示词越长越细，回答越准(00:01:48)
- 上下文工程与Harness Engineering的构建(00:01:52)
    - 从提示词到上下文工程(00:01:52)
        - 上下文的概念与限制(00:01:52)
            - 上下文包含提示词及其他所有信息(00:01:52)
            - 上下文窗口的限制与上下文腐化问题(00:02:04)
        - 上下文工程的定义与目标(00:02:30)
            - 目标：在合适时机将合适内容塞入有限上下文(00:02:30)
            - 定义：动态管理大模型上下文的技术(00:02:35)
            - 与提示词工程的关系：后者是前者的子集(00:02:35)
    - 上下文工程的技术实现(00:02:47)
        - 核心三步骤：召回、压缩、组装(00:02:56)
            - 召回：从各种来源寻找相关信息(00:03:01)
            - 压缩：通过总结等方式减少信息体积(00:03:26)
            - 组装：按特定结构和顺序组织信息以影响模型输出(00:03:31)
        - 效果差异与工具举例(00:03:34)
            - 不同工具的上下文工程策略导致效果差异(00:03:34)
            - 举例：CloudCode的开源与计划讲解(00:03:49)
    - 迈向AI Agent：执行层与循环(00:03:57)
        - 为模型添加执行能力(00:03:57)
            - 添加Bash沙箱、文件系统、MCP等工具能力(00:04:06)
            - 构成执行层，使模型能操作外部工具(00:04:06)
        - ReAct模式与AI Agent的本质(00:04:19)
            - 流程：组装上下文 -> 模型思考 -> 程序执行 -> 反馈循环(00:04:19)
            - 定义：一边思考一边行动的循环即ReAct(00:04:40)
            - 本质：能执行任务的程序，即一个`for`循环(00:04:40)
- Harness Engineering的完整架构与落地(00:04:48)
    - 解决长循环问题：记忆层与反馈层(00:04:48)
        - 长循环带来的挑战(00:04:48)
            - 上下文膨胀与腐化风险(00:04:48)
            - 目标约束被冲淡，理解偏移(00:04:58)
        - 引入记忆层：固化核心信息(00:05:01)
            - 解决方案：在上下文中保持可复用核心信息(00:05:01)
            - 实现方式：规则文件（如cloud.md, .rs文件）(00:05:14)
            - 注入机制：作为系统提示词自动加载(00:05:29)
            - 优化策略：文件拆分与按需加载路由(00:05:41)
        - 形成反馈层：实现自动修复(00:05:55)
            - 机制：将测试输出和报错加入上下文，驱动下一轮修复(00:06:01)
            - 定义：通过校验结果回溯错误的能力层(00:06:01)
    - 全局规划：编排层与Harness Engineering定义(00:06:16)
        - 引入编排层避免跑偏(00:06:16)
            - 问题：缺乏全局规划易导致死循环或偏离(00:06:16)
            - 解决方案：任务拆解与全流程管控(00:06:31)
            - 定义：以全局规划为核心的拆解与管控能力层(00:06:31)
        - Harness Engineering的完整定义与公式(00:06:41)
            - 定义：由编排、执行、反馈、记忆层组成的工程外壳(00:06:41)
            - 与大模型的关系：模型越强，外壳可越薄，但必须有(00:06:41)
            - 核心公式：Agent = 大模型 + Harness Engineering(00:06:49)
    - Harness Engineering的落地实践(00:07:01)
        - 轻量级落地：以CloudCode为例(00:07:06)
            - 原生支持四层能力(00:07:06)
            - 核心操作：在cloud.md中定义背景、目标、禁令、测试步骤(00:07:12)
        - 进阶落地：使用插件与DD开发模式(00:07:20)
            - 插件举例：spec-kit扩展(00:07:29)
            - 工作流程：生成约束 -> 制定计划 -> 拆解任务 -> 修改测试(00:07:34)
            - 开发模式：DD (Development)，即Harness Engineering的落地(00:07:48)
        - 对程序员工作的影响与总结(00:07:53)
            - 工作内容转变：从写代码到定义规则和Skills(00:07:58)
            - 幽默比喻：前同事变成Skill陪伴你(00:08:06)
            - 三大工程总结(00:08:16)
                - 提示词工程：明确需求与标准(00:08:16)
                - 上下文工程：注入精准上下文(00:08:16)
                - Harness Engineering：保障规范执行与最终交付(00:08:16)

## 总结

## 文章分析专家

### 一句话总结
- 本文深入解析了 **Harness Engineering**（驾驭工程）的概念及其与提示词工程、上下文工程的关系，揭示了AI Agent开发的核心逻辑。

### 核心要点
- **Harness Engineering** 是包裹大模型的工程外壳，包含编排层、执行层、反馈层和记忆层，确保AI Agent按规范执行任务。
- **提示词工程** 通过设计提示词约束大模型输出，解决模型“乱说话”问题。
- **上下文工程** 动态管理大模型的上下文信息，解决上下文窗口限制和腐化问题。
- AI Agent的本质是一个循环（ReAct），结合提示词工程、上下文工程和外部工具执行任务。
- 程序员未来的主战场将转向规则和Skills的编写，而非传统编码。

### 深度问答
1. **Harness Engineering 的核心组成部分是什么**？
   - 包括编排层（任务拆解与管控）、执行层（工具操作）、反馈层（结果校验与修复）和记忆层（核心信息固定）。

2. **提示词工程和上下文工程的区别是什么**？
   - 提示词工程聚焦于设计输入约束，而上下文工程解决信息的动态组织与压缩问题。

3. **为什么上下文窗口限制会影响AI Agent的表现**？
   - 窗口满会导致关键信息丢失（上下文腐化），模型输出变得不一致或偏离目标。

4. **AI Agent的“ReAct”循环如何工作**？
   - 模型思考→外部程序执行→结果反馈到上下文→下一轮推理，形成闭环。

5. **程序员如何适应Harness Engineering的变革**？
   - 转向编写规则文件（如`cloud.md`）、设计Skills和任务拆解，而非直接编码。

### 关键词标签
- Harness Engineering  
- AI Agent  
- 提示词工程  
- 上下文工程  
- ReAct  

### 目标受众
1. **AI开发者**：需掌握工程化封装大模型的技术。  
2. **程序员**：转型为规则和Skills设计者。  
3. **技术管理者**：理解AI驱动的开发流程变革。  
4. **AI研究者**：探索模型与工程层的协同优化。  

### 术语解释
- **上下文窗口 (Context Window)**：大模型单次处理的最大文本长度限制。  
- **RAG (Retrieval-Augmented Generation)**：通过检索外部信息增强模型输出的技术。  
- **ReAct**：结合推理（Reasoning）和行动（Action）的AI Agent循环框架。  
- **Skills**：AI Agent可调用的一组外部工具或功能模块。  
- **上下文腐化 (Context Corruption)**：因信息丢失导致的模型输出偏差。

![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/b12ee7ef-16b9-43cc-a960-1f349f671d2a.webp)

**Harness Engineering**是什么？和**提示词工程**、**上下文工程** 有什么关系？

2026年，OpenAI 在一篇博客文章中提到了 **Harness Engineering**（驾驭工程）之后，它就在 AI 圈里快速火了起来。很多人根本不知道它到底是什么，就开始跟风吹捧。这在“三天一重磅，五天一炸裂”的 AI 圈里虽然离谱，但也合理。

那它到底是什么？和这两年很火的 **提示词工程**、**上下文工程**又是什么关系？全网资料参差不齐，如有差异，以我为准。今天就把这些概念串起来讲透。看完你就会知道**AI Agent** 的开发本质是在做什么。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/da104c08-64a4-4961-8282-d1fbaea85fe7.webp)

为什么同样的模型换个 **Prompt Engineering**效果会差这么多？有了**AI** 程序员就不写代码是真的吗？



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/5ac182f6-2adf-494d-9dbf-c0af0c16561e.webp)

怎么做到的？



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/6a729b40-5f76-43f1-8f9f-eb41724440db.webp)

看之前你点赞了吗？关注了吗？谢谢。**Prompt Engineering**把**PTcloud**的外壳拨开，里面的大模型，也就是**LLM** 本质就是一



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/2f0dd0a0-9d8d-4a85-aa50-c80c4e7da9f9.webp)

将磁盘上的超大参数文件加载到显卡内存里，配上 **HTTP接口**就成了**大模型 API** 服务。给它加个聊天界面就变成了聊天应用。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/2da9ca8e-f862-4da3-8020-d3f45f78ed40.webp)

AI加个代码编辑器就成了 **大模型** 做的事情很简单，就是基于当前输入的内容，预测下一个字词大概率会是什么。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e8507bf5-e82d-4a5f-8dd2-8b13a3f2d0fd.webp)

它本质上只是在猜你想要什么。所以如果你给它输入的指令太宽泛，那它预测的答案就会非常发散。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/63720c88-447f-4c59-8643-3b282a913d5d.webp)

比如你丢给他一段代码，说加个**排序**，他可能只回你排序的那部分怎么写。你得补一句：给我完整函数代码，不要乱改我的代码。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/9f5e693e-6a65-4e33-95b0-38c351d91560.webp)

它给的结果才会更符合要求。能加的内容有很多，比如 **角色设定**、**背景**、**历史对话**、**参考文档**、**限制输出格式**。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/4013c838-f7e8-41e7-b588-506ecb7e97e5.webp)

这些约束构成了所谓的 **提示词**。而这种有意识的调整和设计提示词，让模型稳定地朝着你预期的内容和格式输出的技术手段，就是所谓的**提示词工程**。它解决的是**大模型** 无引导乱说话的问题。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/93fef800-9dfa-44a2-9f5a-00f6cdc1141e.webp)

**Prompt Engineering** 提示词写得越长越仔细，模型知道的就越多，回答就越准。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/4a96f988-899f-4889-be06-eb895c2c1cae.webp)

反过来，同理 **大模型**回答不准，那大概率是因为知道的不够多。于是大家很自然会不断往大模型里塞各种资料。这些打包到一起发给大模型的所有信息就叫**上下文**，提示词只是上下文的一部分。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e8b22fff-cd9e-47e5-ab42-89e3e7057c7d.webp)

但 **大模型**再强，一次性能处理的**上下文** 也有最大限制。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/da9f34ab-e581-4dcc-880c-c22269812de3.webp)

这个限制叫 **上下文窗口**，在**AI大模型** 应用里，多对话几轮就很容易将上下文窗口打满，于是就需要通过一些策略来解决。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/62586833-90e8-404c-959d-6f4e6dcfb3ea.webp)

略去压缩或丢弃部分信息。在这个过程中，不可避免会丢失关键信息，从而破坏上下文的完整性和准确性。这类问题被统称为 **上下文腐化**，效果上就是模型开始记不住，回答前后不一致。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/16daac81-5a9a-4b9b-a5e0-922b8823022d.webp)

**上下文窗口**就这么大，于是问题就变成了：怎么才能在合适的时候将合适的内容塞入到有限的上下文中。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/6cc7b561-35a2-4f71-86e7-b83071e42e58.webp)

于是衍生了一套负责动态管理 **大模型****上下文**的技术，也就是所谓的**上下文工程****。提示词**是上下文的一部分，自然**提示词工程** 其实也是。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e0b9df19-1405-4a28-a41e-bffe581cc726.webp)

是 **上下文工程**的一部分，它一般通过外部程序来实现。比如**Skills**这类**aiagent**，注意这不是广。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/9a672ebc-f0d7-490c-88c6-6268a7031fcd.webp)

每一家的技术实现都有差异，但总的来说可以总结为三个步骤：**召回**、**压缩**和**组装**。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/9db08a5a-b1b8-48e5-8d50-720993ab265a.webp)

第一步是 **召回**，说白了就是找信息。这些信息可以来自外部新闻、过去聊天记录、当前代码环境或程序运行报错等。总之，就是从里面找出最相关的内容。

这里面涉及到一些 **RAG** 等技术，随便拿出一个都能单开一个视频。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/ff80f6c6-4b8e-4d65-bece-102a302484e9.webp)

这里。如果看到这里还没睡着，弹幕扣个0。信息很多，**上下文窗口**有限，所以需要将信息变小。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/0a0d879b-7b4e-44cd-8c70-151af80f0be1.webp)

于是引入第二步 **压缩**，比如将信息分开发给**大模型** 做总结，之后就是组装。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/8b92b06b-22b9-4aaa-ac8a-ea5e5d8510c0.webp)

因为**信息放置的位置和顺序**会直接影响模型的理解和输出。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/c2dee33c-0c2e-4ea6-b154-16004d56859e.webp)

比如越靠后越容易被模型关注。所以我们需要通过一定的结构重新组装内容，这样进入模型的 **上下文** 更精简、更相关，输出也会更稳定、更准确。

不同AI工具的 **上下文工程** 策略不同，所以你会发现，就算用的是同一个模型，不同AI工具的执行效果也会有差异。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/a2ba0116-f58d-4f04-8a47-4500be21fc36.webp)

**CloudCode**最近也被开源了，正好可以单开一期讲下它的**上下文工程** 是怎么做的。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/0b36233b-9755-45d4-b2e6-8f5747a67ed1.webp)

看到这里还在坚持的弹幕扣个一。**Harness Engineering**和**提示词工程**解决了**大模型** 无引导乱说话的问题。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/22b71f4e-baa5-43a3-bfb4-d41567ad7004.webp)

**上下文工程**解决的是上下文的组织问题。模型是更聪明了，但它只能聊天，没法帮我们干活。于是我们可以给**大模型**加入**Bash**沙箱、文件系统、**MCP** 这些能力。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/a1044d76-9805-41df-86c9-4bde91416ff9.webp)

让它能像人一样操作外部工具，读写代码文件、执行命令、做测试。它们共同构成了执行层，将它们串成一个流程，在外部套一层循环。于是我们就可以通过 **提示词工程**和**上下文工程** 组装上下文。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e9888d15-d697-45de-8de3-f12c3ebd96b4.webp)

发给 **大模型**，大模型负责思考；外部程序负责执行。执行过程中得到的报错等信息，再加到**上下文** 里继续推理和执行。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/df3564a7-378f-420f-9c3a-78cefd5a36a4.webp)

这套一边思考一边行动的循环，就是所谓的 **ReAct**。而这个能通过聊天帮你执行任务的程序，就是所谓的**aiagent**。它的本质就是一个 `for` 循环。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/6146ce55-963f-45a2-bc8b-c3581c4ded65.webp)

只要这个循环一长，**上下文**就一定会膨胀。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/a75610af-2fa9-47cd-b9d3-8ff6bcacdbfc.webp)

**上下文工程**做得再好，也可能会腐化。随着他看过的文件越来越多，拿到的信息越来越杂。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/beb8f689-d1e1-465b-a3aa-725aca6311b3.webp)

前面定好的 **目标约束**，后面可能慢。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/193e9b50-e4cf-426a-98b8-1e3008ac9915.webp)

慢就被冲淡了，理解也会越来越偏，怎么办呢？很简单，只要我们可以保证每次给 **大模型**的**上下文** 中都包含一些可复用的核心信息，比如项目目标、技术栈、需求背景、代码风格、禁止事项等。只要保证这部分一直在，那大模型就能在大框架约束下减少理解偏移。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/6647d036-0e45-400b-b82e-294cdd009c08.webp)

这些核心信息可以单独写成文件固定在代码仓库里，比如 **CloudCode** 用 `cloud.md` 或 `tree`，也会有各自的 `rs` 文件。他们暂时没有统一的名字，我暂且这样命名。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/75175977-ee69-45e8-8139-47ee3efc7339.webp)

规则文件会在调用 **大模型**的时候作为系统**提示词** 自动注入上下文。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/037604ab-0466-4f82-8a27-166eaaae0c3a.webp)

规则文件写多了也会变长，所以



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/626dc2ee-3501-49bf-9ed0-0af9a3b734a3.webp)

**上下文**也会很长，那就拆成几份更短的文件，再加一个简单的路由。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/6cb5ffd9-38ed-4d62-8103-d1de7d0047a8.webp)

比如背景就读 **bgmd**，技术栈就看**stackmd**。一般情况下只需要加载文件地址路径，真正需要的时候再加载文件的全部内容，将它们跟**提示词工程**和**上下文工程** 配合在一起，形成记忆层。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/5215005e-e86d-426d-942b-edd8ec44ee80.webp)

有了 **记忆层**和**执行层**的配合**，Agent** 就能不停写代码。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/27d72b36-125a-4723-92f6-eb73c8373720.webp)

在单元测试过程中发现执行有问题时，还可以将测试输出和报错加入到 **上下文**里，这样就可以驱动**Agent**在下一轮循环中自动做修复。这套通过校验结果回溯错误来实现自动修复问题的能力形成了**反馈层**。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/f5a12a72-8fcd-4e9f-adc3-04b150330b8a.webp)

但 **agent**的循环如果缺乏**全局规划** 和清晰的结束目标，依然很容易跑偏，甚至陷入无效死循环。

我们还可以将大任务拆解为有明确执行标准的多个子任务，按规划驱动 **agent**分布执行。这种以**全局规划** 为核心的方式能有效避免偏离。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/10abc5b4-f81b-4b3b-8684-8d4ee2b6666b.webp)

为核心对任务做 **拆解与全流程管控**的能力形成了编排层。编排层、执行层、反馈层和记忆层这些能力共同组成了一套包裹着**大模型**的工程外壳，它就是**Harness Engineering**（驾驭工程）。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/805a50f2-a2c7-40ee-be07-690541dcb493.webp)

大模型越强，外壳就可以做得越薄。但无论



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/3628a43f-1dc4-41c5-b0c8-c03b1c5817c5.webp)

怎么样，这层外壳都得有，再给个公式：**Agent**=**大模型**+**Harness Engineering**。只要不是大模型的那部分，那都属于**Harness Engineering** 的范畴。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/5a429bb9-f14c-47ad-9ae1-fa7f303532e9.webp)

存量程序员们好好看，好好学，以后它就是我们的 **主战场** 啦。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e8cc5926-d664-44ed-b55f-fb3ef0f20bbf.webp)

那增量程序员。怎么说**评论区会给你答案****。Harness Engineering** 怎么落地？



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/656c6992-1692-464e-8b82-80e8090178c1.webp)

概念理解了，那最重要的问题来了，怎么落地？以 **CloudCode** 为例，CloudCode 软件



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/cf1d67c0-f312-4c53-a83d-6bacb9dead55.webp)

本身已经原生支持 **Harness Engineering** 的四层能力，所以最轻量的做法就是在 `cloud.md` 文件里写清楚：

- 项目背景是什么；
- 你希望 **大模型** 做什么；
- 别做什么；
- 做完之后要跑哪些单元测试和 **CI** 执行哪些步骤就行。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/488e4f11-1d93-459b-97c8-817c979374b8.webp)

如果不想自己写这类内容，可以引入一些插件。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/5bc90cf7-fc0e-4c06-977c-226a41602f5f.webp)

件，比如 **spec-kit** 这类扩展，它会根据项目将需求拆成多个阶段，做的事情也很简单。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/f565ac02-7a30-4985-9829-157fc5d44e2d.webp)

首先生成对应的约束文件，明确需求，再制定具体开发计划并拆解任务，最后进行实际修改和测试。每个阶段都可能会更新一次 **CLAUDEmd**。这样每一阶段注入**上下文** 的尽可能都是核心信息。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/c5145690-ad9a-462a-a847-697f5a73d2c6.webp)

这套开发方式也叫 **Development**，简称**DD**，本质上做的事情就是**Harness Engineering** 的落地。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/bf9e9fd1-a328-4da0-be5d-0d080bba6fbf.webp)

但 **Speckit** 整体还是不够强。我相信很快会有更加全面的替代方案出现。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/f9adfcd7-e285-44d9-916e-1295e01bc51f.webp)

有了 **Harness Engineering**之后，程序员的工作内容就从写代码慢慢改为规则和**Skills**。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/37b0b989-3e7a-44f6-94f6-12255b2c950b.webp)

所以有句话是这么说的：你那些拿了N+1的同事，其实从未离开你，他只是变成了 **Skill**，默默陪伴你。你就说暖不暖心吧**。提示词工程**可以让**大模型**



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/f2f71684-c734-46a5-b63d-9d8facae91f4.webp)

模型明白你的具体需求和输出标准。**上下文工程**可以给**大模型**注入精准有效的上下文**。Harness Engineering** 可以让大模型持续按规范执行任务，并最终交付。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/f97bc7ff-e200-4984-b76a-6ea1f3845cc4.webp)

现在大家听懂了吗？好啦，如果你觉得这期视频对你有帮助，记得转发给你那不成器的兄弟。文字版的笔记见评论区。这里是 **小白debug**，我们聚焦一切可能影响人类历史。



![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260412/96bec6ca-bd61-b686-d1b3-b1331a61338f/e94b12ba-a79a-4436-894b-9526848c2cd5.webp)

进程的技术，如果你感兴趣，记得关注，我们下期见。



