---
product: Aluminum Heatsink with Fan (SKU 110991904)
vendor: seeed
platform: seeed_device
tags:
  - heatsink
  - fan
  - cable-length
  - a603
  - rma
  - accessory
date: 2026-08-14
source_links:
  - https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
  - https://jp.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
  - https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
  - https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
status: active
source_type: customer_attachment_plus_product_page
source_note: "Cable length 110±10mm from Seeed outline drawing attached by customer/Mouser as Figure 4 for SKU 110991904; body dims align with published ~58×39×17mm."
---

# 110991904 散热风扇线缆长度：110±10mm，短于下限可判规格不符

## 适用范围

- SKU **110991904**（Mouser **713-110991904**）：Aluminum Heatsink with Fan for Jetson Orin NX / Orin Nano / Xavier NX
- 常见投诉：装在 Orin NX 上、配合 **A603** 载板时，风扇线够不到 FAN 座

## 事实

| 项目 | 内容 |
| --- | --- |
| 产品 | 主动散热铝散热器+风扇，商详标注支持 Orin NX/Orin Nano/Xavier NX；文案强调与 **reComputer J401** 官方配套 |
| 线缆规格（外形图） | **电缆长 110±10 mm** → 合格范围 **100–120 mm** |
| A603 | Seeed 载板（SKU 102110840），带 FAN 连接器（5V PWM / PicoBlade） |
| 本案例实测 | 客户/Mouser：6 台均为 **95–97 mm**，低于下限 100 mm；装到 A603 后线缆到不了左侧 FAN 座 |

### 判定口径

1. 若外形图标注为 **110±10 mm**，则 **95–97 mm** 属于**尺寸规格不符（out of tolerance）**，可作为不良/换货技术依据转售后/RMA。
2. 客户此前同品号能接到 A603，说明目标用法合理；当前批次线偏短导致无法连接，与「装错料」不同——料号正确，线长不合规。
3. 「希望换偏规格上限的较长线」属于换货偏好，需 **RMA/仓库/质量** 执行，技术侧可转述，不自行承诺库存线长分布。

## 客服口径

### 内部 / 回复 Mouser 要点

- 确认零件号 **110991904** 正确。
- 按公开外形尺寸：**110±10 mm**；客户实测 **95–97 mm** → **低于下限，可视为规格不良**。
- 建议走渠道换货；换货时尽量选取符合规格、线长充足的批次。
- 具体 RMA 流程、交期交由售后/渠道同事处理。

### 禁止

- 不要说「线短但只要能凑合用就不算不良」。
- 不要承诺「一定发接近 120 mm 的最长线」除非仓库/质量确认。
- 不要把 J401 专用话术说成「A603 不支持该散热」——本案例问题是线长，不是载板型号错误。

## 来源

- 商详：https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
- A603 商详：https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
- A603 Wiki：https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
- 客户/Mouser 附件：SKU 110991904 outline dimensions drawing（电缆长 110±10 mm）
