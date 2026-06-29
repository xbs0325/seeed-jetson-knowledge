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
回复路由：[`instructions/reply-routing.md`](instructions/reply-routing.md)

## 每次回复前

1. **先判断回复对象**（用户内部 / 客户 / 淘宝买家 / 销售 / 同事或合作伙伴），按 [`reply-routing`](instructions/reply-routing.md) 决定输出格式
2. **判断场景**（电商 / Bazaar·附件 / 英文邮件 / 转交）；淘宝「官方核心模组」→ [`memory/workflow-notes.md`](memory/workflow-notes.md)
3. **检索** `INDEX.md` → `docs/faq`、`docs/seeed_device`、`docs/official_kit`、`docs/common`（仅 `active`）
4. **`docs/staging/`** 仅作参考，须标注待确认
5. **外查** Seeed Wiki / NVIDIA 官方（须实际打开页面）
6. **标置信度**（给用户内部判断用；客户话术可自然表达）

## 结案后（闭环）

1. 新增 [`cases/`](cases/) 记录
2. 已确认 → `docs/faq/` 等 + `status: active` + 更新 `INDEX.md`
3. 待确认 → `docs/staging/`
4. `docs/staging/` 经用户或可靠来源确认后 → 移入对应 `docs/faq`、`docs/seeed_device`、`docs/official_kit` 或 `docs/common`，并更新 `INDEX.md`
5. 「记住」→ `memory/`
6. 开 **draft PR**，不自行 merge

## 禁令

- 无依据不下技术结论；附件未核对不断言「没有资料」
- 非技术问题转交，不硬答
- 英文客户邮件默认先给内部建议，用户明确要求外发后再写客户邮件
- 淘宝 / 天猫回复必须短、口语、可复制，不输出长篇内部分析
- 条目写入知识库时 **必须含 `source_url` 或 `source_links`**；内部确认可写 `source_type: internal_confirmation`
