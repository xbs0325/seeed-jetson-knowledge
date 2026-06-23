---
date: 2026-06-23
channel: bazaar
product: reComputer Industrial R2045-12 (SKU 100080766)
resolved: yes
confidence: confirmed
---

## 问题摘要

英文客户 George Redpath（Lumen ID）询问 reComputer Industrial R2045-12（SKU 100080766）是否可将 TPM 作为选配订购，以及在 Seeed 网店未找到订购入口。Bazaar 客服 Viola 已转技术支持。

## 答复要点

- **已确认**：标准 SKU **100080766 不含 TPM**；规格表 Security 项「Encryption Chip TPM 2.0*」带 `*`，Wiki 声明带 `*` 项需按配件表另购。
- **已确认**：R2045-12 属于 R20xx（CM5）系列，载板支持 TPM，推荐配件为 **TPM 2.0 Module with Infineon SLB9670**，SKU **114993114**，SPI 接 **J26**。
- **已确认**：R2045-12 商详页仅有 AI Accelerator / Memory 配置及 LoRa、SSD 等「Also Add」，**无 TPM 下拉选项**——客户「在网店找不到如何订购」与当前页面设计一致。
- **订购建议**：单独搜索/下单 SKU **114993114**；需出厂预装或批量可联系 **industrial@seeed.cc** 或销售跟进（价格/库存转交销售）。
- **验证**：安装后 `ls /dev | grep tpm` 应见 `tpm0`。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/seeed_device/recomputer-industrial-r20xx/recomputer-industrial-r20xx-tpm-option.md`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/recomputer_industrial_r20xx_getting_start/
- https://www.seeedstudio.com/reComputer-Industrial-R2045-12-p-6544.html
- https://www.pi-shop.ch/recomputer-industrial-r2045-12（经销商页亦标注 Optional TPM）

## PR

- cursor/r2045-tpm-option-faq-4d0e
