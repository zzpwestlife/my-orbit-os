---
type: "inbox"
status: "processed"
---


## 大纲

-    引言与演讲者背景 (00:00:15)
    -   演讲者介绍与主题概述 (00:00:15)
        -   演讲者身份与隶属机构 (00:00:15)
            -   Anthropic AI的Boris Cherny (00:00:15)
            -   《编程TypeScript》作者 (00:00:15)
        -   演讲重点 (00:00:15)
            -   Claude代码实用技巧 (00:00:15)
            -   不涉及深度历史或理论 (00:00:15)
    -   观众互动与设置 (00:00:30)
        -   观众调研 (00:00:30)
            -   询问谁曾使用过Claude代码 (00:00:30)
        -   安装指南 (00:00:48)
            -   安装命令：anthropic-ai/claude-code (00:00:48)
            -   需预先安装Node.js (00:00:57)
-   Claude代码核心概念 (00:01:25)
    -   定义Claude代码 (00:01:25)
        -   新型AI编程助手 (00:01:25)
            -   基于代理的架构 (00:01:25)
            -   支持模块/函数/完整文件操作 (00:01:25)
    -   关键特性与兼容性 (00:01:43)
        -   无缝工具集成 (00:01:43)
            -   兼容现有工具链 (00:01:43)
            -   无需更换IDE (00:01:43)
        -   全环境开发支持 (00:02:08)
            -   适配所有IDE和终端 (00:02:08)
            -   支持本地/SSH/跨操作系统 (00:02:08)
    -   初始设置与入门 (00:02:19)
        -   突破初始空白状态 (00:02:19)
            -   如何开始操作的挑战 (00:02:19)
        -   推荐环境配置 (00:02:19)
            -   终端设置（Shift+Enter换行） (00:02:19)
            -   使用`/theme`切换明暗模式 (00:02:57)
            -   通过`/install-github-app`安装GitHub应用 (00:02:57)
        -   增强输入方式 (00:03:23)
            -   自定义工具权限避免弹窗 (00:03:23)
            -   Mac OS听写功能实现语音输入 (00:03:23)
            -   明确提示词的重要性 (00:03:23)
-   入门：代码库问答法 (00:04:14)
    -   第一步：向代码提问 (00:04:14)
        -   新用户首要建议 (00:04:14)
            -   从代码库问答开始 (00:04:14)
        -   Anthropic内部用例 (00:04:18)
            -   新员工技术入职流程 (00:04:18)
            -   将入职周期从2-3周缩短至2-3天 (00:04:18)
    -   问答隐私与安全 (00:05:05)
        -   本地私有化运行 (00:05:05)
            -   不索引/上传代码 (00:05:05)
            -   代码不用于模型训练 (00:05:05)
        -   零配置要求 (00:05:18)
            -   下载即可运行 (00:05:18)
    -   实际问答示例 (00:05:30)
        -   典型问题类型 (00:05:30)
            -   某段代码的具体用途？ (00:05:30)
            -   如何在代码库实例化对象？ (00:05:30)
            -   超越简单文本搜索 (00:05:30)
        -   查询Git历史与问题 (00:06:00)
            -   解析函数为何需要15个参数 (00:06:00)
            -   通过Git提交追踪参数引入 (00:06:00)
            -   从GitHub issues获取背景 (00:06:00)
            -   自动生成站会周报摘要 (00:06:00)
    -   团队推广建议 (00:06:00)
        -   从基础开始 (00:06:00)
            -   先开展代码问答，而非高级编辑 (00:06:00)
            -   培养有效提示技巧与理解Claude能力边界 (00:06:00)
-   进阶代码编辑 (00:07:52)
    -   第二步：代码修改 (00:07:52)
        -   语言模型的代理能力 (00:07:52)
            -   提供工具后自主决策使用方式 (00:07:52)
            -   内置工具集：文件编辑/Bash执行/文件搜索 (00:07:52)
        -   步骤链式执行优势 (00:08:02)
            -   无需指定具体工具 (00:08:02)
            -   直接声明"完成这个任务" (00:08:02)
    -   最佳实践：头脑风暴与规划 (00:08:02)
        -   大型直接请求的问题 (00:08:02)
            -   要求3000行功能常导致低质结果 (00:08:02)
        -   解决方案：先思考后编码 (00:09:03)
            -   让Claude先构思方案 (00:09:03)
            -   确认计划后再编写代码 (00:09:03)
            -   简单指令："编码前先制定计划" (00:09:12)
    -   高级自动化案例：`commit pushf` (00:09:12)
        -   复杂Git操作标记 (00:09:12)
            -   创建提交/推送分支/发起PR (00:09:12)
            -   Claude检查代码/历史/日志格式 (00:09:12)
            -   通过模型智能实现（非系统提示） (00:09:25)
-   团队工具集成与迭代工作流 (00:09:50)
    -   连接团队工具 (00:09:50)
        -   两大工具类别 (00:09:50)
            -   Bash工具（如自定义CLI） (00:09:50)
                -   向Claude描述工具以研究使用 (00:09:50)
                -   常用工具可跨会话记忆存储 (00:09:50)
            -   MCP（模型上下文协议）工具 (00:10:28)
                -   描述/添加/解释MCP工具 (00:10:28)
                -   Claude可代理调用 (00:10:38)
    -   高效工作流模式 (00:10:38)
        -   模式1：探索-规划-确认（循环） (00:10:38)
        -   自验证模式 (00:10:38)
            -   利用单元测试/测试套件/模拟器反馈 (00:10:38)
            -   支持持续迭代优化 (00:11:30)
    -   三阶段进阶 (00:11:30)
        -   阶段1：教会AI使用工具 (00:11:30)
        -   阶段2：确立正确工作流（编码/构思/计划/迭代） (00:11:30)
        -   阶段3：理解流程以优化指令 (00:11:30)
-   记忆文件提供丰富上下文 (00:12:07)
    -   上下文的重要性 (00:12:07)
        -   更多上下文促成更智能决策 (00:12:07)
        -   工程师具备系统级心智模型 (00:12:07)
    -   上下文提供方法 (00:12:19)
        -   CLAUDE.md文件（主要方式） (00:12:19)
            -   位置：项目根目录或嵌套目录 (00:12:19)
            -   类型：`CLAUDE.md`（共享） vs `CLAUDElocal.md`（个人） (00:12:54)
            -   内容：Bash命令/MCP工具/架构决策记录/关键文件说明 (00:12:54)
            -   保持简洁确保有效性 (00:12:54)
            -   企业级：`/enterpriseroot/CLAUDE.md`全局共享 (00:12:54)
        -   斜杠命令 (00:14:05)
            -   存储于家目录或项目根 (00:14:05)
            -   示例：自动GitHub issue标签工作流 (00:14:33)
        -   提及文件 (00:14:33)
            -   嵌套`.md`文件自动载入上下文 (00:14:33)
    -   上下文配置优化 (00:14:33)
        -   值得投入时间获取性能提升 (00:14:33)
        -   策略：提示优化器/目标受众/加载策略 (00:14:33)
-   分层配置与企业策略 (00:15:41)
    -   层级化集成结构 (00:15:41)
        -   组合CLAUDE.md/MCP等配置 (00:15:41)
        -   层级：项目级/用户全局/团队企业级 (00:15:41)
    -   企业策略文件应用 (00:16:11)
        -   审批与自动化 (00:16:11)
            -   自动批准通用命令（如全员测试命令） (00:16:11)
        -   拦截与安全 (00:16:33)
            -   屏蔽特定URL或保护代码库 (00:16:33)
    -   共享MCP服务器 (00:16:33)
        -   提交`MCP ON`文件触发团队安装 (00:16:33)
    -   初始建议：共享项目上下文 (00:16:33)
        -   一次编写，全员受益（网络效应） (00:17:19)
