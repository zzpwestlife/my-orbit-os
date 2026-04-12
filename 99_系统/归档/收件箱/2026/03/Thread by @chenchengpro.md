---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://x.com/chenchengpro/status/2033855423623925869"
created: 2026-03-17
archived: 2026-03-26
---
**陈成** @chenchengpro [2026-03-17](https://x.com/chenchengpro/status/2033855423623925869)

大多数人用 AI 写代码，还在一条条手敲 prompt。

真正的差距不在于谁用了更好的模型，而在于谁把自己的工程经验编码成了可复用的流程模块。

Matt Pocock（TypeScript 圈知名工程师）把他每天在用的 5 个 agent skill 全部开源了：

→ /grill-me — 在你动手写任何东西之前，对你的方案发起连续追问，直到把每个决策分支都逼出来。他自己被问了 24 个问题，坐在那写了一小时 PRD。

→ /write-a-prd — 通过互动访谈 + 读你的代码库，生成一份完整需求文档，自动以 GitHub Issue 归档。

→ /prd-to-issues — 把 PRD 按「垂直切片」拆成一个个独立可认领的 Issue，开箱即用。

→ /tdd — 经典红 - 绿 - 重构循环，每次做一个切片，逼 Agent 先写测试再实现。

→ /improve-my-codebase — 扫描代码库，找架构改进点，重点是加深 "浅层模块" 和提升可测试性。

三天前刚开源，已经 1.2k star。

这背后的本质是：会 prompt 的人很多，能把经验系统化的人很少。 Skill 就是把你作为工程师的判断力和流程，变成 Agent 可以反复执行的操作合约。

你写给 Agent 的 skill，就是你在这个时代留下的工程资产。