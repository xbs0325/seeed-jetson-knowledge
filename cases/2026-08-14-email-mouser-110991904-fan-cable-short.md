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

- **已确认（技术）**：按外形图 **110±10 mm**，合格下限 **100 mm**；实测 **95–97 mm** → **规格不符 / 可判尺寸不良**。
- **已确认**：料号正确（散热风扇本体），问题是线长偏短，不是发错 SKU。
- **已确认**：A603 有 FAN 座；客户称以往同品号可插上，与本次线短现象一致。
- **需转交**：换货/RMA、是否能发偏长线批次 → **售后 / 质量 / 渠道（Mouser）流程**；技术不承诺线长偏好。
- 本轮仅内部建议，未生成外发英文。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/faq/heatsink-110991904-fan-cable-length-110-pm10.md`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://www.seeedstudio.com/Aluminum-Heatsink-with-Fan-for-Jetson-Orin-NX-Orin-Nano-Xavier-NX-Module-p-5633.html
- https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
- https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
- Mouser/客户附件：外形尺寸图（110±10 mm）、实测算尺图、A603 安装未达座照片

## PR

- cursor/heatsink-110991904-fan-cable-length-eda7