-   记忆管理与高级快捷方式 (00:17:34)
    -   内置记忆管理工具 (00:17:34)
        -   查看记忆：`/memory`显示所有加载文件 (00:17:34)
        -   编辑记忆：`/s memory`编辑特定文件 (00:17:34)
        -   保存记忆：`#`标记内容至指定记忆库 (00:17:34)
    -   下一步：团队配置 (00:18:06)
        -   一次性设置CLAUDE.md/MCP服务器/工具 (00:18:06)
    -   专业技巧与隐藏快捷方式 (00:18:15)
        -   Shift + Tab：切换"自动接受编辑"模式 (00:19:02)
        -   # 符号：让Claude记忆内容供后续使用 (00:19:02)
        -   ! 符号：进入"bash模式"本地执行命令并纳入上下文 (00:19:02)
        -   ESC键：安全停止当前操作 (00:20:03)
        -   ESC ESC：历史回溯 (00:20:14)
        -   --resume/--continue：恢复先前会话 (00:20:14)
        -   Ctrl键：查看详细输出（匹配云端上下文窗口） (00:20:14)
-   Claude代码SDK与管道 (00:20:40)
    -   SDK介绍 (00:20:40)
        -   通过`claude -dashP`访问 (00:20:40)
        -   近期功能增强 (00:20:40)
    -   CLI工具SDK使用 (00:21:01)
        -   输入：提示词/允许工具/输出格式（JSON/流） (00:21:01)
        -   用例：构建代理应用/CI/CD/事件响应 (00:21:01)
        -   视为智能Unix通用工具 (00:21:52)
    -   管道技术威力 (00:21:52)
        -   无限组合可能性 (00:21:52)
        -   示例：`git status`管道至`jq`/分析S3日志/处理Sentry CLI数据 (00:22:01)
-   高阶使用模式与并行工作 (00:22:38)
    -   资深用户模式 (00:22:38)
        -   维护多SSH会话与TMUX隧道 (00:22:38)
        -   多代码检出或git worktrees实现任务隔离 (00:22:38)
        -   Claude并行工作显著提升效率 (00:22:38)
-   总结与问答环节 (00:23:24)
    -   演讲收尾 (00:23:24)
        -   末页幻灯片过渡至问答 (00:23:24)
    -   观众问答 (00:24:00)
        -   Q1：构建Claude最大挑战？ (00:24:00)
            -   Bash命令安全性的大规模平衡 (00:24:11)
            -   解决方案：只读命令/静态分析/分层权限 (00:24:11)
        -   Q2：多模态能力（图像）？ (00:25:05)
            -   完全多模态支持 (00:25:17)
            -   方式：拖放/文件路径/图像粘贴 (00:25:17)
            -   用例：根据设计稿自动实现 (00:25:17)
        -   Q3：为何选择CLI而非IDE？ (00:25:48)
            -   原因1：用户IDE偏好多元/终端是共同基础 (00:25:54)
            -   原因2：适应后IDE时代的模型演进 (00:25:54)
        -   Q4：ML/AutoML应用？ (00:26:42)
            -   Anthropic约80%技术人员高频使用 (00:26:55)
            -   包含研究员的笔记本工具使用 (00:26:55)
    -   致谢与结束 (00:27:24)

## 总结

## 文章分析专家

### 一句话总结
- 本次演讲详细介绍了**Claude Code**这一AI编程助手的核心功能、使用技巧和高级应用场景，帮助开发者提升编程效率。

### 核心要点
- **Claude Code**是一款基于智能体架构的AI编程助手，专注于构建功能模块和完整文件，而非简单的逐行代码补全。
- 它能无缝集成到各种开发环境（VS Code、Xcode等）和操作系统，支持本地、远程SSH等多种工作场景。
- 问答功能是入门首选，可直接向代码库提问，显著缩短技术入职时间（从2-3周降至2-3天）。
- 提供多种上下文管理方式（MCP文件、CLAUDEmd文件等），通过丰富背景信息提升AI决策质量。
- 支持高级工具链集成（Bash命令、Git操作等），并能通过迭代优化（结合测试反馈）持续改进代码质量。

### 深度问答
- **Claude Code与传统代码补全工具有何不同**？
    - 传统工具专注逐行补全，而Claude Code采用智能体架构，能处理完整功能模块和文件级任务。

- **如何快速上手Claude Code**？
    - 建议从代码库问答功能开始，先熟悉提问方式和AI能力边界，再逐步尝试代码编辑功能。

- **Claude Code如何保证代码安全性**？
    - 通过静态分析、分层权限系统和只读命令限制，确保Bash操作安全，同时平衡效率与风险。

- **为什么选择终端作为主要界面**？
    - 终端是开发者的最大公约数，能兼容各种IDE；同时避免在快速迭代的AI领域过度投资UI。

- **如何利用Claude Code进行机器学习开发**？
    - 支持notebook编辑和运行，可用于AutoML等场景，Anthropic内部80%技术人员日常使用。

### 关键词标签
- AI编程助手
- Claude Code
- 智能体架构
- 开发者工具
- 代码自动化

### 目标受众
- **软件工程师**：提升日常编码效率，快速理解新代码库。
- **技术团队管理者**：优化入职流程，统一团队工具链。
- **AI研究人员**：探索智能编程助手的前沿应用。
- **学生/教育工作者**：学习现代编程实践和工具。
- **开源贡献者**：快速参与新项目，降低贡献门槛。

### 术语解释
- **智能体架构(Agent Architecture)**：一种AI系统设计模式，赋予AI自主使用工具和制定计划的能力。
- **MCP文件**：Claude Code的配置文件，用于提供项目级上下文信息。
- **CLAUDEmd**：Markdown格式的文档，用于存储团队共享的知识和工具说明。
- **Bash模式**：允许Claude Code直接执行终端命令的工作模式。
- **上下文窗口(Context Window)**：AI处理请求时可参考的近期对话和文件内容范围。

![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/82433874-b201-4a7b-a5e8-fda266b0650d.webp)

Speaker1: *00:00:15 - 00:00:21*

大家好，我是**Boris Cherny****，Anthropic AI**的**技术团队成员**，也是《**精通Claude编程**》的创作者。今天我来和大家分享一些使用**Claude Code**的实用技巧和小窍门。

Hello everyone, I'm **Boris Cherny**, a**Member of Technical Staff**here at**Anthropic AI**, and I created**Code w/ Mastering Claude**. I'm here to talk to you about some practical tips and tricks for using**Claude Code**.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/cd07fa43-1641-4c97-84f5-eb516ed7c38a.webp)

Speaker1: *00:00:30 - 00:00:48*

这次内容会非常实用——我不会过多探讨历史或理论部分。在开始之前，请大家快速举手示意：谁之前使用过**Claude Code**？很好，这正是我们希望看到的。至于没有举手的各位，我知道你们...

It's going to be very practical—I'm not going to delve too much into the history or theory. Before we start, can we get a quick show of hands: who has used **Claude Code** before? All right, that's what we like to see. For everyone who didn't raise your hands, I know you're...





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/e2c97354-0fb5-49a1-abb8-ad9347ddf298.webp)

Speaker1: *00:00:48 - 00:00:54*

虽然不该在别人讲话时做这个，但如果你能打开笔记本电脑输入以下命令，它将帮你安装 **anthropic-ai/claude-code**，这样你就能跟上后续的演讲内容。

Not supposed to do this while people are talking, but if you can open your laptop and type this, it will help you install **anthropic-ai/claude-code** so you can follow along for the rest of the talk.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/29ad7fa9-b026-498e-b3af-3a5c0aeeee56.webp)

Speaker1: *00:00:57 - 00:01:22*

你只需要安装Node.js。如果已经安装好了，这段代码应该就能运行。你不必跟着操作，但如果还没安装的话，现在正是安装的好时机，这样你就能跟着一起实践了。

All you need is Node.js. If you have it, this should work. You don't have to follow along, but if you don't have it yet, this is your chance to install it so you can follow along.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/9e308500-44bd-4a84-8eb4-e08535c1a031.webp)

Speaker1: *00:01:25 - 00:01:43*

那么什么是**Claude Code**？Claude Code是一种新型的**AI编程助手**。以往出现过不同世代的编程AI助手——大多数都专注于逐行或少量代码的补全。而Claude Code则截然不同：它采用完全基于智能体的架构，专为构建功能模块、编写完整函数以及创建整个文件而设计。

