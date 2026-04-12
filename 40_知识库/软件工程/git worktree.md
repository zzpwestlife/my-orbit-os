---
area: [[软件工程]]
tags: [版本控制, Git, 并行开发]
created: 2026-03-05
---
# git worktree

## 定义

git worktree 是 Git 的一个功能，允许你在同一个仓库中同时检出多个分支到不同的物理目录。每个 worktree 都是一个独立的工作目录，但共享同一个 .git 仓库，可以在不同的分支上并行工作而互不干扰。

## 要点

- **物理隔离**：每个 worktree 是独立的目录，文件修改互不影响
- **共享仓库**：所有 worktree 共享同一个 .git 数据库
- **并行开发**：可以同时在多个分支上工作
- **安全实验**：在隔离环境中测试，不影响主工作区

## 示例

**创建 worktree**：
```bash
# 在主仓库中
git worktree add ../feature-branch feature-branch

# 目录结构
/project/              # 主工作区（main 分支）
/project-feature/      # worktree（feature-branch 分支）
```

**在 AI Agent 中的应用**：

**问题场景**：
- Agent 在当前目录下修改代码
- 一旦改坏了很难回滚
- 多个 Agent 同时工作会相互干扰

**解决方案**：
```python
# Agent 接收任务时
def handle_task(task_id):
    # 自动创建独立的 worktree
    worktree_path = f".claude/worktrees/{task_id}"
    subprocess.run([
        "git", "worktree", "add",
        worktree_path,
        "-b", f"task-{task_id}"
    ])

    # 在隔离环境中工作
    os.chdir(worktree_path)
    # ... Agent 执行任务 ...

    # 完成后可以选择
    # 1. 合并到主分支
    # 2. 直接删除（如果失败）
```

**优势**：
- **安全性**：改坏了直接删除 worktree，不影响主代码
- **并行性**：多个 Agent 可以同时处理不同任务
- **可追溯**：每个任务都有独立的分支历史
- **易回滚**：失败的实验不会污染主分支

**实际案例（Claude Code）**：
- Agent 接收到重构任务
- 自动创建 worktree：`.claude/worktrees/refactor-auth`
- 在隔离环境中进行重构
- 测试通过后合并，失败则删除 worktree

## 相关概念

- [[Git]]
- [[版本控制]]
- [[AI Agent]]
- [[任务隔离]]

## 参考资料

- [[learn-claude-code架构拆解]]
- Git 官方文档：git-worktree
