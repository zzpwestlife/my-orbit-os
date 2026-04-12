# 启动计划: Claude Code 工程实践

## 来源
- 收件箱文件: [[你不知道的 Claude Code：架构、治理与工程实践]]
- 原始链接: https://x.com/HiTw93/status/2032091246588518683
- 作者: @HiTw93（Tw93，Kaku 终端作者）
- 收件箱日期: 2026-03-12

## 目标
系统掌握 Claude Code 的六层架构（上下文工程、Skills 设计、工具设计、Hooks、Subagents、验证闭环），建立可复用的工程化配置实践，从"会用 Claude Code"进化到"能治理 Claude Code"。

## 项目结构
- 领域: [[AI编程]]
- 类型: project
- 预估规模: 中型（15 个知识主题，3 个实践阶段，预计 3-4 周）
- 建议路径: `20_项目/Claude-Code-工程实践/Claude-Code-工程实践.md`

## 建议行动项
- [ ] 确认项目优先级和时间线
- [ ] 创建项目文件夹 `20_项目/Claude-Code-工程实践/`
- [ ] 定义成功标准（见下方"成功指标"）
- [ ] 分解为阶段/里程碑（见下方"行动"）
- [ ] 识别依赖项：需先完成 [[Vibe-Coding-学习]] 阶段1理论学习
- [ ] 将收件箱原文标记为 `status: processed`

## 项目大纲草案

### 背景

**问题：** 大多数人把 Claude Code 当 ChatBot 用，上下文越来越乱、工具越多效果越差、规则越写越长却越不遵守。根本原因不是 Prompt 写得不好，而是缺乏对 Claude Code 六层架构的系统理解和工程化治理。

**为什么重要：**
- 原文来自 Tw93 半年深度使用的实战经验，覆盖了 Claude Code 从底层运行机制到上层工程实践的完整知识体系
- 这些知识直接可操作——每一节都有具体的配置示例、反模式警告和最佳实践
- 与 vault 中已有的 [[AI编程方法论]] 研究互补：方法论研究偏"认知层"（怎么想），本项目偏"工程层"（怎么做）
- 直接服务于 OrbitOS 自身的 Claude Code 配置优化

### 行动（阶段）

#### 阶段1: 知识提取与结构化（1 周）
从收件箱原文提取核心知识点，创建原子化知识卡片。

- [ ] 提取并创建知识卡片到 `40_知识库/AI编程/`：
  - [ ] [[Claude Code 代理循环]]（第1节：收集上下文 → 行动 → 验证 → 循环）
  - [ ] [[Claude Code 概念边界]]（第2节：MCP / Plugin / Tools / Skills / Hooks / Subagents）
  - [ ] [[上下文工程实践]]（第3节：200K 分解、分层加载、压缩陷阱、Compact Instructions）
  - [ ] [[Skills 设计模式]]（第4节：三种类型——检查清单、工作流、领域专家；反模式）
  - [ ] [[Agent 工具设计原则]]（第5节：好工具 vs 坏工具、AskUserQuestion 演进）
  - [ ] [[Hooks 工程实践]]（第6节：PostToolUse、Notification、三层叠加）
  - [ ] [[Subagents 使用指南]]（第7节：隔离 vs 并行、权限约束、反模式）
  - [ ] [[Prompt Caching 架构]]（第8节：前缀匹配、缓存破坏陷阱、defer_loading）
  - [ ] [[验证闭环设计]]（第9节：Verifier 层级、Definition of Done）
  - [ ] [[CLAUDE.md 编写指南]]（第11节：应放/不应放什么、高质量模板）
- [ ] 创建研究笔记到 `30_研究/AI编程/Claude-Code工程实践/`，整合以上知识点
- [ ] 更新 [[AI编程方法论]] 研究笔记，添加本项目的交叉引用

#### 阶段2: 实践应用与配置优化（1-2 周）
将知识应用到 OrbitOS vault 自身的 Claude Code 配置。

