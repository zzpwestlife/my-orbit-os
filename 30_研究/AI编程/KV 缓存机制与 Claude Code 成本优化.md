---
area: "[[AI编程]]"
tags: [AI, Claude-Code, 缓存, Token, KV-Cache]
created: 2026-04-12
source: "[[搞懂缓存机制，从 Gemma4 到 Claude Code 省 80% Token.md]]"
---
# KV 缓存机制与 Claude Code 成本优化

## 核心发现

通过本地实验揭示 KV 缓存的工作原理：同一对话中，prompt 处理时间从 **30 秒降到 0.2 秒**，100 倍加速。

## KV 缓存原理

Transformer 注意力公式：`Attention(Q, K, V) = softmax(Q · Kᵀ / √d) · V`

- **Q (Query)**：当前新 token，每次不同，**不能缓存**
- **K (Key)**：历史 token 的索引，算完就固定，**可以缓存**
- **V (Value)**：历史 token 的内容，算完就固定，**可以缓存**

> KV 缓存就是把历史 token 的 Key 和 Value 存起来，新 token 只需要算自己的 Q，然后查已有的 KV。

### 模型大小与缓存收益

| 模型 | 未命中 | 命中 | 加速比 |
|------|--------|------|--------|
| Gemma 4 (4.5B active) | ~25,000ms | ~170ms | **148x** |
| Qwen3.5 (0.8B) | ~566ms | ~173ms | 3.3x |

**模型越大，KV 计算越昂贵，缓存收益越大。**

## Claude Code 的缓存工程

### Prompt 多层结构

```
Block 1: 计费归因头           → 不缓存
Block 2: CLI 前缀            → 不缓存
Block 3: 静态指令（行为规则）  → global 缓存（全球用户共享！）
── DYNAMIC_BOUNDARY ──
Block 4: 动态内容（CLAUDE.md） → org 缓存
Tools: 工具 schema            → session 内冻结
Messages: 对话历史             → 最后一条放 cache_control
```

### 两档 TTL
- **默认 5 分钟**：所有用户
- **扩展 1 小时**：Pro/Max 订阅用户

### 缓存断裂检测
监控 `cache_read_input_tokens`，如果比上次下降 >5% 且绝对值 >2000 tokens，判定为断裂。

## 省钱使用姿势

### ✅ 保护缓存
- **连续对话**：一个 session 持续对话
- **btw**：共享 session 共享缓存
- **CLAUDE.md**：配好就别动

### ❌ 破坏缓存
- **开新 session**：~20K tokens 全价重算
- **改 CLAUDE.md**：Block 4 起全部失效
- **加减 MCP 工具**：工具 schema 变化 = 断裂
- **切换模型**：完全失效（KV 张量不能互用）
- **/compact**：消息历史变了 = 断裂（>100K 再用）
- **发呆超 TTL**：1h 内说句话续命

### 费用对比
10 轮对话，系统提示词 20K tokens：
- 一个 session 持续对话：**1.9 份**
- 每次开新 session：**10 份**
- 差距：**5 倍**

## Sub-agent 缓存

Sub-agent **几乎不能复用**主线程缓存：
- 工具集不同 → 缓存前缀不同
- 消息历史完全独立
- 可能用不同模型

## 相关概念

- [[Claude Code]]
- [[Harness Engineering]]
- [[Claude Code 配置体系]]