So what is **Claude Code**? Claude Code is a new kind of**AI assistant**. There have been different generations of AI assistants for coding - most have focused on completing a line at a time or a few lines of code. Claude Code is different: it's fully agent-based, designed for building features, writing entire functions, and creating complete files.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/47030d96-cfe7-44d4-8dfe-a9d5cd3797e9.webp)

Speaker1: *00:01:43 - 00:02:07*

一次性修复所有错误。**Quad代码**最酷的一点在于它能与你所有的工具无缝协作——你无需改变工作流程或更换整套系统就能开始使用它。

无论你用的是**VS Code**、**Xcode**还是**IntelliJ**，总有些用户至死都不愿放弃这些IDE，但他们依然在使用**Quad代码**。

Fixing entire bugs at the same time. What's kind of cool about **Quad code** is it works with all of your tools—you don't have to change your workflow or swap everything to start using it.  

Whatever IDE you use—**VS Code**,**Xcode**, or**IntelliJ**—there are some people who won't pry them from their cold dead hands, but they still use**Quad code**.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/bca5092a-3f7f-4b92-aa93-973e78af4246.webp)

Speaker1: *00:02:08 - 00:02:19*

因为**Claude Code**能与每一款**集成开发环境(IDE)**、每一个终端完美兼容。无论是本地运行、通过远程**SSH**连接，还是跨越不同**操作系统**——在任何开发环境中都能流畅使用。

Because **Claude Code**works with every single**IDE**, every terminal out there. It'll work locally, over remote**SSH**, over**OS**—whatever environment you're in.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/82728d49-53d8-42fd-a25b-05e61b3176bd.webp)

Speaker1: *00:02:19 - 00:02:57*

你可以直接运行它。这是一个通用工具，但如果你过去从未使用过这类自由形式的编程辅助工具，可能会有点难以入手。打开后你只会看到一个输入栏，可能会困惑：*我该用它做什么？该输入什么内容？*

这是个**强力工具**，能用于处理各种任务。正因为它功能强大，我们不会限定你的使用方式——作为工程师，你应该能按自己的需求自由使用。

当你首次打开**Cloud Code**时，我们建议先完成几项环境设置，操作非常简单：

- 运行**终端设置**——这会启用`Shift+Enter`换行功能，无需再输入反斜杠。使用体验会更流畅。

You can run it. It's general purpose, and this is something where if you haven't used these kind of free-form coding assistance in the past, it can be kind of hard to figure out how to get started. You open it up and just see a prompt bar, and you might wonder: *What do I do with this? What do I type in?* 

It's a **power tool**, so you can use it for a lot of things. But because it can do so much, we don't try to guide you towards a particular workflow—you should be able to use it however you want as an engineer.

As you open up **Cloud Code** for the first time, there are a few things we recommend doing to set up your environment. These are pretty straightforward:

- Run **terminal setup**—this will give you `Shift+Enter` for new lines, so you don't have to use backslashes. It makes it a little nicer to use.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/c8762f31-64f7-42b9-b9b5-9019db533465.webp)

Speaker1: *00:02:57 - 00:03:23*

输入 `/theme` 可设置**浅色/深色模式**或自定义主题。

您还可以执行 `/install-github-app`。今天我们发布了**GitHub应用**，您可以在任意GitHub议题或拉取请求中@**Claude**。要安装该应用，请在终端运行此命令。

Do `/theme` to set **light/dark mode** or customized themes.  

You can also do `/install-github-app`. Today, we announced a **GitHub app**where you can mention**Claude** on any GitHub issue or pull request. To install it, run this command in your terminal.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/3d439f3d-8eea-4032-86e9-98f4fbf0ba39.webp)

Speaker1: *00:03:23 - 00:04:08*

你可以自定义允许的工具集，这样就不会每次都弹出提示。这对于那些我经常需要确认的操作来说相当方便——我一定会这样设置，避免反复确认。

我很多提示词都不是手动输入到**GitHub**的。如果你使用**Mac OS**系统，可以在系统设置的**辅助功能**里启用听写功能。然后只需双击听写键，说出你的提示词即可。  

使用**具体明确的提示词**会很有帮助。这实际上非常棒——你可以像和另一个工程师交谈那样对着代码说话，而不需要打太多字。

You can customize the set of allowed tools so you're not prompted every time. This is pretty convenient for stuff I'm frequently prompted about—I'll definitely customize it this way to avoid accepting it repeatedly.

For many of my prompts, I don't hand-type them into **GitHub**. If you're on**Mac OS**, you can go into your system settings under**Accessibility** and enable dictation. Then, you just hit the dictation key twice and speak your prompt.  

It helps a lot to have **specific prompts**. This is actually pretty awesome—you can just talk to code as you would to another engineer, without typing much.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/5a8f8bcd-1740-4629-b5be-b929957142fc.webp)

Speaker1: *00:04:14 - 00:04:18*

当你刚开始接触**云代码**时，对我来说它无比自由且无所不能。那么该从何处着手呢？我最首要的建议就是先使用**代码库问答AI**——直接向你的代码库提问。

So when you're starting out with **cloud code**, it's so free for me and it can do everything. What do you start with? The thing I recommend above everything else is starting with**Codebase Q&A AI** — just asking questions your codebase.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/b3c41df6-b256-45ea-b52d-1d522c8af9c5.webp)

Speaker1: *00:04:18 - 00:04:53*

这是我们在Ropic传授给新员工的内容。技术入职培训的第一天，你会学习**Claude Code**，下载安装后立即开始针对**代码库**提问。

过去的技术入职流程让团队不堪重负。新员工需要不断咨询其他工程师、手动查阅代码、学习工具使用——所有这些都耗费大量时间。有了**Claude Code**，你只需让它探索**代码库**并解答相关问题。

在Ropic，技术岗的入职培训过去需要两到三周。现在已缩短至两到三天。

This is something we teach new hires at Ropic. On the first day of technical onboarding, you learn about **Claude Code**, download it, get it set up, and immediately start asking questions about the**codebase**.

In the past, technical onboarding taxed the team significantly. You had to ask other engineers questions, explore the code manually, and learn tool usage — all of which took considerable time. With **Claude Code**, you can simply ask it to explore the**codebase** and answer such questions. 

At Ropic, onboarding for technical hires used to take two or three weeks. Now it's down to two or three days.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/4e0ce14e-2e18-4b7c-877a-5b1e76dc2379.webp)

Speaker1: *00:05:05 - 00:05:18*

关于**问答功能**的关键点还在于：我们不会进行任何形式的索引——你的代码不会存储在远程数据库中。我们不会将代码上传到任何地方；**你的代码始终保存在本地**。我们不会用这些代码来训练生成式模型。因此，代码完全由你掌控，不存在任何索引或类似机制。

What's also key about **Q&A**is we don't do any sort of indexing—there's no remote database with your code. We don't upload it anywhere;**your code stays local**. We do not train generative models on the code. So it's there, you control it, with no indices or anything like this.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/1c6e6184-6a4f-479b-82e4-63188df55ec8.webp)

Speaker1: *00:05:18 - 00:05:27*

这意味着无需任何设置。你只需启动**云服务**，下载后即可立即运行——无需索引，无需等待。你可以立刻使用它。

And what that means is there's no setup. You start **cloud**, download it, and run it immediately—no indexing, no waiting. You can use it right away.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/5eb1983a-27e9-4902-834d-6bc13d19055f.webp)

Speaker1: *00:05:30 - 00:06:00*

这是一场技术性演讲，因此我将展示一些非常具体的提示词和代码示例，帮助你提升**四元代码**的使用体验。

你可能会提出以下问题：
- 这段特定代码是如何被使用的？
- 我该如何在**云端代码**中实例化这个对象？

它不仅仅是简单的文本搜索——它会深入挖掘，找到类被实例化和使用的具体案例。你将获得更全面的答案，就像在**规范文档**中看到的那样，而不仅仅是简单的"Command+F"查找结果。

This is a technical talk, so I'll show some very specific prompts and code samples that you can use to improve your **quad code** experience. 

Some questions you might ask:
- How is this particular piece of code used?
- How do I instantiate this thing in **cloud code**?

