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
3. **刷机**：OneDrive 替代百度；Recover（REC+RES/RST + Micro-USB）；包内示例  
   `cd JetPack_4.6_Linux_JETSON_XAVIER_NX_TARGETS` → `./nx.t506s.v1.3.flash.sh`（**v1.3 待核对**，以标签/包内脚本为准）。
4. **Wi‑Fi**：此前对外写过可自行 SMT 加装；跟进委婉收回——无经确认精确料号，建议售后寄回评估加装，勿再指导自购焊接。
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
