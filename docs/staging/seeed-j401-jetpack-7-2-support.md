---
product: Seeed J401/J501 carrier boards
vendor: unknown
platform: unknown
jetpack: "7.2"
l4t: "39.2"
tags:
  - jetpack
  - seeed
  - j401
  - bsp
  - need-review
date: 2026-06-10
source_url: https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471
status: need_review
review_target: docs/faq
review_reason: "JetPack 7.2 support for Seeed J401/J501 requires official Seeed image/BSP confirmation."
next_action: "Check current Seeed Wiki/product pages and internal release status; promote only after Seeed JP7.2 BSP/image is confirmed."
---

# 待复核：Seeed J401/J501 是否支持 JetPack 7.2

## 适用范围

- Seeed J401/J501 carrier board 相关用户咨询。
- 适用平台类型：`unknown`，需人工复核。

## 背景

NVIDIA 已发布 JetPack 7.2 / Jetson Linux 39.2，并把 Jetson Orin 系列纳入 JetPack 7 release 线。Seeed 论坛有用户询问 J401/J501 carrier board 是否会发布官方 JetPack 7.2 镜像或 BSP。

## 当前可确认信息

- NVIDIA 官方 JetPack 7.2 支持 Jetson Orin family，并提供官方开发套件 ISO/SDK Manager/flash script 流程。
- 该信息不能自动推出 **所有** Seeed J401/J501 变体均可直接使用 NVIDIA 官方 DevKit ISO。
- **reComputer Industrial**：[Industrial Getting Started](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/) 已提供 **Jetpack7.2** 页签与 J4012/J4011/J301x mfi 下载；Seeed GitHub `Linux_for_Tegra` 分支 **`r39.2.0`** 含 Industrial board conf（`recomputer-industrial-orin-j401`）。
- Classic / Super / Robotics 等其他 J401/J501 形态仍需逐产品核对 Wiki / DevelopTool / 刷机选择器中的 L4T 39.2 条目。
- 从 JetPack 6.x 到 7.2 应完整刷机；跨大版本 `apt upgrade` 不推荐（[Flash and OTA to JP7.2](https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/)）。

## 人工复核事项

- Classic J401、Super、Robotics J401/J501 各自是否已在刷机选择器列出 JP7.2。
- 各产品线在 JP7.2 上的 CAN、CSI/GMSL、GPIO、风扇、电源模式、M.2/PCIe、USB、以太网验证状态。
- 是否有经产品确认的 JP6→JP7.2 OTA payload（当前文档强调多数场景用完整刷机）。

## 售后建议

- **Industrial J4012**：可引导客户使用 Seeed Industrial Wiki 的 JetPack 7.2 镜像 / `r39.2.0` BSP，**不要**改用 NVIDIA 官方 DevKit ISO。
- 其他 J401/J501：在 Wiki/DevelopTool 未列出该产品的 L4T 39.2 前，答复“需核对对应 Seeed BSP/镜像”，勿承诺 NVIDIA 官方 ISO 可直接刷入。
- Ubuntu 24.04 + PREEMPT_RT：见 [docs/faq/j4012-preempt-rt-kernel-ubuntu2404-jp72-r392.md](../faq/j4012-preempt-rt-kernel-ubuntu2404-jp72-r392.md)。