It won't just do a text search - it'll go deeper, finding examples of how a class is instantiated and used. You'll get a much more thorough answer, like what you'd find in **proper documentation**, not just a simple "Command+F" result.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/e3353463-9b3e-486c-9248-136548320749.webp)

Speaker1: *00:06:00 - 00:07:30*

我经常做的一件事就是查询**Git历史记录**。比如：为什么这个函数有15个参数？为什么参数命名这么奇怪？我敢说每个代码库都有类似这样的函数或类**。ThoughtCode**可以追溯Git历史来查明：
- 这些参数是如何被引入的
- 是谁引入了它们
- 当时是什么情况
- 相关提交关联了哪些issue

它会自动汇总这些信息——你不需要指定细节。只要说"查查Git历史"它就能理解。它之所以知道这些不是因为系统提示，而是因为**TTO**太强大了。如果你让它使用Git，它就知道该怎么做。

我也经常查询**Hub issues**。它能获取issue并提供上下文，这非常棒。

每周一**站会**上我都会问："我这周发布了什么？" ThoughtCode会：
- 查找vlog
- 知道我的用户名
- 给我一份漂亮的发布内容摘要
- 然后我直接复制粘贴到文档里

给新**Claude Code**用户的**建议#1**：
向团队介绍时先从基础问答开始。不要一上来就：
- 用高级工具
- 编辑代码

先问些关于代码库的问题。这能教会大家：
- 如何有效提问
- Claude Code的能力边界
- 哪些需求需要：
  - 一次尝试
  - 多次尝试
  - 在REPL中使用交互模式

Something I do a lot is ask about **Git history**. For example: why does this function have 15 arguments, and why are they named this weird way? I bet all our codebases have functions or classes like this.**ThoughtCode** can look through Git history to figure out:
- How these arguments were introduced
- Who introduced them
- What was the situation
- Which issues those commits linked to

It summarizes all this automatically - you don't need to specify details. Just ask "look through Git history" and it understands. The reason it knows this isn't from our system prompt; it's because the **TTO** was awesome. If you tell it to use Git, it knows how.

I often ask about **Hub issues** too. It can fetch issues and provide context, which is pretty awesome. 

Every Monday in our **weekly standup**, I ask: "What did I ship this week?" ThoughtCode:
- Looks for the vlog
- Knows my username
- Gives me a nice readout of everything I shipped
- Which I then copy-paste into a doc

**Tip #1**for new**Claude Code** users: 
Start with basic Q&A when introducing it to your team. Don't begin with:
- Fancy tools
- Code editing

Just ask questions about the codebase first. This teaches:
- How to prompt effectively
- The boundaries of what Claude Code can do
- What requires:
  - One attempt
  - Multiple attempts
  - Interactive mode in a REPL





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/bef5cf80-6ec1-49ed-899c-42547a9ca580.webp)

Speaker1: *00:07:52 - 00:08:02*

当你熟悉问答功能后，就可以开始尝试编辑代码了。这是进阶的下一步。以智能体方式使用**语言模型**的妙处在于：你只需提供工具，它就能神奇地掌握使用方法。

通过**Claude代码助手**，我们提供了一套小型**内置工具集**：
- 编辑文件
- 运行**Bash**命令
- 文件搜索

系统会将这些工具串联起来，用于代码探索、头脑风暴，最终完成编辑操作。

Once you're comfortable with Q&A, you can dive into editing code. This is the next step. The cool thing about using an **LM** in an agent-like way is you give it tools, and it magically figures out how to use them.

With **Claude Code**, we provide a small set of**built-in tools**:
- Edit files;
- Run **Bash** commands;
- Search files.

It strings these together to explore code, brainstorm, and finally make edits.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/6b3b6a37-24f7-43b0-8cf6-707bd6b8e39e.webp)

Speaker1: *00:08:02 - 00:09:03*

你无需特意指示它使用**这个工具**或那个工具——只需说“做这件事”，它就能自行找到方法完成。它会以符合**Claude Code**逻辑的方式将这些步骤合理串联起来。

使用方法多种多样。我个人有时喜欢在让Claude编写代码前，先请它进行头脑风暴或制定计划。这是我们强烈推荐的做法。

我有时会看到人们拿着**Vood代码**要求实现长达3000行的庞大功能。虽然偶尔能一次成功，但更多时候构建出来的结果与你想要的完全不符。

You don't have to prompt it specifically to use **this tool**and that tool — you just say "do this thing" and it'll figure out how to do it. It'll string it together in the right way that makes sense for**Claude Code**.

There are many ways to use this. Something I like to do sometimes is, before having Claude write code, I'll ask it to brainstorm or make a plan. This is something we highly recommend. 

What I sometimes see is people taking **Vood code** and asking it to implement enormous 3000-line features. Sometimes it gets this right on the first try, but other times what gets built isn't at all what you wanted.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/9133fc12-6b4b-428a-8d50-c67e81575518.webp)

Speaker1: *00:09:03 - 00:09:12*

想要获得理想结果，最简单的方法是先让它思考。**头脑风暴**出各种点子，制定计划，征求我的意见，在编写代码之前先获得批准。

The easiest way to get the result you want is to ask it to think first. **Brainstorm** ideas, make a plan, run it by me, and ask for approval before you write code.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/adfcf6de-cb06-41ef-baa7-cf9cd171e9ee.webp)

Speaker1: *00:09:12 - 00:09:25*

你无需启用计划模式或使用任何特殊工具来完成这个操作。只需直接提出要求，它就能明白该怎么做。你只需要说："在编写代码之前，先制定一个计划。"它就会给出答案。

这个功能也...我想重点说说这个**commit pushf**指令。这是我常用的一个标记符号，虽然本身没什么特别之处，但**Claude**足够智能能理解其含义。它会自动执行以下操作：

1. 创建提交；
2. 推送至分支；
3. 新建分支；
4. 在Hub上为我创建拉取请求。

你完全不需要做任何解释。它会自行检查代码、历史记录和Git日志，来确定提交格式等所有细节。它会以正确的方式完成提交和推送。

You don't have to use plan mode or any special tools to do this. All you have to do is ask, and it'll know what to do. Just say: "Before you write code, make a plan." Answer's it.

This is also... I want to think with this one—this **commit pushf**. It's a really common notation that I use. There's nothing special about it, but**Claude** is smart enough to interpret this. It'll:

1. Make a commit;
2. Push it to the branch;
3. Make a branch;
4. Create a pull request for me on Hub.

You don't have to explain anything. It'll look through the code, the history, and the Git log by itself to figure out the commit format and all the details. It'll make the commit and push it the right way.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/ea22d89f-4e49-497a-9729-7ab4598b31a9.webp)

Speaker1: *00:09:25 - 00:09:50*

再次强调，我们并没有通过系统提示来达成这一点。它只是知道该怎么做——**这个模型确实很优秀**。

Again, we're not system prompting to do this. It just knows how to do this — **the model was good**.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/c27adee1-8775-4799-815f-687e8fdc2386.webp)

Speaker1: *00:09:50 - 00:10:28*

随着你的技能逐渐提升，你会想要开始接入团队的各类工具。这正是**Claude**大显身手的时刻。工具通常分为两大类：

1. **Bash工具**——例如类似*barley CLI*这样的工具（此为虚构示例）。你可以向Claude介绍这个工具，并请它协助研究使用方法。这种方式非常高效。如果你频繁使用某个工具，还可以将其存入DM（我们稍后会详述），这样Claude就能在跨会话时记住它。这是Anthropic团队内部常用的工作模式，我们也观察到外部客户采用同样的实践。

As you get a little more advanced, you'll want to start plugging in your team's tools. This is where **Claude** starts to really shine. There are generally two kinds of tools:

1. **Bash tools** – An example of this would be something like *barley CLI* (this isn't a real thing). You can tell Claude about this tool and ask it to help figure out how to use it. This is efficient. If you find yourself using it often, you can also dump this into your DM (we'll discuss this later) so Claude can remember it across sessions. This is a common pattern we follow at Anthropic, and we see external customers use it too.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/59fc67fd-e4ab-41ea-a56b-86b973c63e8d.webp)

Speaker1: *00:10:28 - 00:10:38*

