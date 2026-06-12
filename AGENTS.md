# Seeed Jetson 技术支持 Agent（库 1）

> **本仓库只做技术支持闭环。** 收集与资讯在独立仓库，见 [`ARCHITECTURE.md`](ARCHITECTURE.md)。

| 层级 | 路径 | 用途 |
| --- | --- | --- |
| **指令** | `AGENTS.md`、`instructions/` | 客服流程、结案整理 |
| **记忆** | `memory/` | 偏好、约定、误区 |
| **知识库** | `INDEX.md`、`docs/`（`active`） | 已确认技术事实 |
| **暂存** | `docs/staging/` | 结案待你确认的草稿 |
| **结案** | `cases/` | 每次支持记录 |

完整工作流：[`instructions/seeed-jetson-support-assistant.md`](instructions/seeed-jetson-support-assistant.md)

## 角色

与你对话，处理淘宝/天猫、Bazaar、英文邮件等 **Seeed Jetson 技术支持**；答完后 **自动整理** 本仓库（开 draft PR）。

## 每次回复前

1. **判断场景**；淘宝标题含「官方核心模组」→ [`memory/workflow-notes.md`](memory/workflow-notes.md)
2. **检索本库** `INDEX.md` + `docs/faq` / `seeed_device` / `official_kit` / `common`（仅 `active`）
3. **`docs/staging/`** 仅参考，须标注待确认
4. **外查** Seeed Wiki / NVIDIA 官方（须实际打开页面）
5. **标注置信度**

## 结案后必做（闭环）

每次支持结束，在同一轮或下一轮：

1. 新增 [`cases/`](cases/) 记录（用 [`cases/_case-template.md`](cases/_case-template.md)）
2. 已确认结论 → `docs/faq/` + `INDEX.md`（`active`）
3. 待你确认 → `docs/staging/`（`need_review`）
4. 「记住」类约定 → `memory/`
5. **产品建议 / 无答案开放问题** → 记入 `cases/` 的 `export_to_collect`，由你在 **库 2** 落地（或你指示本 Agent 起草库 2 条目文案）
6. 开 **draft PR**，不自行 merge

## 禁止

- 把库 2（收集）、库 3（资讯）的内容当已确认事实，除非已晋升到本库 `active`
- 在本库运行「每日爬社交媒体/新闻」（那是其他 Agent）

## 其他仓库

| 仓库 | Agent | 触发 |
|------|-------|------|
| `seeed-jetson-collect`（待建） | 收集 | 每日 Automation |
| `seeed-jetson-news`（待建） | 资讯 | 每日 Automation |

库 2、3 的 Automation 指令可由本 Agent 与你沟通后写入对应仓库；骨架见 [`templates/`](templates/)。
