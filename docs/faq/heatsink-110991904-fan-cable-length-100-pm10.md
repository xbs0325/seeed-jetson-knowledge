---
product: Aluminum Heatsink with Fan (SKU 110991904)
vendor: seeed
platform: seeed_device
jetpack: "N/A"
tags:
  - faq
  - heatsink
  - fan
  - cable-length
  - a603
  - accessory
date: 2026-08-17
source_links:
  - https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
  - https://jp.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
  - https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf
  - https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
  - https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
source_type: internal_confirmation
source_note: "2026-08-17 内部确认：110991904 风扇线规格应为 100±10 mm，外形图/规格书上的 110±10 mm 为文档写错，非生产问题。Mouser INV# 91599381 实测 95–97 mm 落在 90–110 mm 合格范围内。"
status: active
---

# 110991904 散热风扇线缆：正确规格 100±10 mm，图纸 110±10 为文档错误

## 适用范围

- SKU **110991904**（Mouser **713-110991904**）：Aluminum Heatsink with Fan for Jetson Orin NX / Orin Nano / Xavier NX
- 常见投诉：装在 Orin NX 上、配合 **A603** 载板时，风扇线够不到 FAN 座
- **不适用**：把图纸上的 **110±10 mm** 当成现行生产规格去判不良

## 事实

| 项目 | 内容 |
| --- | --- |
| 产品 | 主动散热铝散热器+风扇；商详支持 Orin NX / Orin Nano / Xavier NX，文案强调与 **reComputer J401** 官方配套 |
| **正确线缆规格（内部确认）** | **100±10 mm**（合格 **90–110 mm**） |
| 公开图纸仍写的数字 | Seeed 托管风扇规格书 [heatsink_datasheet.pdf](https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf) DIMENSION 页、以及渠道/客户手中的 110991904 外形图，仍标注 **110±10 mm** |
| 文档结论 | **110±10 mm 是规格书写错**，不是本批次生产不良 |
| A603 | SKU **102110840**，FAN 为 5V PWM / PicoBlade（W14） |
| 本案例实测 | Mouser / 京都大学：INV# **91599381**，6 台 **95–97 mm**，落在 **90–110 mm** 内 |

### 与公开图纸的关系

- 2026-08-14 曾按外形图 **110±10 mm**（下限 100 mm）把 95–97 mm 判为规格不符。
- 2026-08-17 **经确认**：生产规格是 **100±10 mm**；图纸数字错误。该口径覆盖本批及同 SKU 在库品，**不能**再按 110±10 判不良或走退货。

### A603 够不到座 ≠ 线长不良

- 商详官方配套写的是 **reComputer J401**，不是 A603。
- A603 的 FAN 座相对散热组件更远，**即使线长在 90–110 mm 内，装到 A603 仍可能偏紧或够不着**。
- 目录里没有「110991904 加长线」第二料号；**114992746**（Xavier NX Heatsink with Long Cable）是另一停产 SKU，**不能**当本料换货。

## 推断

- 客户称「以前同品号能接到 A603」，更可能是当时线长偏规格上限或走线更顺，不能据此要求整批复判为生产不良。
- 量测起点（壳体出口 vs 风扇本体）可能差几毫米；在已确认 100±10 的前提下，95–97 mm 仍在合格带内。

## 建议

1. **技术结论**：95–97 mm **符合** 100±10 mm；**非生产问题**，本批及渠道剩余库存都**不按尺寸不良退换**。
2. **A603 用法**：建议加 **4-pin PicoBlade（1.25 mm）风扇延长线**，使插头够到 A603 FAN 座。
3. **图纸**：公开资料仍写 110±10，对外说明「正确规格是 100±10，图纸数字有误」；改图交 **PM / 文档**，技术不承诺改图时间。
4. **退换货流程**：Mouser 问 claim / return 属售后/渠道，技术只给「不构成尺寸不良」的依据。

## 禁止

- 不要再说「95–97 mm 低于 110±10 下限，本批不良」。
- 不要对外写「再次确认 / upon further review 才发现写错」，用「经确认 / it has been confirmed」。
- 不要承诺「一定换成偏 110 mm 上限的长线」或「有加长版 110991904」。
- 不要用 **114992746** 换给 Orin NX + A603。
- 不要让客户剪线、改插头。
- 不要把 J401 配套说成「A603 不支持该散热」。

## 客服口径

### 回复渠道（Mouser 等）要点

- 经确认：正确规格 **100±10 mm**，不是图纸上的 **110±10 mm**。
- 95–97 mm 在 **90–110 mm** 内；**不是生产问题**，不按本批不良退货。
- 渠道剩余库存同样适用该规格。
- A603 仍可能偏紧，建议 4-pin PicoBlade（1.25 mm）延长线。
- claim / return 手续交售后/渠道；技术侧无尺寸不良依据。

## 相关链接

- [110991904 商详](https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html)
- [风扇规格书（图纸仍为 110±10）](https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf)
- [A603 商详](https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html)
- [A603 Wiki](https://wiki.seeedstudio.com/reComputer_A603_Flash_System/)