对于**MCP**也是如此——Claude代码可以使用**bash工具**和**MCP工具**。你只需向它描述这些工具，添加MCP工具，解释如何使用，它就会开始运用它们。

Same thing with **MCP**— Claude code can use**bash tools**and**MCP tools**. Just describe the tools to it, add the MCP tool, explain how to use it, and it'll start using them.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/35151568-5984-4d1d-8b6e-5cf18d5c44bf.webp)

Speaker1: *00:10:38 - 00:11:30*

这一点极其强大，因为当你开始在新的代码库上使用代码时，你可以直接赋予它所有工具——包括你的团队已为该代码库使用的全部工具——代码就能代表你调用这些工具。

常见模式有几种。第一种是我刚才提到的：**先进行少量探索，制定简单计划，在编写代码前请求确认**。

右侧的另外两种模式在系统具备自我验证机制时尤为强大——例如通过编写**单元测试**、运行**测试套件**或在**iOS模拟器**中测试。这样系统就能持续迭代。其精妙之处在于：如果你给它一个模拟环境并说"构建这个网页界面"，它可能做得不错；但经过两三次迭代后，往往就能近乎完美地实现目标。

And this is extremely powerful because when you start to use code on a new code base, you can just give it all of your tools—all the tools your team already uses for this base—and the code can use it on your behalf.

There are a few common modes. This is the one I talked about already: **do a little exploration, do a little planning, and ask for confirmation before writing code**. 

The other two modes on the right are extremely powerful when the system has a way to check its work—for example, by writing **unit tests**, running a**test suite**, or testing in the**iOS simulator**. Then it can iterate. This is incredible because if you give it a mock and say, "Build this web UI," it'll get pretty good. But if you iterate two or three times, it often gets it almost perfect.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/98937d26-f9e1-4420-bd63-abdc8d3727d6.webp)

Speaker1: *00:11:30 - 00:12:07*

因此，关键在于为其提供某种反馈工具以检查其工作成果。基于此，AI将自主迭代，从而获得更优质的结果。  

无论您所处的领域是单元测试、集成测试、应用还是网页开发——只要为其提供评估结果的方法，它就会不断迭代优化。  

以下是后续步骤：  

1. 教会**AI**如何使用您的工具。  
2. 确定合适的工作流程——无论是让AI直接编写代码、头脑风暴、制定计划还是迭代优化。  
3. 对流程有一定理解，以便更有效地向**AI**发出指令。

So the trick is to give it some sort of tool for feedback to check its work. Based on that, it will iterate by itself, and you'll get a much better result.  

Whatever your domain is—whether it's unit tests, integration tests, app or web development—just give it a way to evaluate its results, and it will iterate and improve.  

Here are the next steps:  

1. Teach **AI** how to use your tools.  
2. Figure out the right workflow—whether you want AI to jump into code, brainstorm ideas, make a plan, or iterate.  
3. Have some sense of the process so you know how to prompt **AI** effectively.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/31d43906-3de6-42d3-ba19-bd90d6942b68.webp)

Speaker1: *00:12:07 - 00:12:19*

当你超越工具层面深入探索时，就会开始想要为**Claude**提供更多上下文背景。你提供的背景信息越丰富，它做出的决策就会越智能。

作为基地工程师，你脑海中储存着关于系统架构、历史沿革等海量背景知识。可以通过多种方式将这些信息传递给**Claude**——随着提供的背景资料越详尽，它的表现就会越出色。

As you go deeper beyond tools, you want to start to give **Claude** more context. The more context you provide, the smarter the decisions will be. 

As an engineer working on a base, you have a ton of context in your head about your systems, their history, and everything else. There are different ways to provide this to **Claude**, and as you give Claude more context, it'll perform better.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/41b279d3-01b1-4bbe-81fa-1e524ae4128f.webp)

Speaker1: *00:12:19 - 00:12:54*

实现这一目标有多种方法。**第一种**是我们称之为**MCP**资源的方案**。MCP**是特定的文件名**。首选**存放位置是项目根目录，也就是你开始对话的同一层级目录。在此处放置**MCP**文件后，它会在每次会话开始时自动载入上下文。本质上，用户的第一轮对话就会包含**MCP**内容。

There are different ways to do this. The **first**one is what we call**MCP**resources.**MCP**is the special file name. The**first**place to put it is in the project root, so the same directory you start chatting. Put a**MCP**in there, and that'll get automatically read into context at the start of every session. Essentially, the first user turn will include the**MCP**.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/37907202-54f6-4ea7-be64-d0604e05ec33.webp)

Speaker1: *00:12:54 - 00:14:05*

你也可以拥有一个本地的 **CLAUDElocalmd**文件，这类文件通常不需要提交到源代码管理系统中。而**CLAUDEmd**文件则应该提交到源码控制系统并与团队成员共享，这样就能实现一次编写、多人复用。本地版本仅供个人使用**。CLAUDEmd** 文件中通常包含以下内容：
- 常用 **bash** 命令；
- 常用 **MCP** 工具；
- 架构决策记录；
- 重要文件说明；
- 项目范围内工作需要了解的所有关键信息。

请注意保持内容简洁——如果文档过长，不仅会占用上下文空间，实际效用也会降低。例如在我们的基础文档中仅包含：
- 关键 **bash** 命令；
- 代码风格指南；
- 若干核心文件说明。

其他 **CLAUDEmd**文件可以存放在嵌套子目录中**，Claude**会根据需要自动加载。虽然系统会自动加载某些**CLAUDEmd**文件，但存放在嵌套目录中的文档也会在**Claude** 处理对应目录时被动态加载。

如果是企业级应用，您可能需要创建一个跨所有代码库共享的 **CLAUDEmd**文件。只需将其放置在**/enterpriseroot/CLAUDEmd** 路径下，系统就会自动加载这个全局文档。

You can also have a local **CLAUDElocalmd**, and this one you don't usually check into source control.**CLAUDEmd**, however, should be checked into source control and shared with your team so you can write it once and share it. The local one is just for you.

The kinds of things you put in **CLAUDEmd** include:
- Common **bash** commands;
- Common **MCP** tools;
- Architectural decisions;
- Important files;
- Anything you'd typically need to know to work in the scope base.

Try to keep it short—if it gets too long, it'll use up context and usually isn't that useful. For example, in our base, we have:
- Key **bash** commands;
- A style guide;
- A few core files.

All other **CLAUDEmd**files can be placed in nested child directories, and**Claude**will pull them in on demand. These are the**CLAUDEmd**files that get pulled automatically, but you can also place them in nested directories, and they'll be pulled when**Claude** works in those directories.

If you're a company, you might want a **CLAUDEmd**shared across all code bases, managed on behalf of your users. You can place it in**/enterpriseroot/CLAUDEmd**, and it'll get pulled in automatically.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/6e08437b-f8f0-4076-839e-cd238c6ea705.webp)

Speaker1: *00:14:05 - 00:14:33*

获取上下文的方式多种多样。事实上，为了展示所有可能的方法，我费了很大功夫才组织这场讨论，但**量子d AI**是自动引入的。

你也可以使用**CLAUDEmd**命令（即`clod slash commands`），这些命令可以放在你的主目录下，也可以提交到你的**项目根目录**中。这是专门针对**CLAUDEmd**命令的。

There's a ton of ways to pull in context. I actually had a lot of trouble putting this fight together just to communicate the breadth of ways you can do this, but **quantum d AI** is pulled in automatically.

You can also use **CLAUDEmd**commands (so this is `clod slash commands`), and this can be in your home directory or it can be checked into your**profoct-root**. This is for**CLAUDEmd** commands.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/d68079a1-a55f-4008-b9ad-cfe141d25ccd.webp)

Speaker1: *00:14:33 - 00:15:35*

在这里，我们展示几个**云代码**内置的**斜杠命令**实例。比如当你在云代码仓库中看到议题被自动打标签时，实际上正是这个工作流在运行：**label-github-issuesmd**。

我们配置了一个GitHub Action（就是今早讨论过的同款），云代码会将其作为斜杠命令执行。它能自动处理议题，省去人工操作，大幅提升效率。

你可以添加提及的文件来扩充上下文。正如先前所说，当云代码在某个目录运行时，嵌套目录中的`.md`文件会被自动纳入上下文。花时间优化给云代码的上下文非常值得，具体可以：

