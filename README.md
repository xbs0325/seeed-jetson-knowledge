# Seeed Jetson 技术支持工作空间

本仓库 **仅服务技术支持闭环**：与你对话的 Agent 答客户、结案沉淀、维护已确认知识库。

## 结构

| 路径 | 用途 |
|------|------|
| [`AGENTS.md`](AGENTS.md) | Agent 入口指令 |
| [`instructions/`](instructions/) | 完整支持流程 |
| [`memory/`](memory/) | 偏好与约定（短） |
| [`INDEX.md`](INDEX.md) | 知识库索引 |
| [`docs/`](docs/) | 已确认资料与 FAQ |
| [`docs/staging/`](docs/staging/) | 待确认的草稿 |
| [`cases/`](cases/) | 每次支持的结案记录 |

## 闭环

1. 你发起支持问题 → Agent 检索 `INDEX` + 外查 Wiki  
2. 给出答复（标置信度）  
3. 结案：写 `cases/` + 必要时更新 `docs/faq` 或 `docs/staging`  
4. 开 draft PR，由你 merge  
