---
product: Seeed Jetson Xavier NX carrier boards and systems
vendor: seeed
platform: seeed_device
jetpack: "4.6 / 5.1.x"
l4t: "32.x / 35.x"
tags:
  - xavier-nx
  - carrier-board
  - availability
  - j202
  - j2012
  - t506s
date: 2026-07-14
source_links:
  - https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html
  - https://www.seeedstudio.com/reComputer-J2021-p-5438.html
  - https://www.seeedstudio.com/reComputer-Industrial-J2012-p-5685.html
  - https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
  - https://www.seeedstudio.com/A203-Carrier-Board-for-Jetson-Nano-Xavier-NX-V2-p-5214.html
  - https://wiki.seeedstudio.com/reComputer_J2021_J202_Flash_Jetpack/
status: active
---

# Seeed 是否还有支持 Jetson Xavier 系列的载板 / 整机？

## 适用范围

- 客户询问 Seeed 是否仍提供兼容 **Jetson Xavier NX**（以及 Nano / TX2 NX 等同代 SODIMM）的载板或整机。
- 常与 Mini AI Computer T506S、reComputer J202、Industrial J201x 一起出现。

## 事实

（商详状态随仓库变动；下述为 2026-07-14 公开页核对结果，**正式下单前须销售确认库存。**）

| 产品 | 形态 | Xavier 相关支持说明 | 公开页状态（核对日） |
| --- | --- | --- | --- |
| [reComputer J202 Carrier Board](https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html) SKU 102991695 | **独立载板** | Nano / Xavier NX / TX2 NX | 商详显示 In stock |
| [reComputer J2021](https://www.seeedstudio.com/reComputer-J2021-p-5438.html) SKU 110061381 | 整机（含 Xavier NX 8GB + J202 载板） | Xavier NX 8GB | 商详显示 In stock |
| [reComputer Industrial J2012](https://www.seeedstudio.com/reComputer-Industrial-J2012-p-5685.html) SKU 110110189 | 工业整机 | Xavier NX 16GB | 商详显示 In stock |
| [Mini AI Computer T506S](https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html) SKU 114110167 | 工业整机 | Xavier NX 8GB | 商详显示 In stock |
| [A203 / A203v2](https://www.seeedstudio.com/A203-Carrier-Board-for-Jetson-Nano-Xavier-NX-V2-p-5214.html) | 载板 | Nano / Xavier NX / TX2 NX | Out of stock / Discontinued |

- J202 Wiki 明确支持模组列表含 Xavier NX 8GB/16GB，刷机文档以 SDK Manager / L4T 为主（常见示例 JP4.6.1；整机商详亦见预装 JP5.1.1 描述）。
- J202 **不**等同 Orin 用的 Classic/Super J401；筛选器里「Orin NX, Orin Nano」是其他系列选项，不是 J202 本身支持 Orin。

## 推断

- Seeed **仍有**面向 Xavier 系列的载板（至少 J202）与整机（J2021、Industrial J2012、T506S）公开在售入口。
- 部分老型号（A203）已停产，不能对外笼统说「所有 Xavier 载板都还有」。
- Orin 已是主推线；Xavier 货源与模组采购周期可能不如 Orin 稳定，需销售确认交期。

## 建议

1. 客户要「单独买一块还能用 Xavier 的载板」→ 优先引导 **J202**（SKU 102991695），并提醒库存问销售。
2. 客户要整机替代 / 备机 → 按接口需求区分：开发向 J2021；工业 DI/DO/PoE 向 Industrial J201x；多 PoE NVR 向 T506S（或 Orin 代的 reServer Industrial）。
3. 客户若想从 Xavier **升级到 Orin** → 不要推荐往旧 Xavier 定制载板插 Orin；推荐选购 Orin 载板/整机（J401 / Super / Industrial / Robotics 等）。

## 禁止

- 禁止把「商详显示 In stock」写成对客户的库存保证。
- 禁止说 J202 支持 Orin NX/Nano。
- 禁止把 A203 当作当前可售推荐。

## 客服可复制回复

**内部 / 转销售：**

> 公开商详目前仍能看到 Xavier 相关产品：独立载板有 J202（102991695），整机有 J2021、Industrial J2012、T506S。A203 已停产。请帮忙确认实际库存和交期后再回客户。

**英文邮件可用短句（库存措辞保守）：**

> Seeed still lists Xavier NX–compatible options on our storefront, including the reComputer J202 carrier board and selected Xavier-based systems (for example J2021 / Industrial J2012 / T506S). Availability can change; our sales team will confirm stock and lead time. Note that J202 targets Xavier NX / Nano / TX2 NX and is not an Orin drop-in upgrade path.

## 相关链接

- [J202 Carrier Board](https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html)
- [J202 Wiki / Flash](https://wiki.seeedstudio.com/reComputer_J2021_J202_Flash_Jetpack/)
- [Industrial J2012](https://www.seeedstudio.com/reComputer-Industrial-J2012-p-5685.html)
- [T506S](https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html)