- [ ] 审计当前 OrbitOS 的 CLAUDE.md，对照第11节模板优化
  - [ ] 检查是否过长，精简到核心契约
  - [ ] 添加 Compact Instructions
  - [ ] 添加 Verification 部分
- [ ] 评估现有 Skills 配置
  - [ ] 检查描述符 token 消耗
  - [ ] 按频率分类：auto-invoke / disable-auto-invoke / 移除
  - [ ] 优化描述符长度（目标: <15 tokens/skill）
- [ ] 配置 Hooks
  - [ ] PostToolUse: Edit 后自动格式化/校验
  - [ ] Notification: 任务完成通知
- [ ] 运行 `/health` 健康检查（`npx skills add tw93/claude-health`）
- [ ] 记录优化前后的体感差异

#### 阶段3: 总结沉淀与分享（1 周）
将实践经验沉淀为可复用的知识资产。

- [ ] 整理 Claude Code 工程化配置最佳实践清单
- [ ] 创建"Claude Code 工程化布局参考"（基于第12节的完整布局）
- [ ] 更新 [[Vibe-Coding-学习]] 项目，添加"工程化治理"阶段
- [ ] 编写项目总结到进展日志
- [ ] 归档完成的收件箱内容到 `99_系统/归档/收件箱/2026/03/`

### 成功指标
- [ ] 从原文 15 节内容中提取 ≥10 张原子化知识卡片
- [ ] OrbitOS 的 CLAUDE.md 通过 `/health` 检查无严重问题
- [ ] Skills 描述符总 token 消耗降低 ≥30%
- [ ] 配置至少 2 个 PostToolUse Hooks 并验证有效
- [ ] 建立个人 Claude Code 工程化配置模板，可复用到其他项目

## 与现有项目的关系

### 与 [[Vibe-Coding-学习]] 的关系
- **互补而非重叠**：Vibe Coding 学习是广义的 AI 编程方法论（模型选择、需求沟通、SDD），本项目是专精的 Claude Code 工程实践（架构治理、配置优化）
- **层级关系**：Vibe Coding = "学会开车"，Claude Code 工程实践 = "学会改装和维护引擎"
- **建议**：本项目保持独立，但在 Vibe Coding 阶段2实践应用中添加交叉引用
- **依赖**：建议先完成 Vibe Coding 阶段1的理论基础

### 与已有研究笔记的关系
- [[AI编程方法论]]：本项目的工程实践将丰富其"开发层"内容，特别是 Context Engineering 部分
- [[learn-claude-code架构拆解]]：提供了 Agent 底层12层架构视角，与本项目的六层治理视角互补
- [[Anthropic的战略转向]]：Skills 战略背景，本项目的 Skills 设计实践是其具体落地
- [[Claude Code可观测性实践]]：可观测性是验证闭环的基础设施，本项目第9节验证闭环与其衔接
- [[oh-my-claudecode多智能体编排]]：多智能体编排工具，本项目第7节 Subagents 提供了底层理解
- [[从Vibe Coding到Agentic Engineering]]：认知框架，本项目是从"Vibe"到"Engineering"的具体路径

## 澄清问题（可选）

**问:** 时间线？
**答:** 建议 3-4 周，可根据 Vibe Coding 学习进度灵活调整

**问:** 优先级？
**答:** 建议 P2（与 Vibe Coding 学习同级），但阶段2的 CLAUDE.md 优化可提前到 P1 执行，因为直接改善日常工作体验

**问:** 约束？
**答:**
- 需要 Claude Code 的实际使用环境来验证配置变更
- 部分实践（如 `/health` 检查）依赖网络安装第三方 Skill
- 知识卡片创建量较大（≥10 张），建议使用 `/research` 工作流批量处理

**问:** 是否创建新项目文件夹？
**答:** 建议创建 `20_项目/Claude-Code-工程实践/` 文件夹，因为预计会有项目笔记 + 配置参考文件 + 实践记录等多个文件
