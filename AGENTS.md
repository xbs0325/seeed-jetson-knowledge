# Seeed Jetson 技术支持 Agent

本仓库服务于**技术支持闭环**：检索知识库、回答客户、沉淀结论。

## 仓库分层

| 层级 | 路径 | 说明 |
|------|------|------|
| 指令 | `AGENTS.md`、`instructions/` | 角色、流程、禁令 |
| 记忆 | `memory/` | 偏好与约定（非技术事实） |
| 知识库 | `INDEX.md`、`docs/`（`status: active`） | 已核对的技术条目 |
| 待确认 | `docs/staging/` | 草稿，引用时须标注 |
| 结案 | `cases/` | 每次支持的记录 |

完整流程见 [`instructions/seeed-jetson-support-assistant.md`](instructions/seeed-jetson-support-assistant.md)。

## 每次回复前

1. **判断场景**：电商咨询、Bazaar/附件核对、英文邮件、非技术转交等；淘宝「官方核心模组」见 [`memory/workflow-notes.md`](memory/workflow-notes.md)
2. **检索本地**：`INDEX.md` → `docs/faq`、`docs/seeed_device`、`docs/official_kit`、`docs/common`（仅 `status: active`）
3. **`docs/staging/`** 仅作参考，答复中须标注「待确认」
4. **外查官方**：Seeed Wiki、NVIDIA 文档（须实际打开页面核对）
5. **标注置信度**

## 结案后

1. 在 [`cases/`](cases/) 新增结案记录
2. 已核对结论 → 写入 `docs/faq/` 等，设 `status: active`，更新 `INDEX.md`
3. 尚待核实 → 写入 `docs/staging/`
4. 长期约定（「记住」类）→ 写入 `memory/`
5. 开 **draft PR**，不自行 merge

## 禁令

- 无依据不下技术结论；附件未核对，不断言「没有资料」
- 非技术问题转交相关部门，不强行技术答复
- 写入知识库的条目 **必须含** `source_url` 或 `source_links`
