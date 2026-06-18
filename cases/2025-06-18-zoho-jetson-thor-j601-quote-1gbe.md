---
date: 2025-06-18
channel: other
product: Jetson AGX Thor / J601 / J501
resolved: partial
confidence: need_review
---

## 问题摘要

Ruhr-Universität Bochum（Thomas Becker）跟进工单 #356347 Jetson Thor 咨询：要求直接报价；询问是否用 SDK Manager；是否有 case；强调仅需 USB + Ethernet，夹爪需要 **1Gb Ethernet**（10GbE 等可能不支持）。Zibo 曾推荐即将推出的 J601（4× USB3.2 + 4× 10GbE），客户此前已拒绝 GMSL 方案。

## 答复要点

- 报价转 order@seeed.io / 销售；Thor Dev Kit SKU 100060965，官网单价约 $3,499，德国本地分销商约 €4,190。
- SDK Manager：Thor 官方 Dev Kit 以 JetPack 7 ISO 安装为主；Seeed J501/J601 用 Seeed BSP，非 SDK Manager 刷官方 kit 镜像。
- Case：Thor Dev Kit 含参考外壳；J601 仅为载板，无完整机箱。
- 1GbE：J501/J501 Mini 有专用 1GbE 但为 Orin；Thor Dev Kit 为 5GbE RJ45（可协商 1G，需与夹爪确认）；J601 10GbE 方案可能不满足夹爪 1GbE 硬需求。

## 知识库更新

- [x] `docs/staging/jetson-thor-j601-usb-1gbe-selection.md`
- [ ] `docs/faq/...`（active，待 J601 规格定稿）

## 来源

- Seeed Wiki J601 / J501
- NVIDIA Jetson AGX Thor Developer Kit User Guide
- https://www.seeedstudio.com/NVIDIA-Jetson-AGX-Thor-Developer-Kit-p-9965.html

## PR

- cursor/jetson-thor-j601-quote-a02a
