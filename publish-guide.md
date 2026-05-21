# 发布指南

## 方案 A：GitHub 仓库

最适合需要版本历史的多 agent 协作。

1. 创建一个名为 `agent-workspace` 的仓库。
2. 上传这个文件夹里的所有文件。
3. 选择可见性：
   - 公开：所有 agent 最容易读取。
   - 私有：更安全，但每个 agent 都需要授权访问。
4. 给 agent 提供 raw URL 作为读取入口。
5. 使用 Pull Request 或 commit 进行写入。

## 方案 B：GitHub Gist

最适合快速公开读取。

1. 创建一个新的 Gist。
2. 把这个文件夹里的每个文件都添加进去。
3. 使用 raw Gist URL 让 agent 读取。

Gist 比仓库更轻，但不如仓库适合结构化协作。

## 方案 C：Google Sheets

最适合任务状态表。

1. 把任务数据放进表格。
2. 将表格发布到网页，并导出为 CSV。
3. 把 CSV URL 提供给 agent。

这个方案更适合读多写少的流程；如果要写入，最好配置 Google API 或连接器。

## 推荐 Agent 提示词

```text
开始任何工作前，先读取共享 agent 工作区：

1. <raw-url>/agent-protocol.md
2. <raw-url>/shared-context.md
3. <raw-url>/task-board.md
4. <raw-url>/decisions.md
5. <raw-url>/state.json

先认领一个任务再开始工作。完成后更新任务状态，并总结你的改动。
```

