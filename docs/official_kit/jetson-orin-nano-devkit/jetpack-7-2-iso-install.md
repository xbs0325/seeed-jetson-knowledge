---
product: Jetson Orin Nano Developer Kit
vendor: nvidia
platform: official_kit
jetpack: "7.2"
l4t: "39.2"
tags:
  - flashing
  - iso
  - sdk-manager
  - qspi
  - nvme
date: 2026-06-10
source_url: https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/latest/setup_bsp.html
status: active
---

# Jetson Orin Nano Developer Kit：JetPack 7.2 ISO 安装方式

## 适用范围

- 产品：NVIDIA Jetson Orin Nano Developer Kit。
- 适用平台类型：`official_kit`。
- 不适用于 Seeed reComputer / reServer / Robotics 的直接刷机流程。

## 官方推荐路径

NVIDIA 在 JetPack 7.2 上推荐使用 Jetson ISO 做首次安装：

1. 在 Windows、macOS 或 Linux 电脑上把 Jetson ISO 写入 USB 闪存盘。
2. 将目标存储安装到开发套件上，可选 microSD 卡或 NVMe SSD。
3. 从 USB 安装介质启动，在开发套件上把 Jetson Linux 安装到目标存储。

## 重要前提

- JetPack 7.2 ISO 方式要求开发套件已有 JetPack 6.x generation 的 UEFI/QSPI firmware。
- 如果仍是旧出厂固件，必须先完成 JetPack 6.x update path。
- 从 JetPack 7.2 起，Jetson Orin Nano Developer Kit 不再提供 SD Card image。不要把 ISO 当作 SD 卡系统镜像写入 microSD；ISO 应写入 USB 盘，再由安装器把系统安装到 microSD 或 NVMe。

## 可选刷机方式

- NVIDIA SDK Manager：需要 Ubuntu 20.04 或 22.04 x86_64 host PC，可在 Force Recovery Mode 下刷机并安装 JetPack 组件。
- Flash script：适合自动化或高级用户，需在 Ubuntu x86_64 host PC 上使用 Jetson Linux Driver Package 与 sample root filesystem。

## 售后提示

客户如果反馈“下载不到 Orin Nano SD 卡镜像”，需确认客户是否在查 JetPack 7.2。JetPack 7.2 官方流程已改为 USB ISO 安装；旧版 JetPack 6.x 流程应按对应旧文档处理，不要混写。
