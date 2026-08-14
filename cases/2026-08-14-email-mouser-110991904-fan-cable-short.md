---
date: 2026-08-14
channel: zoho
reply_to: user_internal
product: Aluminum Heatsink with Fan SKU 110991904 (Mouser 713-110991904)
issue_type: accessory
resolved: partial
confidence: confirmed
final_customer_reply: false
---

## 问题摘要

Mouser（Manuel Rosario / Yuiho Takasu）转发京都大学客户投诉：发票 **91599381**，零件 **713-110991904 / 110991904**，**6 pcs**。装在 Jetson Orin NX + Seeed **A603** 上时风扇线够不到 FAN 座；6 台线长均为 **95–97 mm**，外形图为 **110±10 mm**；要求换较长线（尽量偏规格上限）。询是否正确零件、是否可判不良。

## 答复要点

- **已确认（技术）**：按外形图 / 风扇规格书 **110±10 mm**，合格下限 **100 mm**；实测 **95–97 mm** → **规格不符 / 可判尺寸不良**。
- **已确认**：料号正确（散热风扇本体），问题是线长偏短，不是发错 SKU。
- **已确认**：公开规格书出处：`https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf`（DIMENSION 页 110±10）；日本 Switch Science 挂为 110991904 数据手册。
- **未找到（公开）**：针对 110991904 **线长变更的 PCN**；风扇规格书修订记录仅有 Duty 相关 Rev2，无线长变更。另有独立 SKU **114992746 Long Cable**，勿当成对本料号的 PCN。
- **资料来源**：客户装配外形图未在英文商详公开区定位到同一文件；可能来自渠道转存/历史附件。代理后还有日本分销（如 Switch Science）。
- **需转交**：换货/RMA、是否曾内部改线长 → **售后 / 质量 / PM**；技术不承诺线长偏好。
- **处理建议（内部）**：本批可按尺寸不良；目录无加长线款 110991904；**不要**用 114992746 换 Orin NX。无整机可换时，可个案 **补发 1.25 mm PicoBlade 4P 延长线 ×6**（仓库/采购确认有料），不要让客户改线。
- 本轮仅内部建议，未生成外发英文。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/faq/heatsink-110991904-fan-cable-length-110-pm10.md`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
- https://files.seeedstudio.com/wiki/Orin_Nano_Fan/heatsink_datasheet.pdf
- https://www.switch-science.com/products/9229
- https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
- https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
- Mouser/客户附件：外形尺寸图（110±10 mm）、实测算尺图、A603 安装未达座照片

## PR

- cursor/heatsink-110991904-fan-cable-length-eda7
