---
date: 2026-07-14
channel: zoho
product: Mini AI Computer T506S (SKU 114110167, Jetson Xavier NX 8GB)
customer: Robert Ranete
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户 T506S（Xavier NX 8GB）：Orin 升级、JetPack/BSP、Wi‑Fi 料号。

跟进（2026-07-15）：客户无法用百度网盘（需注册），要求 OneDrive/直链等；并索要 JP4.6.1 支持的精确 SMT Wi‑Fi 厂商与料号。

## 答复要点（最新）

1. **Orin**：不支持本机换模组。
2. **BSP**：Seeed 现网发 **JetPack 4.6.1**（OneDrive）。客户反馈包内多为注意事项、缺刷机教程。
3. **刷机文档补齐**：图为资源中心有公开材料——`Readme_T506S.pdf`（版本/网盘入口）+ 中英文手册（Recover：REC+RES/RST + Micro-USB OTG + `lsusb`）。完整烧录命令在**镜像包内刷机文件**，公开 PDF 不写死 `flash.sh` 行。OEM Readme 另列 JP5.1.1（V2.3）百度链，**对客是否承诺 JP5 待内部确认**。
4. **Wi‑Fi**：贴片；无精确料号；**不建议客户自行采购焊接**；转售后评估**寄回加装**。
5. **转交**：售后 RMA/寄回评估。

## 知识库更新

- [x] staging：刷机文档入口、Recover 步骤、JP5.1.1 待确认、Wi‑Fi RMA

## 来源

- 内部确认（代售 T506S；图为客服；JP4.6.1 包）
- https://www.twowinit.com/jetsonxaviernx11/441.html
- https://www.twowinit.com/web/userfiles/articlefile/systemos/Readme_T506S.pdf
- https://www.twowinit.com/web/userfiles/articlefile/userguide/T506S-E4-BD-BF-E7-94-A8-E8-AF-B4-E6-98-8E-E6-89-8B-E5-86-8C.pdf
- https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html

## PR

- cursor/t506s-xavier-carrier-support-923a
