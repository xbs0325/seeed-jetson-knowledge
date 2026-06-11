---
product: Jetson Orin modules and developer kits
vendor: nvidia
platform: official_kit
jetpack: "6.2.1"
l4t: "36.4.4"
tags:
  - jetpack
  - l4t
  - sdk-manager
  - docker
  - hsm
  - gpio
date: 2026-06-11
source_url: https://docs.nvidia.com/jetson/jetpack/release-notes/
status: active
---

# JetPack 6.2.1 / Jetson Linux r36.4.4 官方发布要点

## 适用范围

- NVIDIA Jetson Orin production modules and Developer Kits。
- 适用平台类型：`official_kit`。
- 这是 NVIDIA 官方 Jetson Linux/JetPack 维护版本资料；Seeed reComputer、reServer、Robotics、H01 等设备需另行核对 Seeed BSP、设备树和镜像。

## 关键信息

- JetPack 6.2.1 搭配 Jetson Linux 36.4.4，官方 release notes 标注 Jetson Linux r36.4.4 GA 为 2025-06。
- Jetson Linux 36.4.4 是可用于 production purposes 的 GA release，包含 Linux kernel 5.15、Ubuntu 22.04 rootfs、UEFI bootloader、NVIDIA drivers、firmware 和 toolchain。
- NVIDIA release notes 明确该版本支持 all Jetson Orin production modules and Developer Kits。
- 软件栈包含 CUDA 12.6.10、TensorRT 10.3.0、cuDNN 9.3.0、VPI 3.2、DLA 3.1、DLFW 24.0。
- 官方列出的维护更新包括：
  - 增加使用 Hardware Security Module (HSM) 签名 boot images 的支持。
  - 修复若干 SDK Manager 刷机小问题，提高刷机成功率。
  - 修复 JetPack 6.2 与 Docker v28.0.x 的兼容性问题。
  - Argus library 优化，官方称可降低最多 40% CPU 使用率。
  - 增加 GStreamer `nvunixfdsink` 和 `nvunixfdsrc` IPC plugins。

## 已知问题与售后提示

- r36.4.4 release notes 仍提示 `/sys/class/gpio` 已废弃，用户态 GPIO 应使用 GPIO character device API，例如 libgpiod。
- 官方提示同一设备多启动介质上的 BSP 版本应保持一致，不同 BSP 版本混刷可能导致 UEFI 崩溃。
- 若 initrd flash 过程中高速 USB 口出现解包/刷机失败，官方建议尝试在 host 与 target 之间加入 USB hub 或改用较低速 USB 口。
- 对 Seeed 设备，不能把 NVIDIA `jetson-orin-nano-devkit-super.conf`、SDK Manager 修复或 Docker 修复直接视为 Seeed 镜像已更新；需确认 Seeed 对应型号是否发布基于 36.4.4/6.2.1 的包。

## 售后提示

客户询问 JetPack 6.2 是否有修复 Docker 28 或 SDK Manager 刷机问题时，可说明 NVIDIA 官方 JetPack 6.2.1 / L4T 36.4.4 已包含相关修复；如果客户使用 Seeed 设备，只能作为版本背景，实际刷机或升级仍需以 Seeed Wiki/镜像/BSP 为准。