- 通过提示优化器运行
- 考虑上下文的目标受众
- 选择每次加载、按需调用或团队共享
- 将其视为个人偏好设置

只要方法得当，精心调校的上下文配置将显著提升运行效能。

And over here, we have a few examples of the **slash commands**that we have in**云代码**itself. For example, if you're in the 云代码 repo and see issues getting labeled, that's actually this workflow running here:**label-github-issuesmd**. 

We have a GitHub Action running (the same one we talked about this morning) where 云代码 will run this command as a slash command. It'll work on the issues so humans don't have to, saving us a bunch of time. 

You can add mentioned files to pull them into context. As I said before, `.md` files in nested directories get pulled in when 云代码 works in that directory. Giving 云代码 more context is definitely worth taking the time to tune. You can:

- Run it through a prompt improver
- Consider who the context is for
- Decide whether to put it in every time, on demand, or share it with a team
- Treat it as a personal preference

Taking the time to tune context will improve performance dramatically if done right.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/dcebf8ed-4e53-44f8-9e4c-64cb54aaf07b.webp)

Speaker1: *00:15:41 - 00:16:11*

随着你更加深入，你会需要更多地思考这种分层整合各种方式的结构。这不仅仅是**dM D**，还包括**fig**以及关于**Quad**的所有内容，你都可以通过这种层级化的方式整合进来。

项目是特定于你的**代码库(Repo)**的，你可以将它们签入或设为仅自己可见。你还可以拥有：

- 适用于所有项目的**全局gs**；
- **企业级策略**，本质上是你为整个团队创建的全局**fig**配置，团队会自动遵循这些配置。

As you get more advanced, you'll want to think more about this hierarchy of different ways to pull in everything. It's not just **dM D**, but also**fig**and everything about**Quad** you can pull in this hierarchical way.

Projects are specific to your **Repo**, and you can check them in or make them just for you. You can also have:

- **Global gs** that apply across all projects;
- **Enterprise policies**, which are essentially global**fig** configurations you create for your entire team to follow automatically.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/4ad40578-fd14-4066-9000-240ca7fa6969.webp)

Speaker1: *00:16:11 - 00:16:33*

这张幻灯片信息量相当大，但核心观点是这套方法适用于许多场景。你可以对**s命令**这么做，也可以对**共享权限**这么做。

举个例子，如果你有一条所有员工都会执行的批处理命令——比如全体员工都要使用的测试指令——你实际上可以把它纳入这个**企业策略文件**中。这样当任何员工运行该命令时，系统就会自动审批，相当便捷。

This slide is pretty information-dense, but the point is this applies to a lot of things. You can do this for **s commands**, you can do it for**share permissions**. 

For example, if you have a batchsh command that all your employees would run — like all employees using this test command — you can actually check it into this **enterprise policies** file. Then, when any employee runs this command, it will be auto-approved, which is pretty convenient.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/238a1c0e-b413-4b5c-b7de-402bcf39c33d.webp)

Speaker1: *00:16:33 - 00:17:19*

你也可以利用这个功能来拦截命令。例如，若存在某个永远不应被请求的URL，只需将其添加到此文件中，就能阻止员工对其进行编辑。该URL将永远无法被获取。无论是用于阻断访问还是保护**代码库**安全，这都相当便捷。

同样的逻辑适用于**MCP服务器**。在代码库中检入一个`MCP ON`文件，这样每当有人在你的代码库中运行代码时，系统就会提示他们安装**MCP服务器**并与团队共享。

如果你不确定该使用哪种方式——由于我们支持多种工作流，且工程流程非常灵活（每家公司情况不同），这会形成一个复杂矩阵——我们的目标是全面覆盖所有场景。若不知从何入手，我建议从**共享项目上下文**开始。

You can also use this to block commands. For example, if there's a URL that should never be fetched, just add it to this file, and that'll prevent an employee from editing it. That URL can never be fetched. It's pretty convenient both for blocking access and keeping your **code base** safe.

The same applies to **MCP servers**. Have an `MCP ON` file checked into the base, so anytime someone runs code in your base, they'll be prompted to install**MCP servers** and share it with the team.

If you're unsure which of these to use—it's a complex matrix because we support many workflows, and engineering flows are very flexible (every company is different)—we aim to support everything. If you're not sure how to get started, I recommend beginning with **shared project context**.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/a2179e41-524b-4089-b840-b69c04f5a369.webp)

Speaker1: *00:17:19 - 00:17:27*

你只需编写一次，就能与团队中的所有人共享，从而产生**网络效应**——某人只需付出少量工作，就能让所有人受益。

You write this once and then share it with everyone on the team, creating a **network effect** where someone does a little bit of work and everyone benefits.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/a66894c6-cc0c-418f-9041-d8ef1fa2369c.webp)

Speaker1: *00:17:34 - 00:18:01*

**ClaudeCode**内置了许多工具来管理这些功能。例如，执行 `/memory` 命令时，你可以看到所有被调用的不同**记忆文件**。

你可能拥有：
- 一份**企业策略**文件；
- 你的**用户记忆**文件；
- **项目文档**；
- 以及可能仅针对特定目录调用的嵌套文档。

同样地，使用 `/s memory` 命令时，你可以编辑特定的**记忆文件**。当输入 `#` 来记忆某些内容时，你可以选择将其存入哪个记忆库。

There are a lot of tools built into **ClaudeCode**to manage this. For example, if you run `/memory`, you can see all the different**memory files** that are getting pulled in. 

You might have:
- An **enterprise policy**;
- Your **user memory**;
- **Project MD**;
- And potentially a nested MD that's only pulled in for certain directories.

Similarly, when you use `/s memory`, you can edit particular **memory files**. When you type `#` to remember something, you can choose which memory you want it to go to.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/9e6808c1-8c90-4dcd-b706-49955d42e201.webp)

Speaker1: *00:18:06 - 00:18:15*

所以没错，下一步就是花时间配置**CLAUDEmd**、**MCP服务器**以及团队使用的所有工具。这样一来，你只需设置一次，就能与所有人共享配置。

So yeah, that's the next step—take the time to configure **CLAUDEmd**,**MCP servers**, and all the tools your team uses. That way, you can set it up once and share it with everyone.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/dd31e356-389e-444d-8a65-4b8801dca328.webp)

Speaker1: *00:18:15 - 00:19:02*

以我们的**Topic**应用代码库为例——这是存放所有网页和应用代码的仓库。其中设有**Tier MCP**服务器，团队共享该资源。库内还配置了**SCHE**系统，因此任何在该代码库工作的工程师都能使用**Tier**功能进行自动试点、测试、截图及迭代——确保每位工程师无需自行安装环境。

本次分享聚焦**专业技巧**。我想稍作延展，探讨一些可能不为人知的常用快捷键绑定：  

- 为**终端**开发虽然极具挑战性，但也充满乐趣——就像在探索一门全新的设计语言  
- 终端界面极度精简，因此有时很难发现这些快捷键  

快速备忘：按下**Shift + Tab**可确认编辑内容。  

（注：技术术语处理说明：  
1. 保留**Topic**/**Tier MCP**/**SCHE**等专有名词不译  
2. "pro tips"译为"专业技巧"而非字面直译  
3. "design language"采用"设计语言"行业标准译法  
4. 保持技术文档特有的简洁句式结构）

An example of this is in our apps repo for **Topic**—this is the repo where we have all of our web and apps code. There's a**Tier MCP**server, and we share this with the team. There's an**SCHE**in it, so any engineer working in that repo can use**Tier** to pilot, test, screenshot automatically, and iterate—ensuring every engineer doesn't have to install it themselves.

This is a talk about **pro tips**. I want to take a quick detour to discuss some common key bindings people may not know.  

- It's very hard to build for **terminal**, but also very fun—it feels like uncovering a new design language.  
- Terminals are extremely minimal, so sometimes it's hard to discover these key bindings.  

Here's a quick reference: you can hit **Shift + Tab** to accept edits.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/1e08726d-c651-4ae7-a1c3-5e174650ced7.webp)

Speaker1: *00:19:02 - 00:20:03*

