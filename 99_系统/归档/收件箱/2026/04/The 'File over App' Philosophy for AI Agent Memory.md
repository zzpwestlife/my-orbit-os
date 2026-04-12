---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://www.bestblogs.dev/en/status/2040572272944324650"
created: 2026-04-08
processed: 2026-04-12
output: "[[File over App - AI Agent 记忆的个人维基实践]]"
---
[![Andrej Karpathy](https://pbs.twimg.com/profile_images/1296667294148382721/9Pr6XrPB_normal.jpg)](https://www.bestblogs.dev/en/tweets?sourceId=SOURCE_073b5b)

### [Andrej Karpathy](https://www.bestblogs.dev/en/tweets?sourceId=SOURCE_073b5b)

@karpathy

```
Farzapedia，Farza 的个人维基，是我那条关于 Wiki LLM 推文之后的一个很好的实践案例。

我非常喜欢这种个性化方式，相比于那种“AI 越用越聪明”的现状，它在很多方面都更胜一筹：

1. 显式化。记忆工件是显式且可导航的（维基本身），你可以清楚地看到 AI 到底知道什么、不知道什么，并且可以检查和管理这些工件，即使你自己不直接编写文本（由 LLM 完成）。关于你的知识不是隐式的、未知的，而是显式的、可见的。
2. 归你所有。你的数据属于你自己，存储在你的本地计算机上，而不是在某个 AI 提供商的系统中，无法提取。你掌控着自己的信息。
3. 文件优于应用。这里的记忆是一组以通用格式（图像、Markdown）存储的文件。这意味着数据具有互操作性：因为它们只是文件，你可以使用海量的工具/命令行界面 (CLI) 或任何你想要的东西来处理这些信息。智能体可以在它们之上应用整个 Unix 工具集。它们可以原生读取和理解这些文件。任何类型的数据都可以作为输入导入文件，任何类型的界面都可以作为输出查看它们。例如，你可以使用 Obsidian 来查看它们，或者用代码实现你自己的查看器。搜索“File over app”了解这一哲学。
4. 自带 AI (BYOAI)。你可以使用任何你想要的 AI 来“接入”这些信息——Claude、Codex、OpenCode 等等。你甚至可以考虑获取一个开源 AI 并在你的维基上进行微调——原则上，这个 AI 不仅是关注你的数据，还能在权重层面“了解”你。

因此，这种个性化方法让你能够完全掌控。数据是你的。采用通用格式。显式且可检查。随心所欲地使用任何 AI，让那些 AI 公司保持危机感吧！:)

当然，这并不是让 AI 了解你的最简单方法——它确实需要你管理文件目录等等，但智能体也让这变得相当简单，它们能给你很大帮助。我想未来可能会出现许多产品让这一切变得更容易，但我认为“智能体熟练度”是 21 世纪的一项核心技能。它们是非常强大的工具——它们会说英语，还能为你完成所有的计算机操作。尝试一下这个机会，去体验一下吧。

---

【引用推文】

这是 Farzapedia。

我让一个大语言模型 (LLM) 提取了我日记、Apple Notes 和一些 iMessage 对话中的 2,500 条条目，为我创建了一个个人维基。

它为我的朋友、我的初创公司、研究领域，甚至我最喜欢的动画及其对我的影响，撰写了 400 篇详细的文章，并附带了反向链接。

但是，这个维基不是为我建立的！我是为我的智能体建立的！

维基文件的结构及其反向链接的方式非常容易被任何智能体抓取 + 使其成为一个真正有用的知识库。

我可以启动 Claude Code 来处理这个维基，从 index.md（我所有文章的目录）开始，当我提出查询时，智能体在钻取我维基中需要上下文的特定页面方面做得非常好。

例如，当试图构思一个新的落地页时，我可能会问：

“我正在为我的一个新想法设计这个落地页。请查看最近启发我的图片和电影，并为我提供新的文案和美学建议”。

在我的日记中，我记录了一切：心得、人物、灵感、有趣的链接、图片。

所以智能体阅读我的维基，并从关于吉卜力工作室纪录片的笔记中提取我的“哲学”文章，从我截屏了落地页的 YC 公司那里提取“竞争对手”文章，以及我多年前保存的 1970 年代披头士乐队商品的图片。它给出了一个很棒的回答。

一年前我用 RAG 构建了一个类似的系统，但效果很烂。

一个能让智能体通过它真正理解的文件系统找到所需内容的知识库，效果就是更好。

现在最神奇的事情是，当我向我的维基添加新内容（文章、灵感图片、会议记录）时，系统可能会更新它认为属于该上下文的 2-3 篇不同文章，或者直接创建一篇新文章。

它就像你大脑的超级天才图书管理员，总是为你完美地归档东西，同时也让你轻松地为有用的任务（例如设计、产品、写作等）查询知识，而且它永远不会累。

我下周可能会花时间把这个产品化，如果你感兴趣，请私信我并告诉我你的用例！
```

#### Farza 🇵🇰🇺🇸

3d ago

```
This is Farzapedia.

I had an LLM take 2,500 entries from my diary, Apple Notes, and some iMessage convos to create a personal Wikipedia for me.

It made 400 detailed articles for my friends, my startups, research areas, and even my favorite animes and their impact on me complete with backlinks.

But, this Wiki was not built for me! I built it for my agent!

The structure of the wiki files and how it's all backlinked is very easily crawlable by any agent + makes it a truly useful knowledge base.

I can spin up Claude Code on the wiki and starting at index.md (a catalog of all my articles) the agent does a really good job at drilling into the specific pages on my wiki it needs context on when I have a query.

For example, when trying to cook up a new landing page I may ask:

"I'm trying to design this landing page for a new idea I have. Please look into the images and films that inspired me recently and give me ideas for new copy and aesthetics".

In my diary I kept track of everything from: learnings, people, inspo, interesting links, images.

So the agent reads my wiki and pulls up my "Philosophy" articles from notes on a Studio Ghibli documentary, "Competitor" articles with YC companies whose landing pages I screenshotted, and pics of 1970s Beatles merch I saved years ago. And it delivers a great answer.

I built a similar system to this a year ago with RAG but it was ass.

A knowledge base that lets an agent find what it needs via a file system it actually understands just works better.

The most magical thing now is as I add new things to my wiki (articles, images of inspo, meeting notes) the system will likely update 2-3 different articles where it feels that context belongs, or, just creates a new article.

It's like this super genius librarian for your brain that's always filing stuff for your perfectly and also let's you easily query the knowledge for tasks useful to you (ex. design, product, writing, etc) and it never gets tired.

I might spend next week productizing this, if that's of interest to you DM me + tell me your usecase!
```

![视频缩略图](https://pbs.twimg.com/amplify_video_thumb/2040562032819486720/img/jVrKry6tC4BPFnCg.jpg)

02:24