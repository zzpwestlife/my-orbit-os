---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://mp.weixin.qq.com/s/WqdJxdr-UBTvK12g4a4zmQ"
created: 2026-03-05
processed_to: "[[Claude Code可观测性实践]]"
processed_date: 2026-03-05
---
![cover_image](https://mmbiz.qpic.cn/mmbiz_jpg/Wkpr3rA9wF02o6Ph8pnkDsiaaD5sF0fNia0NPhKEicvEx9nEhhIW7yby4ia4ZygmibEVyPl6SRbN0Sn5YX8kqHpbTjQ/0?wx_fmt=jpeg)

Original 冯若航 [老冯云数](https://mp.weixin.qq.com/s/) *2026 年 1 月 26 日 21:24*

昨天老冯发了条推特：“做了个 Claude Code Grafana Dashboard ，研究下它是怎么做决策，用工具，调 API 花钱的。” 结果发现非常多的用户都对这个主题感兴趣。

![Image](https://mmbiz.qpic.cn/mmbiz_png/Wkpr3rA9wF02o6Ph8pnkDsiaaD5sF0fNiaZY427KnfC9MvE8AxSgia9YxuaaIoM1Iqbj17iaYjEbh5ggQSM7lFgOjQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0) ![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

这是我没想到的。所以今天来聊一聊 那就是 Claude Code 的可观测性 。

老冯的想法其实非常简单 —— 我也挺好奇这个 Claude Code 内部到底是怎么工作的。虽然 Claude Code 不开源（ [其实被开源过一次](https://mp.weixin.qq.com/s?__biz=MzU5ODAyNTM5Ng==&mid=2247489471&idx=1&sn=fb8cdcbdac233959f153a4d11eec9ffa&scene=21#wechat_redirect) ），但你其实可以通过它的监控指标和日志，分析出它的大概工作原理。

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

  

Claude Code 提供 OTEL 格式的指标和日志，而且配置起来其实挺简单的。你只要指定几个环境变量，就可以让它主动推送到支持 OTEL 的监控系统里面去，然后用 Grafana 进行可视化。

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

这里的难点其实在于：我去哪找这么一个监控系统和 Grafana 呢？后来我看见这么多人都有需求，就干脆做一个开箱即用的配置模板。你只要找一台 Linux 服务器，运行几行命令把这个东西拉起来，它就会自带一个 Claude Code 的环境，所有东西都帮你配好了（包括监控这些）。你也可以直接把自己的 Claude Code 监控给接进去。

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

实际上，如果你已经会用 Claude Code 的话，并不需要了解太多细节。你只要告诉它有这么个东西、能干这么个事，并给它准备一台虚拟机，剩下的事它都应该能帮你自动干好。我看有人评论留言就是这么说的。哈哈！

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

## 监控事件说明

  

这个监控面板其实很朴素：上方可以选择会话（Session ID），选择之后，下方会列出各种各样的事件。你可以通过拖动来查看在处理任务的过程中都产生了哪些事件。

目前最主要的事件分为以下四大类：

1.User Prompt：你对它说了什么，或者给了什么提示词 2.API Request：调用 API 的请求 3.Tool Decision：系统决定使用什么工具 4.Tool Result：工具返回的具体结果

每个事件都有一些对应的字段。大体上，只要看一眼这个面板，就能明白整个任务的处理流程是怎么一回事了。

举个例子，最简单的事件就是 User Prompt，你给 CC 发一条信息，就会有一个这个事件：

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

  

User Prompt 事件之后，通常是 API Request ，也就是调用 API 模型。这里会有一个 model 字段 —— Claude 是区分了快速模型和高质量模型的，这里我用的是 GLM 4.7 作为例子，有些简单快速的请求，是 4.5-air 来处理的。

然后 API Request 事件会有几个核心字段：Cost，就是开销，然后是四个 Token 指标。Token.In / Out 就是输入，输出的 Token，Token Cache Read 则是缓存命中的指标。

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

API Request  完成之后，通常会有一个  Tool Decision 事件，也就是模型进行了决策，用什么样的工具。这里比如说就有 Bash，Read，Write，Search 等各种各样的 Tool，然后会有一个 Decision Source / Result，也就是根据什么标准（配置文件/询问用户/……），选择 “批准” / “拒绝”。

Tool Decision  事件之后，就是  Tool Restult 事件了。这是调用工具的关键事件，关键字段包括 —— Tool 的命令，说明，错误，参数，UseID，成功与否等等……

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

其实还有一些其他类型的事件，但是最主要的事件类型就是上面这四类。关于更多细节：可以参考 Claude Code 的监控文档： https://code.claude.com/docs/en/monitoring-usage

  

## 沙箱环境

  

当然，老冯也知道 “授人以 渔 不如授人以 鱼 ” ，但光说原理没用，干脆就直接把东西做好给你算了。所以我做了一个开箱即用的沙箱环境，里面就包含了一套完整的开箱即用的 Vicotira 监控系统与 Grafana 监控大盘，随便找台 1C2G 的 Linux 虚拟机几分钟就装好了。

  

这个沙箱除了监控 Claude Code ，还可以干很多有趣的事情。最主要的是，它已经替你配置好了常用的 Web Coding 工具 Claude Code，VS Code，Open Code。里面自带一个 PostgreSQL 和 Nginx，所以如果你需要一个云服务器开发环境，也可以试一试。

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

  

你也可以在这里直接使用不用翻墙的 GLM 模型，多配置一行参数就好了。 关于 Claude Code 最美妙的就是：既然你都已经用它了，那你大概也不需要操心这些细节都是怎么弄的 ，直接动嘴让它自己去 VIBE 自己就好了

  

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

![Image](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

  

![](https://mmbiz.qlogo.cn/mmbiz_jpg/e5xS3Vwicpl8vEzwicmWCF70Y4HnvILGe2WlJnGNdXqQOyUq83icsPshyXHt8ytQhusdhppIKm6xs3TbYzVlHbJWA/0?wx_fmt=jpeg)

 [Like the Author](https://mp.weixin.qq.com/s/)

继续滑动看下一个

老冯云数

向上滑动看下一个

Clip to Feishu Docs