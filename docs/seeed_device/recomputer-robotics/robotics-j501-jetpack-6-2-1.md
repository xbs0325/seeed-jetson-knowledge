---
product: reComputer Robotics J501 / J501 Mini
vendor: seeed
platform: seeed_device
jetpack: "6.2.1"
l4t: "36.4.4"
tags:
  - recomputer-robotics
  - j501
  - agx-orin
  - flashing
  - gmsl
  - can
date: 2026-06-12
source_url: https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
status: active
---

# Seeed reComputer Robotics J501 / J501 Mini：JetPack 6.2.1 与接口要点

## 适用范围

- Seeed reComputer Robotics J501，搭配 Jetson AGX Orin 32GB/64GB 模组。
- Seeed Robotics J501 Mini carrier board，搭配 Jetson AGX Orin 32GB/64GB 模组。
- 适用平台类型：`seeed_device`。

## 系统与性能要点

- Seeed Wiki 标注 J501 与 J501 Mini 预装 JetPack 6.2.1 和 Linux BSP。
- J501/J501 Mini 面向机器人与工业边缘 AI，支持 NVIDIA Isaac ROS、ROS 2/1、Hugging Face、PyTorch 等软件栈。
- 搭配 Jetson AGX Orin 32GB/64GB 时，页面标注最高 275 TOPS（AGX Orin 64GB）AI 性能。
- Seeed Wiki 为 AGX Orin 32GB/64GB 分别提供 JetPack 6.2.1 镜像下载与 SHA256 校验值。

## J501 关键接口

- 1x 10GbE + 4x 1GbE。
- 2x M.2 Key M NVMe、M.2 Key E、M.2 Key B。
- 3x USB 3.0 Type-A、USB Type-C recovery、USB Type-C debug UART。
- 4x CAN-FD（2 native + 2 SPI-to-CAN），带电气隔离。
- 可选 GMSL2：页面规格列出 Mini-Fakra/GMSL2 扩展，可支持多路 GMSL2 摄像头方案。
- DI/DO、I2S、UART、RS485、HDMI 2.1、RTC、风扇与 19-48V DC 输入。

## J501 Mini 关键接口

- 1x 10GbE + 1x 1GbE。
- 1x M.2 Key M NVMe、M.2 Key E、M.2 Key B。
- 2x USB 3.2 Type-A、USB Type-C debug、USB Type-C recovery/debug。
- 2x CAN、DI、DO、I2S、RS485、UART。
- 可选 GMSL2：通过 camera expansion header / Mini-Fakra 扩展。
- 19-48V XT30 输入；页面建议使用 Seeed 官方推荐电源与配件，并按散热设计指南处理高负载散热。

## 刷机要点

- 使用物理 Ubuntu host PC、USB Type-C 数据线和对应 Seeed 镜像包；页面建议不要使用虚拟机。
- 进入 Force Recovery Mode 后，AGX Orin 32GB 应显示 `0955:7223 NVidia Corp`，AGX Orin 64GB 应显示 `0955:7023 NVidia Corp`。
- 解压 Seeed `mfi_xxxx.tar.gz` 镜像包后运行包内 initrd flash：

```bash
sudo ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs
```

- 镜像文件约 14.2GB，应使用 Seeed Wiki 提供的 SHA256 值核对完整性。

## 售后提示

J501/J501 Mini 是 Seeed 自定义机器人载板/整机方案，GMSL、CAN、DI/DO、RS485、以太网、电源与风扇等依赖 Seeed BSP 和设备树。客户询问是否可直接刷 NVIDIA AGX Orin Developer Kit 镜像时，应提示使用 Seeed 对应 Wiki 镜像和 flash 包。

## 相关链接

- [reComputer Robotics J501 Wiki](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
- [Robotics J501 Mini Wiki](https://wiki.seeedstudio.com/recomputer_j501_mini_getting_started/)
- [Seeed Linux_for_Tegra](https://github.com/Seeed-Studio/Linux_for_Tegra)
