# 知识条目模板

新建或重写 `docs/` 条目时优先使用本模板。旧条目无需一次性重写；高频 FAQ、容易混淆的兼容性问题、硬件接口问题优先按此结构整理。

## Frontmatter 建议

```yaml
---
product: 产品或产品线
vendor: seeed | nvidia | third_party | unknown
platform: seeed_device | official_kit | common | unknown
jetpack: "版本或范围"
l4t: "版本或范围"
tags:
  - faq
  - camera
  - flashing
date: YYYY-MM-DD
source_url: https://example.com
# 或：
source_links:
  - https://example.com/1
  - https://example.com/2
# 内部确认可用：
# source_type: internal_confirmation
# source_note: "谁/哪类团队确认了什么，按可记录范围写"
status: active | need_review
# staging 推荐补充：
# review_target: docs/faq | docs/seeed_device/<line> | docs/official_kit | docs/common
# review_reason: "为什么还需要复核"
# next_action: "确认后怎么处理"
---
```

## 正文结构

```markdown
# 标题

## 适用范围

- 适用产品、SKU、载板或模块。
- 明确不适用对象，尤其是 Classic / Super / Robotics / Industrial / reServer / H01 / A603 等容易混淆的产品线。

## 事实

- 只写资料、客户证据、官方页面、GitHub issue、内部确认明确支持的内容。
- 涉及版本、接口、SKU、价格、库存、发布状态时，说明是否需要外查最新信息。

## 推断

- 基于事实可以合理判断的内容。
- 推断不能写成确定结论；资料不足时写清楚还缺什么。

## 建议

- 客服可如何回答。
- 客户下一步该怎么做。
- 需要客户补充的 1-3 个关键信息。

## 禁止

- 不能承诺的内容。
- 不能混用的教程、刷机包、接口或产品线。
- 不能外发或容易误导的表达。

## 客服可复制回复（可选）

按场景提供短话术：淘宝/天猫、英文邮件、内部转交可分开写。

## 相关链接

- [资料名](https://example.com/)
```

## 写作原则

- 先短结论，后背景。
- 把事实、推断、建议、禁止分清楚。
- `active` 条目必须能支撑客服答复；不能只是一条线索。
- `need_review` 条目必须写 `review_target` 和 `next_action`，否则后续不知道怎么确认和归档。
- 高风险兼容性问题宁可写少，不要把理论支持写成已验证。
