---
area: [[人工智能]]
tags: [AI编程, 开发范式, 软件工程]
created: 2026-03-05
---
# Agentic Engineering

## 定义

Agentic Engineering 是 Andrej Karpathy 在 2026 年 2 月提出的新概念，取代了过时的 [[Vibe Coding]]。它强调 AI 负责执行，人类负责架构、质量和正确性的协作模式。开发者 99% 的时间不再直接写代码，但需要更强的工程能力来监督和验证 AI 的输出。

## 要点

- **角色转变**：从代码编写者变为架构师和质量把控者
- **系统化监督**：建立完整的验证和测试流程
- **问题定义**：核心能力是把问题定义清楚
- **输出验证**：能够快速判断 AI 的输出是否正确

## 示例

**Vibe Coding vs Agentic Engineering**：

| 维度 | Vibe Coding | Agentic Engineering |
|------|-------------|---------------------|
| 角色定位 | AI 是助手 | AI 是执行者 |
| 人类职责 | 写代码 | 架构设计 + 质量把控 |
| 工作方式 | 随缘使用 | 系统化监督 |
| 核心能力 | 打字速度 | 问题定义 + 输出验证 |
| 时间分配 | 80% 写代码 | 99% 不写代码 |

**Agentic Engineering 的工作流**：

```
1. 需求分析和架构设计（人类）
   ↓
2. 将任务分解为清晰的子任务（人类）
   ↓
3. AI 执行具体的代码实现
   ↓
4. 自动化测试验证（AI + 人类设计的测试）
   ↓
5. 代码审查和质量把控（人类）
   ↓
6. 集成和部署（AI + 人类监督）
```

**实际案例**：

**传统开发**：
```python
# 开发者手写每一行
def calculate_discount(price, user_type):
    if user_type == "vip":
        return price * 0.8
    elif user_type == "member":
        return price * 0.9
    else:
        return price
```

**Agentic Engineering**：
```
开发者：定义需求和约束
- 需要一个折扣计算系统
- VIP 用户 20% 折扣
- 会员用户 10% 折扣
- 必须处理边界情况（负数、空值）
- 必须有单元测试覆盖
- 必须符合公司代码规范

AI：生成实现 + 测试 + 文档

开发者：验证
- 运行测试套件
- 检查边界情况
- 审查代码质量
- 确认符合架构设计
```

**关键能力转变**：

**不再重要**：
- 记住 API 参数
- 打字速度
- 语法细节

**变得关键**：
- 系统架构能力
- 问题分解能力
- 质量标准制定
- 快速验证能力
- 安全意识

## 相关概念

- [[Vibe Coding]]
- [[AI Agent]]
- [[Claude Code]]
- [[软件架构]]
- [[质量保证]]

## 参考资料

- [[从Vibe Coding到Agentic Engineering]]
- Andrej Karpathy 关于 Agentic Engineering 的定义（2026年2月）
- [[learn-claude-code架构拆解]]
