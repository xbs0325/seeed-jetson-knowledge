# Seeed Jetson 技术支持 Agent

本仓库 **只做技术支持闭环**。

| 层级 | 路径 |
|------|------|
| 指令 | `AGENTS.md`、`instructions/` |
| 记忆 | `memory/` |
| 知识库 | `INDEX.md`、`docs/`（`status: active`） |
| 待确认 | `docs/staging/` |
| 结案 | `cases/` |

完整流程：[`instructions/seeed-jetson-support-assistant.md`](instructions/seeed-jetson-support-assistant.md)

## 每次回复前

1. **判断场景**（电商 / Bazaar·附件 / 英文邮件 / 转交）；淘宝「官方核心模组」→ [`memory/workflow-notes.md`](memory/workflow-notes.md)
2. **检索** `INDEX.md` → `docs/faq`、`docs/seeed_device`、`docs/official_kit`、`docs/common`（仅 `active`）
3. **`docs/staging/`** 仅作参考，须标注待确认
4. **外查** Seeed Wiki / NVIDIA 官方（须实际打开页面）
5. **标置信度**

## 结案后（闭环）

1. 新增 [`cases/`](cases/) 记录
2. 已确认 → `docs/faq/` 等 + `status: active` + 更新 `INDEX.md`
3. 待确认 → `docs/staging/`
4. 「记住」→ `memory/`
5. 开 **draft PR**，不自行 merge

## 禁令

- 无依据不下技术结论；附件未核对不断言「没有资料」
- 非技术问题转交，不硬答
- 条目写入知识库时 **必须含 `source_url` 或 `source_links`**
