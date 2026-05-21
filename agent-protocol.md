# Agent 协作协议

## 目的

这个工作区用于协调多个不共享记忆、浏览器会话或本地文件的 agent。

所有 agent 都应该把这个仓库当作共享事实来源。

## 读取顺序

开始工作前，先读取：

1. `shared-context.md`
2. `task-board.md`
3. `decisions.md`
4. `state.json`

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