这将切换至**自动接受编辑**模式。Bash命令仍需确认，但编辑会被自动接受，之后你随时可以让Quad撤销这些改动。

例如，当我确定方向正确时，或者在编写单元测试并反复调整测试用例时，通常会启用自动接受模式，这样就不必逐项确认。

若需要Cloud记住某些操作——比如当它未正确使用某个工具，而你希望它今后能正确使用时——只需输入**#**符号并告知需记忆的内容。系统会自动将其整合至**dM D**中。

如需切换至**bash模式**（运行bash命令），可输入**!**并键入命令。该命令会在本地执行，同时也会出现在**上下文窗口**中，这样Cloud在下一轮交互时就能看到。

此功能适用于：
- 长时间运行的命令（当明确知道要执行的操作时）；
- 任何需要纳入上下文的命令（Quad将看到命令及其输出）。

你可以添加... *(记录中断)*

This switches you into **auto-accept edits** mode. Bash commands still need approval, but edits are auto-accepted, and you can always ask Quad to undo them later. 

For example, I'll do this if I know I'm on the right track, or if it's writing unit tests and iterating on tests. I'll usually just switch into auto-accept mode so I don't have to OK every single item.

Anytime you want Cloud to remember something—for example, if it's not using a tool correctly and you want it to use it correctly from then on—just type the **#**sign and tell it what to remember. It'll incorporate it into**dM D** automatically.

If you ever want to drop down to **bash mode**(to run a bash command), you can hit the**!**and type in your command. That'll run locally, but it also goes into the**context window**, so Cloud will see it on the next turn. 

This is useful for:
- Long-running commands (if you know exactly what you want to do);
- Any command you want to get into context (Quad will see the command and output).  

You can add... *(transcript cuts off)*





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/f81cc6e8-b256-402a-932b-86b8a702e756.webp)

Speaker1: *00:20:03 - 00:20:14*

任何时候你都可以按下**ESC键来停止**Quad当前的操作。无论Quad正在执行什么任务，你都可以安全地按下ESC键——这不会损坏会话或造成任何混乱。  

例如：  
- 假设Quad正在编辑文件——我可以按ESC键终止操作，然后告诉它需要如何调整。  
- 或者它建议进行2:1比例的编辑，但实际上有19行代码看起来完全正确——我会按ESC键，指定需要修改的部分，再让它重新执行该编辑。  

（注：根据中文技术文档惯例，"escape"译为"ESC键"，"hit"译为"按下"更符合操作语境；"redo that edit"采用"重新执行该编辑"既保留技术准确性又符合中文表达）

Anytime you can hit **escape to stop** what Quad is doing. No matter what Quad is doing, you can always safely hit escape — it's not going to corrupt the session or mess anything up.  

For example:  
- Maybe Quad is doing a file edit — I'll hit escape and tell it what to do differently.  
- Or it suggested a 2:1 edit, but actually 19 of these lines look perfect — I'll hit escape, specify the change needed, then tell it to redo that edit.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/ddb701aa-1adf-4cd2-8c3f-d404d0db3c6e.webp)

Speaker1: *00:20:14 - 00:20:40*

你可以连续按两次**escape**键回退历史记录。完成会话后，如需恢复该会话，可以使用`--resume`或`--continue`参数启动`quad`程序。

任何时候若想查看更**详细的输出内容**，按住**Ctrl**键，即可显示完整输出——与云端上下文窗口中呈现的内容完全一致。

You can hit **escape** twice to jump back in history. After you're done with the session, you can start `quad` with `--resume` to resume that session if you want, or `--continue`. 

Anytime if you want to see more **verbose output**, hit**Ctrl**, and that'll show you the entire output—the same thing that cloud sees in its context window.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/e18de5a1-0202-4c7c-a0b0-f5cfd22428c8.webp)

Speaker1: *00:20:40 - 00:21:01*

接下来我想讨论的是**Claude**代码SDK。我们之前提到过这个——就在这之后，Siid会在走廊对面的会议室做一个深度讲解SDK的专场。

如果你还没尝试过：当你在**Claude**中使用`-dashP`参数时，那就是这个SDK的功能。过去几周我们添加了许多新特性来让它变得更强大。

The next thing I want to talk about is the **Claude** code SDK. We mentioned this earlier - right after this, Siid is doing a session just across the hallway where he'll go super deep on the SDK. 

If you haven't tried it yet: when you use the `-dashP` flag in **Claude**, that's what the SDK is. We've been adding many features over the last few weeks to make it even better.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/85e4eae2-8b58-4cf2-9082-018bbccd2911.webp)

Speaker1: *00:21:01 - 00:21:52*

所以，你可以在此基础上构建并实现很酷的功能。这正是**Claude Code**所使用的——它基于相同的**SDK**。

例如，你可以使用`Claude-CLI`（这个**命令行工具SDK**）。你可以传入：
- 一个提示词，
- 允许使用的工具（可能包括特定的**Bash**命令），
- 以及指定你偏好的格式（JSON或流式输出，如果你想处理输出的话）。

这对于构建**智能代理应用**非常有用。我们在**持续集成(CI)**中经常使用它——用于事件响应和各种流水线。它非常方便——可以把它看作一个通用工具。你给它一个提示词，它返回JSON格式的结果，你可以灵活地使用它（通过管道输入或输出）。

So, you can build on top of this and do cool stuff. This is exactly what **Claude Code**uses—it's the same**SDK**. 

For example, you can use `Claude-CLI` (the **CLI SDK**). You can pass:
- A prompt,
- Allowed tools (which could include specific **Bash** commands),
- And specify your preferred format (JSON or streaming if you want to process the output).

This is great for building **agentic applications**. We use this in**CI** all the time—for incident response and various pipelines. It's really convenient—think of it as a universal utility. You give it a prompt, it returns JSON, and you can use it flexibly (pipe into it or out of it).





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/b891611e-8349-45e8-b109-af0423542b22.webp)

Speaker1: *00:21:52 - 00:22:01*

管道功能也相当酷炫。举个例子，你可以先用`git status`命令，然后通过管道将其输出传递给**JQ**工具进行结果筛选。这种组合方式的可能性是无限的。它就像一个超级智能的**Unix实用工具**，而我认为我们才刚刚触及如何运用它的皮毛。我们目前仍在探索阶段。

The piping is also pretty cool. For example, you can use `git status` and pipe this in, then use **JQ**to select the result. The combinations are endless. It's like a super intelligent**Unix utility**, and I think we've barely scratched the surface of how to use this. We're just figuring this out.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/2eb4f42e-85e3-4cde-a5f1-9b4b6523b3c5.webp)

Speaker1: *00:22:01 - 00:22:19*

你可以从**CP存储桶**读取数据，获取庞大的日志文件，然后**通过管道传输**给**Claude**，让它分析日志中的关键信息。同样地，你也可以从**Century LI**获取数据，通过管道输入，交由**Claude**进行处理。

You can read from a **CP bucket**, read a giant log, and**pipe it in**to tell**Claude**to figure out what's interesting about this log. You can also fetch data from the**Century LI**, pipe it in, and have**Claude** process it.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/7cd8e567-4185-4cf8-af39-cbfaaff05ff4.webp)

Speaker1: *00:22:38 - 00:23:22*

最后一点——这可能是我们所见最**高阶的使用场景**——我算是个**Claude普通用户**，通常一次只运行一个Claude实例，可能同时开几个终端标签页跑不同的开源项目。  

观察领域内外的资深用户时，他们几乎总是会：  

- 保持多个**SSH会话**；  
- 通过**TMUX隧道**接入Claude会话；  
- 维护同一代码库的**多个检出副本**以实现任务并行；  
- 或利用**git工作树**实现环境隔离。  

我们正在积极优化这些操作，但目前这些方法能帮助实现与Claude的并行工作。你可以创建任意数量的会话，**并行处理**能带来巨大效率提升。  

*(注：根据上下文将"quad"修正为"Claude"，统一了"TMUX"和"git工作树"等术语。在保持口语化风格的同时精简了冗余表达。)*

The final thing—and this is probably the most **advanced use cases**we see—I'm sort of a**Claude normy**, so I'll usually have one Claude running at a time, and maybe a few terminal tabs for a few different OSS running simultaneously.  

