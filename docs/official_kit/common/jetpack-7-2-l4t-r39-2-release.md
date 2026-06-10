---
product: Jetson Orin family
vendor: nvidia
platform: official_kit
jetpack: "7.2"
l4t: "39.2"
tags:
  - jetpack
  - l4t
  - cuda
  - tensorrt
  - iso
date: 2026-06-10
source_url: https://developer.nvidia.com/embedded/jetpack/downloads
status: active
---

# JetPack 7.2 / Jetson Linux r39.2 官方发布要点

## 适用范围

- NVIDIA 官方 Jetson Orin 系列开发套件与官方支持硬件。
- 适用平台类型：`official_kit`。
- 不应直接套用为 Seeed 盒子/载板的刷机方案；Seeed 设备需使用对应 Seeed BSP、镜像或 Wiki。

## 关键信息

- JetPack 7.2 搭配 Jetson Linux 39.2，发布日期页面标注 Jetson Linux 39.2 为 2026-06-02。
- 软件栈包含 Ubuntu 24.04 rootfs、Linux kernel 6.8、CUDA 13.2.1、cuDNN 9.20.0、TensorRT 10.16.2、VPI 4.1.3、DeepStream 8.0。
- JetPack 7.2 将 Jetson Orin 系列纳入 JetPack 7 release 线。
- 官方引入统一 ISO 安装方式，面向 Jetson Orin 与 Jetson Thor 开发套件。
- Jetson AGX Orin 32GB 新增 MAXN_SUPER，AI 性能从 200 TOPS 提升到 241 TOPS。
- Jetson Orin Nano Developer Kit 不再提供 SD Card image；需使用统一 ISO 写入 USB 盘作为安装介质。

## 支持与注意事项

- 官方下载页列出的支持硬件包括 Jetson AGX Thor Developer Kit、Jetson T5000/T4000 与 Jetson Orin Family。
- 对官方开发套件，可按 NVIDIA Getting Started / BSP Setup 使用 ISO、SDK Manager 或 manual flash。
- 对 Seeed reComputer、reServer、Robotics 等设备，不能用此条目替代 Seeed BSP；仅可作为 JetPack/L4T 版本背景参考。

## 售后提示

客户询问“最新 JetPack 是多少”时，可答复 JetPack 7.2 / L4T 39.2 已发布；若客户使用 Seeed 设备，应继续核对 Seeed 对应型号是否已有官方镜像或 BSP，不要承诺 NVIDIA 官方 ISO 可直接刷入 Seeed 载板。
