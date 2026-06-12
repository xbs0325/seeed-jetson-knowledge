# 知识库条目模板

## 已确认 FAQ / 设备资料（`docs/faq/`、`docs/seeed_device/` 等）

```yaml
---
product: <产品名>
vendor: seeed | nvidia | unknown
platform: seeed_device | official_kit | common
jetpack: "<版本>"
l4t: "<版本>"
tags: []
date: YYYY-MM-DD
source_url: https://...          # 主来源（必填）
source_links:                    # 补充链接（建议填）
  - https://...
status: active | need_review
---
```

正文建议结构：

- 问题 / 适用范围
- 简洁答案
- 注意事项
- 相关链接

## 收集草稿 — 有 Q&A（`docs/inbox/`）

```yaml
---
product: <产品>
platform: seeed_device | official_kit | common | unknown
tags: [inbox, collected]
date: YYYY-MM-DD
collected_at: YYYY-MM-DD
source_url: https://...          # 必填：原帖/视频/帖子
source_links: []
status: need_review
resolution: pending | promoted | rejected
---
```

## 社区开放问题（`docs/community_questions/`）

```yaml
---
product: <产品>
platform: unknown
tags: [community, open-question]
date: YYYY-MM-DD
first_seen: YYYY-MM-DD
last_checked: YYYY-MM-DD
source_url: https://...          # 必填
source_links: []
status: open | answered | stale | promoted
answer_url:                      # 若已有官方/可靠回复，填链接
---
```

正文：问题摘要、已知上下文、上次检查结论、下次检查建议。
