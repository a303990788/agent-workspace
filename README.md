# Agent 联合工作区

这个仓库用于给多个 agent 和人类协作者提供同一个在线工作区。

它可以作为以下内容的统一事实来源：

- 项目共享背景
- 当前任务列表
- agent 任务归属
- 决策与假设
- 机器可读状态

## 文件说明

- `shared-context.md`：项目背景、目标和约束。
- `task-board.md`：任务队列、状态和负责人。
- `decisions.md`：长期有效的决策、假设和变更记录。
- `agent-protocol.md`：所有 agent 在读写前都应遵守的协作规则。
- `state.json`：机器可读的共享状态。

## Agent 启动流程

每个 agent 开始工作前，应该按顺序读取：

1. `agent-protocol.md`
2. `shared-context.md`
3. `task-board.md`
4. `decisions.md`
5. `state.json`

然后再认领一个明确的任务。

## URL 访问方式

如果这个工作区发布在 GitHub 上，agent 可以通过 raw URL 读取文件，例如：

```text
https://raw.githubusercontent.com/<owner>/<repo>/<branch>/shared-context.md
https://raw.githubusercontent.com/<owner>/<repo>/<branch>/task-board.md
https://raw.githubusercontent.com/<owner>/<repo>/<branch>/state.json
```

如果需要写入，优先使用 Pull Request 或带清晰说明的 commit。

