---
date: 2026-08-04
channel: zoho
reply_to: user_internal
product: unknown (customer claims onboard eMMC failure)
issue_type: other
confidence: needs_review
final_customer_reply: false
resolved: partial
---

## 问题摘要

英文客户 Todd：购买的设备 eMMC 损坏，刷机出现 I/O error，进程进入不可中断睡眠（`ps` 显示 D+），请求保修更换 eMMC，并询问需要提供什么材料。

## 答复要点

- **归属**：保修 / 换货 / RMA → **售后**，技术支持不承诺是否在保、是否可换。
- **技术侧**：客户描述（刷机 I/O error + D+）与存储介质异常一致，但**不能据此断定硬件损坏**；且多数 Jetson 模组 eMMC 为焊装，现场「换 eMMC」通常不可行，售后路径一般为整机/模组返修或换新。
- **2026-08-04 追问：是否真坏？** → **当前不能确认 eMMC 已硬件损坏**。D+ 只表示进程在等 I/O，常见也可能是：目标介质搞错（Orin Nano/NX 常无板载 eMMC，实际是 NVMe）、Host 用虚拟机/劣质 USB 线/Hub、Recovery 不稳、镜像/板型参数错误、供电不足、电源或 USB 中途断开。需完整刷机日志 + 型号后再判断；仅在换 Host/线材/正确板型后仍对 `mmcblk0` 稳定报错时，才更倾向硬件。
- **关键缺口**：未提供产品型号 / SKU、订单号、购买渠道与日期、错误截图/日志、序列号。
- **公开入口（供客服转交）**：
  - Returns & Warranty：https://www.seeedstudio.com/get_help/ReturnsRefund（联系 `order@seeed.io` 申请授权）
  - Aftersale Platform：https://aftersale.seeedstudio.com/home（在线申请维修/换货）
  - 一般质保期公开表述约自交付起 12 个月（以订单条款与售后最终判定为准）

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
