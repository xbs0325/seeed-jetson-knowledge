---
date: 2026-08-04
channel: zoho
reply_to: customer
product: unknown (customer claims onboard eMMC failure)
issue_type: other
confidence: needs_review
final_customer_reply: true
resolved: partial
---

## 问题摘要

英文客户 Todd：购买的设备 eMMC 损坏，刷机出现 I/O error，进程进入不可中断睡眠（`ps` 显示 D+），请求保修更换 eMMC，并询问需要提供什么材料。

## 答复要点

- **归属**：保修 / 换货 / RMA → **售后**，技术支持不承诺是否在保、是否可换。
- **技术侧**：客户描述（刷机 I/O error + D+）与存储介质异常一致，但**不能据此断定硬件损坏**；且多数 Jetson 模组 eMMC 为焊装，现场「换 eMMC」通常不可行，售后路径一般为整机/模组返修或换新。
- **2026-08-04 追问：是否真坏？** → **当前不能确认 eMMC 已硬件损坏**。D+ 只表示进程在等 I/O；也可能是 Host/USB/板型/目标介质等问题。
- **用户确认下一步**：先向客户要 **SKU + 完整刷机日志**，暂不承诺保修结论。

## 外发英文要点

- 感谢反馈；需更多信息才能继续排查。
- 请提供：产品 SKU（或完整型号）、完整刷机日志（含 I/O error 前后）。
- 未承诺保修更换。

## 知识库更新

- [x] 无（本轮主要为售后转交；无新增可复用技术结论）
- [ ] `docs/faq/...`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://www.seeedstudio.com/get_help/ReturnsRefund
- https://aftersale.seeedstudio.com/home
- https://solution.seeedstudio.com/warranty-returns/
- https://www.nvidia.com/en-us/support/warranty/jetson-developer-kits-modules-tegra/

## PR

- cursor/case-emmc-warranty-rma-4434
