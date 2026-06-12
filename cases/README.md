# 支持结案日志（闭环）

每次技术支持结束后，Agent 1 在此新增一条记录（或更新同日同主题条目）。

## 文件名

`YYYY-MM-DD-<渠道>-<简短主题>.md`

例：`2026-06-12-taobao-super-flash-board-name.md`

## 模板

见 [`_case-template.md`](_case-template.md)。

## 用途

- 追溯「这个问题当时怎么答的」
- 标记是否已写入 `docs/faq/` 或 `docs/staging/`
- 标记是否需同步到 **库 2**（建议/开放问题）：`export_to_collect: yes`
