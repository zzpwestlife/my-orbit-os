---
type: "inbox"
status: "processed"
archived: 2026-03-26
source: "web-clipper"
url: "https://x.com/Chat24954Lip/status/2034876636542509438"
created: 2026-03-21
---
我一直把 X 当成一个高密度的信息输入源。很多有价值的观点、案例、方法，第一眼看到的时候就知道值得留。但过去很长一段时间里，我的处理方式其实很原始：先点收藏，想着之后再整理进 Obsidian。

问题在于，这个 “之后” 经常不会发生。收藏会越积越多，但真正进入知识库的内容却很少。最后就会出现一种很典型的断裂：输入很多，留存很少；看过很多，沉淀很少。

所以这次我想解决的不是一个宏大的知识管理问题，而是一个很小、但非常真实的动作断点：**能不能把 “先收藏，之后再搬运” 压缩成一个动作？**

最后我做出来的是一个插件：**x-bookmark-to-obsidian**。 **现在我在** [x.com](https://x.com/) **点击 “收藏”，帖子内容就会自动抓取下来，写成 Markdown，直接进入 Obsidian。**

最后跑通的方案，是三段式：

1. 浏览器 content script 监听 X 的收藏动作
2. background 把帖子 URL 和最小元数据发给 Native Host
3. Native Host 调本地抓取能力，再把 Markdown 写入 Obsidian

这次也让我重新确认了一件事：浏览器自动化真正难的，往往不是前面那一下点击，而是后面那条链路有没有一起打通。如果抓取、写入、去重、后处理这几层没有一起想清楚，功能表面上看起来像是完成了，实际用起来还是会不断掉链子。

另外也说明一下，这个项目不是从零开始新写的。它是在一个已有项目基础上继续改造出来的。我这次主要补的是 “X 收藏 -> Obsidian” 这条链路，以及路径配置、媒体兼容、失败降级、URL 去重这些更贴近真实使用的问题。也很感谢原项目提供了一个很好的起点，让这次改造能把精力集中在实际工作流本身。

如果你也：

- 把 X 当输入源
- 用 Obsidian 做知识库
- 想减少 “收藏之后再搬运” 的摩擦

那这个插件你可能会用得上。

项目地址：GitHub: [https://github.com/zhaoscsc/x-bookmark-to-obsidian](https://github.com/zhaoscsc/x-bookmark-to-obsidian)

版本更新：2.2.0 版发布。

- 现在使用固定扩展 ID，不再需要用户手动复制扩展 ID
- 单帖抓取能力已内置到发行包，不再依赖外部 ~/.agents 环境
- **首次使用只需要：加载扩展 -> 运行安装器 -> 选择 Obsidian 目录**
- 仍然保留 Native Host，因为它是静默写入任意 Obsidian 路径的关键能力

Release 提供两个 ZIP： 1、x-bookmark-to-obsidian-extension：扩展目录，解压后直接加载到 Chrome 2、 x-bookmark-to-obsidian-installer：本机安装器，双击 install.command 即可

安装步骤：

1. 下载 extension. zip 并解压
2. 在 chrome://extensions 中加载已解压扩展程序
3. 下载 installer. zip 并解压
4. 双击 install.command
5. 重启 Chrome
6. 在扩展弹窗选择 Obsidian 保存目录 **注意事项，这个安装器会议安全提醒，提示移动废纸篓，要在 macOS 的系统设置隐私和安全性里面允许才可以。**

## 保存以后，大概是这个样子

![图像](https://pbs.twimg.com/media/HD58GpBboAEpu7J?format=jpg&name=large)

![图像](https://pbs.twimg.com/media/HD58PvBbQAAAbMy?format=jpg&name=large)