When I look at power users in and out of topic, almost always they:  

- Have **SSH sessions**;  
- Use **TMUX tunnels** into their Claude sessions;  
- Maintain **multiple checkouts** of the same repo to run jobs in parallel;  
- Or leverage **git worktrees** for isolation.  

We're actively working on making this easier, but for now, these are ideas to parallelize work with Claude. You can run as many sessions as you want, and there's a lot you can accomplish in **parallel**.  

*(Note: Corrected "quad" → "Claude" based on corpus context, and standardized terminology like "TMUX" and "git worktrees". Kept conversational tone while tightening redundancy.)*





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/aae28f3e-18b3-46c5-b256-c30412c49cf6.webp)

Speaker1: *00:23:24 - 00:23:37*

好的，以上就是全部内容。我想预留一些时间进行**问答环节**，所以这应该是我的最后一张幻灯片了。如果大家有任何问题，两侧都有麦克风，我们很乐意解答。

So yeah, that's it. I wanted to also leave some time for **Q&A**, so I think this is the last slide that I have. If folks have questions, there are mics on both sides. We'd love to answer any questions.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/80386e31-961f-466e-8e2f-229474049198.webp)

Speaker0: *00:23:52 - 00:23:53*

哈。

Ha.





Speaker1: *00:23:53 - 00:23:54*

我做到了。

I did.





Speaker2: *00:24:00 - 00:24:09*

嘿，Bo，感谢你开发了**Interlude**。我很好奇，对你来说实现过程中最具挑战性的部分是什么？

Hey Bo, thanks for building **Interlude**. I was wondering, what was the hardest part of the implementation for you?





Speaker1: *00:24:11 - 00:24:13*

我认为这其中有很多棘手的部分。

I think there's a lot of tricky parts.





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/9576efce-0a4b-4bf7-98a9-e8d04e042ad0.webp)

Speaker1: *00:24:13 - 00:25:02*

我认为特别棘手的一个部分是如何确保**bash命令**的安全性**。Bash**本质上相当危险，可能会以意想不到的方式改变系统状态。但与此同时，如果必须手动批准每一条bash命令，对工程师来说会非常烦人，而且工作效率会大打折扣，因为你得不断批准每一条命令。

如何以一种可扩展的方式安全地实现这一点，并适用于不同的代码库，确实相当棘手——毕竟并非所有人都在**Docker容器**中运行代码。最终我们采用的方案是：

1. 某些命令是**只读的**；
2. 我们通过**静态分析**来确定哪些命令可以安全组合；
3. 我们有一套**复杂的分层权限系统**，用于在不同级别上允许或禁止命令。

I think one part that is especially tricky is the things we do to make **bash commands**safe.**Bash** is inherently pretty dangerous and can change system state in unexpected ways. But at the same time, if you have to manually approve every single bash command, it's super annoying as an engineer and you can't really be productive because you're constantly approving every command.

Gating how to do this safely in a way that scales across different code bases was pretty tricky—not everyone runs their code in a **Docker container**. Essentially, what we landed on is:

1. Some commands are **read-only**;
2. We do **static analysis** to figure out which commands can be combined safely;
3. We have a **complex tiered permission system** for allowlisting and blocklisting commands at different levels.





Speaker2: *00:25:02 - 00:25:03*

对。

Right.





Speaker0: *00:25:05 - 00:25:16*

嗨Boris，你提到要给**云代码**传一张图片，这让我好奇是否有什么我不知道的模态功能。你是直接让它指向某个云端图片还是...

Hi Boris, you mentioned giving an image to **cloud code**, which made me wonder if there's some sort of modal functionality that I'm not aware of. Are you just pointing it at an image on the...





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/b4d629ff-666e-4d56-96e5-78d114dbaa05.webp)

Speaker0: *00:25:16 - 00:25:17*

文件系统之类的。对。

File system or something. Yeah.





Speaker1: *00:25:17 - 00:25:45*

所以**Claude代码**是完全模态化的——从一开始就是如此。由于它运行在**终端**里，所以这个功能不太容易被发现。但你可以：

- 拖放一张图片进去（这招管用）；
- 给它一个文件路径（同样有效）；
- 直接复制粘贴图片进去（也行得通）。

我经常使用这个功能。比如当我有个设计稿时，就直接把稿子拖进去，让它实现这个设计，再配个分层服务器让它能反复调试。整个过程完全自动化。

So **Claude code**is fully modal—it has been from the start. It's in a**terminal**, so it's a little hard to discover. But you can:

- Take an image and drag and drop it in (that'll work);
- Give it a file path (that'll work);
- Copy and paste an image in (that works too).

I use this pretty often. For example, if I have a mock of something, I'll just drag and drop the mock in, tell it to implement it, and give it a tier server so it can iterate against it. It's just fully automated.





Speaker4: *00:25:48 - 00:25:49*

嘿，你为什么选择开发一个**命令行工具**而不是**集成开发环境**呢？

Hey, why did you build a **CLI tool**instead of an**IDE**?





Speaker1: *00:25:54 - 00:26:38*

这是个很好的问题。我认为主要有两个原因：

1. 我们开启的这个**主题**，其用户群体使用的**IDE**非常多样化——有人用**VS Code**，有人用**Z**或**Xcode**或**IM**或**EMX**。要开发一个适合所有人的工具很有挑战性，所以终端就成了最大公约数。

2. 在这个主题中，我们亲眼见证了模型改进的速度有多快。很可能到今年年底，人们就不再需要**IDE**了。鉴于模型的飞速发展，我们希望为这个未来做好准备，避免在**UI**和其他层级上过度投入——这些工作可能很快就会过时。

Yeah, it's a good question. I think there are probably two reasons:

1. We started this **topic**, and topic users employ a broad range of**IDEs**—some use**VS Code**, others use**Z**or**Xcode**or**IM**or**EMX**. It was challenging to build something that works for everyone, so the terminal is just the common denominator.

2. In topic, we observe firsthand how rapidly the model is improving. There's a good chance that by year's end, people won't be using **IDEs**anymore. We want to prepare for this future and avoid over-investing in**UI** and other layers, given the models' progress—this work may soon become obsolete.





Speaker0: *00:26:39 - 00:26:39*

是的。

Yes.





Speaker3: *00:26:42 - 00:26:45*

是啊。你有多少——我不确定这个开着吗？

Yeah. How much of you—I don't know if this is on?





![](https://pic.aihaoji.com/user_2nMOjltugKNw1QtG7a8C0ypW0Cr/img/20260415/4750dd04-dba6-3de3-7efd-de2ef2f05876/b255d28d-3f70-4fe4-9fc6-ee8a13f1cbeb.webp)

Speaker3: *00:26:45 - 00:26:55*

我希望你能使用**绘图代码**进行**机器学习**建模，近乎实现一种**AutoML**的体验。我很好奇——目前这方面的体验如何？

I want you to use **plot code**for**machine learning**modeling and almost an**AutoML** experience. I was curious—what has the experience been so far with that?





Speaker1: *00:26:55 - 00:27:23*

是的，我认为问题在于：我们在**机器学习**和建模中使用了多少**QA**代码？实际上我们使用得非常频繁。Ropic的工程师和研究人员每天都会用到**QA**代码。据我所知，公司约**80%**的技术人员日常都在使用**QA**代码，希望你能从产品中感受到这一点，以及我们投入其中的热爱与内部测试。  

这包括研究人员使用**notebook**工具等来编辑和运行笔记本的情况。

Yeah, I think the question was: how much are we using **QA**code for**machine learning**and modeling? We actually use it quite a bit. Both engineers and researchers at Ropic use**QA**code every day. I think about**80%**of technical people at Ropic use**QA** code daily, and hopefully, you can see that in the product and the amount of love and dogfooding we've put into it.  

This includes researchers who use tools like the **notebook** tool to edit and run notebooks.





Speaker3: *00:27:23 - 00:27:24*

好的，非常酷。

Okay, very cool.





Speaker1: *00:27:24 - 00:27:29*

谢谢。好的，我想就这样吧。多谢。

Thank you. All right, I think that's it. Thanks.





