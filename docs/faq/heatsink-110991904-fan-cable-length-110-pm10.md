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
  - https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf
  - https://www.switch-science.com/products/9229
  - https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
  - https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
status: active
source_note: "110±10mm confirmed on fan OEM drawing in Seeed-hosted heatsink_datasheet.pdf (DIMENSION page); customer/Mouser also attached Seeed-style assembly outline with same cable callout. No public PCN found for cable-length change on 110991904."
---

# 110991904 散热风扇线缆长度：110±10mm，短于下限可判规格不符

## 适用范围

- SKU **110991904**（Mouser **713-110991904**）：Aluminum Heatsink with Fan for Jetson Orin NX / Orin Nano / Xavier NX
- 常见投诉：装在 Orin NX 上、配合 **A603** 载板时，风扇线够不到 FAN 座

## 事实

| 项目 | 内容 |
| --- | --- |
| 产品 | 主动散热铝散热器+风扇，商详标注支持 Orin NX/Orin Nano/Xavier NX；文案强调与 **reComputer J401** 官方配套 |
| 线缆规格 | **110±10 mm**（合格 **100–120 mm**） |
| 公开规格出处 | Seeed 托管风扇规格书 [heatsink_datasheet.pdf](https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf) 第 5 页 DIMENSION：Total Cable Length **110±10 mm**（风扇本体引出线；型号 AD4010B05M-P09）。日本渠道 [Switch Science](https://www.switch-science.com/products/9229) 将该 PDF 挂为 110991904「データシート」 |
| 客户附图 | Mouser/客户另附「Seeed Studio 110991904 outline dimensions」装配外形图，同样标注电缆 **(110±10)**；该装配图**未**在 Seeed 英文商详公开附件区定位到同一文件名 |
| A603 | Seeed 载板（SKU 102110840），带 FAN 连接器（5V PWM / PicoBlade） |
| 本案例实测 | 客户/Mouser：6 台均为 **95–97 mm**（自散热壳体出口量到插头），低于下限 100 mm；装到 A603 后线缆到不了左侧 FAN 座 |

### 关于「是否发过 PCN / 是否改过长度」

| 核对项 | 结果 |
| --- | --- |
| 公开网页检索 Seeed PCN + 110991904 / heatsink / fan cable | **未找到** 针对该 SKU 线长变更的 PCN |
| 上述 `heatsink_datasheet.pdf` Revision History | 仅 Rev1（2022-10-28）与 Rev2（2022-11-01，Duty 相关），**无**线长变更记录 |
| 易混淆产品 | 另有停产/独立 SKU **114992746**「Xavier NX Heatsink **with Long Cable**」，是**另一料号**，不是 110991904 的 PCN 改长 |

**结论（公开资料）**：目前**不能**从公开渠道证实「曾发 PCN 把 110991904 线长改短/改长」。若内部有过变更，需 **PM / 质量 / 文档库** 人工核对。

### 资料来源不确定时的说明

代理（如 Mouser）之后往往还有日本零售/分销（Switch Science、秋月、マルツ等）。客户手中的「外形图」可能来自：

1. Seeed 托管风扇规格书（公开：含 110±10）；或  
2. 历史发给渠道的装配外形图 / 商详附件（本次未能在英文商详公开区复现同一装配 PDF）；或  
3. 渠道自行转存的旧资料。

技术回复可不纠缠文件来源：以 Seeed 托管规格书中的 **110±10** 为准；客户实测若可靠且低于 100 mm，仍可按规格不符处理。

### 判定口径

1. 按 **110±10 mm**，**95–97 mm** 属于**尺寸规格不符**，可作为不良/换货技术依据转售后/RMA。
2. 客户此前同品号能接到 A603，说明目标用法合理；当前批次线偏短，不是发错 SKU。
3. 「希望换偏规格上限的较长线」属换货偏好，需 **RMA/仓库/质量** 执行，技术不承诺库存线长分布。
4. 量测起点：客户从**散热壳体出口**量起；风扇 OEM 图从**风扇本体**量起。若仅争议量法，可请质量按图纸定义复核；即便如此，装配外形图若同样标 110±10，95–97 仍超差。

## 客服口径

### 内部 / 回复 Mouser 要点

- 确认零件号 **110991904** 正确。
- 公开规格：**110±10 mm**（见 Seeed 托管 heatsink_datasheet.pdf）；客户实测 **95–97 mm** → **低于下限，可视为规格不良**。
- 公开渠道**未找到**线长变更 PCN；不对外声称「已发 PCN 改过长度」，除非内部确认。
- 建议走渠道换货；具体 RMA 交售后/渠道。

### 禁止

- 不要说「线短但只要能凑合用就不算不良」。
- 不要承诺「一定发接近 120 mm 的最长线」除非仓库/质量确认。
- 不要把 J401 专用话术说成「A603 不支持该散热」。
- 不要把 **114992746 Long Cable** 型号说成是对本 SKU 的 PCN。

## 来源

- 商详：https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
- 风扇/散热规格书：https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf
- Switch Science（挂同一 PDF）：https://www.switch-science.com/products/9229
- A603 商详 / Wiki
- 客户/Mouser 附件：装配外形图（110±10 mm）+ 实测算尺图
