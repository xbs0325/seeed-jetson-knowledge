---
product: Jetson AGX Orin Developer Kit
vendor: nvidia
platform: official_kit
jetpack: "7.2"
l4t: "39.2"
tags:
  - flashing
  - iso
  - sdk-manager
  - emmc
  - maxn-super
date: 2026-06-10
source_url: https://docs.nvidia.com/jetson/agx-orin-devkit/user-guide/latest/quick_start.html
status: active
---

# Jetson AGX Orin Developer Kit：JetPack 7.2 BSP 更新路径

## 适用范围

- 产品：NVIDIA Jetson AGX Orin Developer Kit。
- 适用平台类型：`official_kit`。
- 不适用于 Seeed AGX/Orin 载板或整机的直接刷机流程，除非 Seeed 文档明确说明。

## 官方流程摘要

- JetPack 7.2 是 Jetson AGX Orin Developer Kit 的当前官方 release，包含 L4T r39.2。
- NVIDIA 推荐先完成 eMMC 中预装系统的首次启动，再使用 Jetson ISO 更新到最新 BSP。
- Jetson ISO 使用 USB 安装盘，不要求 Ubuntu host PC。
- AGX Orin Developer Kit 可安装到 eMMC；也可按官方文档选择 NVMe 等目标存储。

## 版本前提

- Jetson ISO 可把 AGX Orin Developer Kit 从 L4T r35.5 或更高版本更新到 L4T r39.2。
- 如果开发套件低于 L4T r35.5，应先通过 NVIDIA SDK Manager 在 Linux host 上更新到 r35.5 或更高，再走 ISO 流程。

## JetPack 组件安装

当 BSP 已更新到 L4T r39.2，系统可直接在 Jetson 上安装 JetPack 组件：

```bash
sudo apt update
sudo apt install nvidia-jetpack
```

## 售后提示

客户询问 AGX Orin 32GB Super Mode 时，可说明 JetPack 7.2 新增 MAXN_SUPER，官方发布信息标注 AI 性能从 200 TOPS 提升到 241 TOPS。实际功耗、散热与电源能力仍需按 NVIDIA 官方开发套件条件确认。
