---
product: Jetson Orin family
vendor: nvidia
platform: official_kit
jetpack: "6.2.2"
l4t: "36.5"
tags:
  - jetpack
  - l4t
  - security
  - docker
  - apt
date: 2026-06-12
source_url: https://developer.nvidia.com/embedded/jetpack-sdk-622
status: active
---

# JetPack 6.2.2 / Jetson Linux r36.5 官方发布要点

## 适用范围

- NVIDIA Jetson AGX Orin、Jetson Orin NX、Jetson Orin Nano 官方支持模组与官方开发套件。
- 适用平台类型：`official_kit`。
- 对 Seeed reComputer、reServer、Robotics 等设备，仅可作为 NVIDIA 官方版本背景；不能直接替代 Seeed 镜像、BSP、设备树或升级流程。

## 关键信息

- JetPack 6.2.2 搭配 Jetson Linux 36.5，是 JetPack 6 的生产版本更新。
- Jetson Linux 36.5 release notes 标注为 2026-02 发布，支持所有 Jetson Orin production modules and Developer Kits。
- BSP 基础为 Linux kernel 5.15、Ubuntu 22.04 rootfs、UEFI bootloader、NVIDIA drivers、firmware 与 toolchain。
- NVIDIA 页面说明 JetPack 6.2.2 主要包含 known issues 与 security vulnerabilities 修复。
- JetPack 6.2.2 与 JetPack 6.2.1 使用同一代 compute stack：CUDA 12.6、TensorRT 10.3、cuDNN 9.3、VPI 3.2、DLA 3.1、DLFW 24.0。
- 官方说明 JetPack 6.2.2 支持 Jetson Platform Services 2.0。

## 官方安装/升级边界

- Jetson Orin Nano Developer Kit 的 SD Card 方法：先使用 JetPack 6.2.1 / Jetson Linux 36.4.4 SD 卡镜像，再通过 APT 升级到 JetPack 6.2.2 / Jetson Linux 36.5。
- 官方开发套件还可使用 SDK Manager 或 manual flash；具体步骤以 NVIDIA 对应 Developer Guide 为准。
- 对 Seeed 设备，NVIDIA 官方 `r36.5` APT/dist-upgrade 流程不能默认直接使用；应走 Seeed 安全升级路径（见下）。

## Seeed 设备（J401 等）安全升级至 6.2.2

- Seeed 已发布 [Linux_for_Tegra r36.5.0](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0)（`seeed-linux-bsp-upgrader` + upgrade bundle），用于 R36.x → R36.5.0 同大版本升级。
- **售后首推**：[Seeed Jetson Developer Tool](https://github.com/Seeed-Projects/Seeed-Jetson-DevelopTool) 的 **OTA Update** 引导流程（SSH 连接 → 选产品 → 按向导升级）。
- **备选**：设备端手动安装 upgrader 后再 `apt upgrade`（Release 页 SOP）。
- 详见本仓库 [J401 安全升级至 6.2.2 FAQ](../faq/j401-safe-upgrade-jetpack-6-2-2-r365.md)。

## 售后提示

客户问“JetPack 6 最新小版本是多少”时，可答 JetPack 6.2.2 / L4T 36.5 已发布，主要是安全与已知问题修复。若客户使用 Seeed J401 等载板/整机，引导 **DevelopTool OTA 或 r36.5.0 upgrader**，不要照搬 NVIDIA 官方 DevKit 裸 `apt upgrade` 命令。

## 相关链接

- [NVIDIA JetPack 6.2.2 页面](https://developer.nvidia.com/embedded/jetpack-sdk-622)
- [Jetson Linux 36.5 页面](https://developer.nvidia.com/embedded/jetson-linux-r365)
- [Jetson Linux r36.5 Release Notes](https://docs.nvidia.com/jetson/archives/r36.5/ReleaseNotes/Jetson_Linux_Release_Notes_r36.5.pdf)
