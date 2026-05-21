# Agent 协作协议

## 目的

这个工作区用于协调多个不共享记忆、浏览器会话或本地文件的 agent。

所有 agent 都应该把这个仓库当作共享事实来源。

## 读取顺序

开始工作前，先读取：

1. `shared-context.md`
2. `task-board.md`
3. `decisions.md`
4. `handoffs.md`
5. `state.json`

## 主 Agent 与 Mira 协作流程

Codex 是当前主 agent。Mira 由 Codex 负责调度。

Codex 每次给 Mira 下达任务时，必须完成以下动作：

1. 在 `task-board.md` 中创建或更新对应任务。
2. 在 `handoffs.md` 中追加一条派发记录，写明任务 ID、目标、输入链接和期望产出。
3. 如果任务改变全局状态，同步更新 `state.json`。
4. Mira 返回结果后，在 `handoffs.md` 中追加反馈摘要、结果链接和下一步动作。
5. 根据反馈把 `task-board.md` 中的任务状态更新为 `done`、`blocked`、`needs_review` 或继续保持 `in_progress`。

Mira 不直接作为工作区最终裁决者。Mira 的输出需要由 Codex 汇总、确认并写回共享工作区。

## 认领任务

开始处理任务前：

1. 找到状态为 `todo` 或 `ready` 的任务。
2. 将任务状态改为 `in_progress`。
3. 将 `owner` 改成你的 agent 名称。
4. 添加一条简短的时间戳备注。

如果你没有写入权限，就在最终回复中明确说明你认领的任务 ID。

## 更新任务

完成工作后：

1. 将任务状态改为 `done`、`blocked` 或 `needs_review`。
2. 补充结果、链接和下一步动作。
3. 如果任务改变了全局状态，更新 `state.json`。
4. 如果产生了长期有效的决策，写入 `decisions.md`。

## 冲突规则

- 不要覆盖其他 agent 正在处理的任务。
- 不要删除其他 agent 留下的备注。
- 优先追加新信息，而不是重写历史；除非是在修正事实错误。
- 如果两个来源互相冲突，优先相信最新提交的内容，并在 `decisions.md` 记录冲突。

## 状态值

任务状态只能使用以下值：

- `todo`
- `ready`
- `in_progress`
- `blocked`
- `needs_review`
- `done`
- `canceled`

## 隐私

不要写入密钥、token、私密凭证、个人数据或敏感业务内容，除非这个仓库的访问权限明确允许。
