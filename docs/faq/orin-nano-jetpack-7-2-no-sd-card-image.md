---
product: Jetson Orin Nano Developer Kit
vendor: nvidia
platform: official_kit
jetpack: "7.2"
l4t: "39.2"
tags:
  - faq
  - flashing
  - sd-card
  - iso
date: 2026-06-10
source_url: https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/latest/setup_bsp.html
status: active
---

* 问题
  * JetPack 7.2 为什么找不到 Jetson Orin Nano Developer Kit 的 SD 卡镜像？
* 适用产品
  * NVIDIA Jetson Orin Nano Developer Kit
* 适用平台类型：official_kit
* 简洁答案
  * JetPack 7.2 官方不再为 Orin Nano Developer Kit 提供 SD Card image。应把 Jetson ISO 写入 USB 闪存盘，再由安装器把 Jetson Linux 安装到 microSD 或 NVMe SSD。
* 注意事项
  * 不要把 ISO 当作 SD 卡系统镜像直接写到 microSD。
  * 使用 JetPack 7.2 ISO 前，开发套件需要 JetPack 6.x generation UEFI/QSPI firmware。
  * 此 FAQ 不适用于 Seeed reComputer/reServer/Robotics 刷机。
* 相关链接
  * [Jetson Orin Nano Developer Kit BSP Setup](https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/latest/setup_bsp.html)
  * [JetPack SDK Downloads and Notes](https://developer.nvidia.com/embedded/jetpack/downloads)
