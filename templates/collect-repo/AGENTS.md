# Seeed Jetson 收集 Agent

本仓库由 **Cursor Automation 每日定时**运行，**不回答客户**。

## 职责

- 收集官方 FAQ 变更、Discord/论坛**可验证** Q&A
- 记录**仅问题无答案**的开放帖
- 记录**产品建议**与体验反馈

## 写入

| 情况 | 路径 |
|------|------|
| 有可靠 Q&A | `inbox/` |
| 仅问题 | `community_questions/` |
| 建议/吐槽 | `feedback/suggestions/` |
| 缺陷/体验问题 | `feedback/issues/` |

每条 **必须** `source_url`。只开 **draft PR**，不 merge。

## 禁止

- 写入 `status: active` 或冒充已确认官方结论
- 修改本文件以外的 `instructions/` 除非用户要求

完整指令：`instructions/collector.md`
