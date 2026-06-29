# Seeed Jetson 技术支持工作空间

本仓库供支持 Agent 使用：检索知识库、回答客户问题、记录结案、维护已核对的技术资料。人工客服也可通过 [`INDEX.md`](INDEX.md) 查阅已确认条目。

## 目录结构

| 路径 | 用途 |
|------|------|
| [`AGENTS.md`](AGENTS.md) | Agent 入口（每次对话先读） |
| [`instructions/`](instructions/) | 完整支持流程与规范 |
| [`memory/`](memory/) | 偏好、渠道约定等长期记忆 |
| [`INDEX.md`](INDEX.md) | 知识库索引（检索入口） |
| [`docs/`](docs/) | 已确认的技术资料与 FAQ |
| [`docs/staging/`](docs/staging/) | 待核实草稿，不可当最终答案 |
| [`cases/`](cases/) | 历次支持的结案记录 |

## 工作闭环

1. 你提出支持问题 → Agent 检索 `INDEX.md`，并外查 Seeed Wiki / NVIDIA 官方资料
2. Agent 给出答复，并标注置信度
3. 结案：写入 `cases/`；已核对结论进入 `docs/`，未核实的进入 `docs/staging/`
4. 开 draft PR，由你审核 merge
