---
type: "inbox"
status: "processed"
source: "web-clipper"
url: "https://x.com/shao__meng/status/2028993863009137082"
created: 2026-03-09
processed: 2026-03-12
integrated_to: "[[30_研究/AI编程方法论]]"
---
**meng shao** @shao\_\_meng 2026-03-03

Anthropic 团队 skill-creator 重磅优化：让 Agent Skills 可测试、可衡量、可迭代

使用过 Agent Skills 的朋友相信对 skill-creator 都不陌生，它可以帮助用户零代码创建 Skills，但 Skills 创建之后，总会遇到这几个问题：

・这个 Skills 在新模型版本上是否仍有效？

・它是否只在该触发时才触发？

・修改后效果是否真的变好了？

没有测试机制，Skills 只是 “看起来管用”，而非 “确切知道管用”。这次官方更新正是为了填补这一空白，将软件开发的测试、基准、迭代实践引入 Agent Skills 创作，且完全无需用户写代码，感谢 @RLanceMartin 的分享！

https://claude.com/blog/improving-skill-creator-test-measure-and-refine-agent-skills…

先看看 Skills 的两种本质类型

1\. 能力提升型

模型原本 “做不到” 或 “做不稳定” 的事，通过 Skills 注入特定技巧、模式来稳定输出。典型例子是文档创建 Skills（如 PDF 处理）。

测试重点：监控模型通用能力是否已追上或超越 Skills，一旦基线模型无需 Skills 即可通过 evals，该 Skills 即可 “退休”。

2\. 偏好编码型

模型每一步都能做，但需要按团队特定流程严格排序。例子：按固定标准审查 NDA、按公司模板生成周报。

测试重点：验证 Skills 是否忠实还原真实工作流，而非模型的 “自由发挥”。

skill-creator 核心新功能

1\. Evals ~ Skills 的 “单元测试”(非常重要！)

・用户只需提供：测试提示词、“好输出应该是什么样子” 的描述。

・skill-creator 自动运行 Skills，判断是否达标。

・实际案例：PDF Skills 曾无法处理 “无字段的非填表表单”，必须精确坐标放置文字。evals 精准定位失败场景，团队据此修复为 “锚定已提取文字坐标”，问题解决。

两大实际价值：

・及早发现质量回归（新模型或基础设施变动导致旧 Skills 失效）。

・判断能力提升型 Skills 是否 “过时”（基线模型已能独立通过 evals）。

2\. Benchmark 模式 ~ 标准化、可追踪的性能仪表盘

支持批量运行同一组 evals，输出指标包括：

・通过率

・执行时间

・Token 消耗

可在模型更新后、Skills 迭代前后定期运行，结果可本地存储、接入仪表盘或 CI / CD 系统，实现真正意义上的 “Skills 持续集成”。

3\. 多智能体并行 + 比较智能体

・多智能体支持：每个 eval 在独立干净的上下文中并行运行，避免上下文污染和顺序依赖，大幅提速。

・比较智能体：盲测模式，同时运行 “Skills A vs Skills B” 或 “有 Skills vs 无 Skills”，由第三方智能体在不知情的情况下客观打分，消除主观偏差。

4\. 触发描述智能调优

随着 Skills 库扩大，描述过宽会导致误触发，过窄则永不触发。skill-creator 现可：

・分析当前描述 vs 历史样本提示

・建议优化文字，同时降低假阳性和假阴性

实际效果：在 Anthropic 自己的 6 个公开文档创建 Skills 上，5 个触发准确率显著提升。

未来方向：从 “如何做” 到 “做什么”

今天 SKILL. md 本质上是 “实现计划”（how），未来可能只需要 “目标描述”（what），模型自己推导实现路径。 而本次发布的 evals 框架，正是迈向这一目标的关键一步 —— 因为 evals 本身就是在描述 “what should happen”。

> 2026-03-03
> 
> check out the updated skill-creator. i esp like built-in support for test generation (e.g., to measure + optimize tricky things like skill trigger rate). available in Claude Code as plugin, http://Claude.ai, + Cowork.
> 
> ![图像](https://pbs.twimg.com/media/HChvJ9XawAIIqE4?format=jpg&name=large)