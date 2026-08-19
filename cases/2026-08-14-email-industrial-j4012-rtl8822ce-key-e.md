---
date: 2026-08-14
channel: zoho
reply_to: customer
product: reComputer Industrial J4012 (SKU 110110191)
issue_type: accessory
resolved: yes
confidence: confirmed
final_customer_reply: true
---

## 问题摘要

渠道客户 PT. Solusi Rekatama Persada（订单 PO 005 VII SRP 2026 / Invoice S2607060007）询问 **reComputer Industrial J4012**（邮件写 SKU 1101110191，官方为 **110110191**）是否可连接 **RTL8822CE M.2 Key-E** Wi-Fi 模组；客户已观察到底板无 Key-E，规格写 Support SMD Wi-Fi/Bluetooth。销售 Dancy Dong 转发技术支持处理。

## 答复要点

- **已确认**：Industrial 载板**无 M.2 Key-E**，不能直接插 RTL8822CE。
- **已确认**：规格中的 Wi-Fi 指 PCB 预留 **SMD 焊接**位；官方示例 **BL-M8723DU1**；不建议客户自行焊接（易损坏且保修失效）；可走定制。
- **已确认**：RTL8822CE Wiki 面向 **Classic** reComputer J4012（有 Key-E），勿与 Industrial 混用。
- 用户确认后已生成外发英文邮件；按反馈去掉「Wiki 写明」表述，仅保留硬件参考链接；定制跟进改为「如需将转接对应部门」，不写销售跟进。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/faq/recomputer-industrial-j4012-wifi-no-m2-key-e.md`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
- https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
- https://www.seeedstudio.com/reComputer-Industrial-J4012-p-5684.html
- https://www.seeed.cc/product/recomputer-industrial-fanless-edge-ai-device-with-jetson-module
- https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/
- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/

## PR

- cursor/industrial-j4012-wifi-key-e-eda7
