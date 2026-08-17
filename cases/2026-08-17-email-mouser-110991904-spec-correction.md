---
date: 2026-08-17
channel: zoho
reply_to: customer
product: Aluminum Heatsink with Fan SKU 110991904 (Mouser 713-110991904)
issue_type: accessory
resolved: yes
confidence: confirmed
final_customer_reply: true
related_pr:
  - https://github.com/xbs0325/seeed-jetson-knowledge/pull/42
---

## 问题摘要

Mouser（Manuel Rosario）跟进 INV# **91599381** / SKU **110991904** 6 pcs：此前技术按外形图 **110±10 mm** 把实测 **95–97 mm** 判为不良。对方将检查剩余库存（约 **2,851** pcs），并询问如何 claim / return。

用户内部纠正：不是此批次生产问题，是规格书范围写错，应为 **100±10 mm** 而非 **110±10 mm**。外发不要写「再次确认」，只写「经确认」。

## 核对资料

- 商详：SKU 110991904，文案配套 reComputer J401。https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
- 公开风扇规格书 DIMENSION 仍为 **110±10 mm**：https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf
- A603（102110840）有 5V PWM / PicoBlade FAN：https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html 、https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
- 内部确认（2026-08-17）：正确规格 **100±10 mm**；图纸错误；非生产问题。95–97 mm ∈ 90–110 mm。

## 最终结论（内部）

1. **已确认**：正确线长 **100±10 mm**；图纸 **110±10** 为文档错误。
2. **已确认**：本批 95–97 mm **合格**；**不能**按不良退换；剩余库存同样不按本原因判不良。
3. A603 FAN 座更远，合格线长仍可能够不着 → 建议 4-pin PicoBlade（1.25 mm）延长线。
4. claim / return 流程属售后/渠道；技术只提供「不构成尺寸不良」。
5. 改公开图纸交 PM/文档。

## 知识库更新

- [x] `docs/faq/heatsink-110991904-fan-cable-length-100-pm10.md`（active）
- [x] 更新 `INDEX.md`
- [ ] 草稿 PR #42（`110±10` 判不良）应废弃，勿再合并

## 外发英文要点

- 经确认：规格为 **100 ± 10 mm**，不是图纸上的 **110 ± 10 mm**。
- 95–97 mm 在 90–110 mm 内；非生产问题，本批不按不良。
- 剩余库存同样适用。
- A603 仍可能偏紧，建议 PicoBlade 延长线。
- 不写「再次确认 / upon further review」。
