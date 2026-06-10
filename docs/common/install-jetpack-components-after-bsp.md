---
product: Jetson software stack
vendor: common
platform: common
jetpack: "6.x / 7.x"
l4t: "36.x / 39.x"
tags:
  - jetpack
  - cuda
  - tensorrt
  - sdk-components
  - apt
date: 2026-06-10
source_url: https://docs.nvidia.com/jetson/agx-orin-devkit/user-guide/latest/setup_jetpack.html
status: active
---

# BSP 已匹配后安装 JetPack SDK 组件

## 适用范围

- 已经刷入正确 BSP 并可正常启动的 Jetson 设备。
- 适用平台类型：`common`。
- 对 Seeed 设备，仅适用于已经使用 Seeed 对应型号镜像/BSP 启动后的 SDK 组件安装；不能替代 Seeed 刷机流程。

## 简要说明

JetPack 通常包含两层内容：

1. Jetson Linux BSP：bootloader、kernel、rootfs、驱动、设备树、板级支持。
2. SDK 组件：CUDA、cuDNN、TensorRT、VPI、Nsight、示例和其他开发包。

官方开发套件可通过 NVIDIA ISO、SDK Manager 或 flash script 安装 BSP。Seeed 设备应使用 Seeed 提供的镜像、BSP 或 Wiki 流程安装 BSP。只要 BSP 已经与设备硬件匹配，后续通常可以在设备端安装 JetPack SDK 组件。

## 常用命令

```bash
sudo apt update
sudo apt install nvidia-jetpack
```

## 注意事项

- 如果底层 BSP/设备树不匹配，安装 `nvidia-jetpack` 不会修复无法启动、外设缺失、GPIO/CAN 不工作等硬件适配问题。
- 新旧 JetPack/L4T 不要混装；先确认 `/etc/nv_tegra_release` 显示的 L4T 版本，再安装对应仓库中的组件。
- Seeed 设备售后应先确认使用的是 Seeed 对应型号镜像，尤其是 J401/J301、reServer Industrial、Robotics J401 等自定义载板。
