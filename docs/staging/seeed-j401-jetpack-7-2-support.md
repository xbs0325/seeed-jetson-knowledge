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
- 该信息不能自动推出 Seeed J401/J501 已支持 JetPack 7.2。
- Seeed J401、reComputer Super、Robotics J401 等页面目前明确可见的是 JetPack 6/6.2 或 JetPack 5.1.x 设备镜像与 BSP 信息。

## 人工复核事项

- Seeed 是否发布 J401/J501 的 JetPack 7.2 镜像、BSP、device tree、overlay、flash config。
- J401/J501 在 JetPack 7.2 上的 CAN、CSI/GMSL、GPIO、风扇、电源模式、M.2/PCIe、USB、以太网是否完成验证。
- 是否有官方 OTA 或从 JetPack 6.2 升级到 JetPack 7.2 的路径。

## 售后建议

在 Seeed 官方文档明确发布前，不要向客户承诺 Seeed J401/J501 可直接使用 NVIDIA JetPack 7.2 ISO 或官方开发套件刷机流程。可答复“JetPack 7.2 已发布，但 Seeed 设备需等待或核对对应 Seeed BSP/镜像”。
