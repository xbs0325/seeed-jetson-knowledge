---
product: NVIDIA Jetson AGX Orin 32GB H01 Kit
vendor: seeed
platform: seeed_device
jetpack: "5.0.2 / 5.1.1 / 5.1.4 / 6.0 / 6.1 / 6.2"
l4t: "35.x / 36.x"
tags:
  - agx-orin
  - h01
  - flashing
  - peripheral-drivers
  - emmc
date: 2026-06-11
source_url: https://wiki.seeedstudio.com/Jetson_AGX_Orin_32GB_H01_Flash_Jetpack/
status: active
---

# Seeed Jetson AGX Orin 32GB H01 Kit：刷 JetPack 与外设驱动

## 适用范围

- Seeed 销售/维护的 NVIDIA Jetson AGX Orin 32GB H01 Kit。
- 适用平台类型：`seeed_device`。
- 虽然产品名包含 NVIDIA Jetson AGX Orin，但该套件需要 Seeed 页面提供的板级外设驱动，不能简单归入 NVIDIA 官方开发套件流程。

## 关键信息

- Seeed Wiki 说明该 H01 Kit 预装 JetPack 5.1.4，默认用户名/密码为 `nvidia` / `nvidia`。
- 页面提示正常收到设备后可直接登录使用；系统损坏或需切换版本时再按刷机步骤重刷。
- Seeed Wiki 列出可下载的外设驱动版本：JP5.0.2/JP5.1.1、JP5.1.4、JP6.0、JP6.1、JP6.2。
- 刷机前需要先下载匹配 JetPack 版本的 peripheral drivers；这些驱动用于保证板上部分硬件外设正常工作。
- 进入 Force Recovery Mode：按住板上 recovery button 后接入电源，再用 USB Type-C 数据线连接 Ubuntu host。
- `lsusb` 出现 `0955:7223 NVIDIA Corp.` 表示设备已进入 recovery mode。

## 刷机边界

- Seeed 页面以 L4T 35.1 / 35.3.1 为示例说明 JP5.0.2 / JP5.1.1 刷机流程，并要求将 Seeed peripheral drivers 与 NVIDIA driver package 放在同一目录后合并。
- 示例刷写目标为 eMMC：

```bash
sudo ./flash.sh jetson-agx-orin-devkit mmcblk0p1
```

- 该命令出现在 Seeed H01 Kit 页面中，并不表示所有 Seeed AGX Orin 载板都可直接按 NVIDIA 官方开发套件流程处理；必须同时使用 Seeed 对应外设驱动和页面说明。

## 已知异常

- Seeed 页面记录：AGX Orin / NX Orin 在 JetPack 5.1.1 可能遇到 `ERROR: failed to read rcm_state`。
- 对该异常，页面提示需下载 NVIDIA Jetson Linux 35.3.1 页面底部的 `Overlay_PCN210361_PCN210100_r35.3.1.tbz2`，并在 apply binaries 前解压合并到 `Linux_for_Tegra`。

## 售后提示

客户询问 H01 Kit 能否用 SDK Manager 或官方 AGX Orin Dev Kit 资料直接重刷时，应先确认其设备为 Seeed H01 Kit，并按 Seeed Wiki 下载对应 peripheral drivers。若客户只是要恢复出厂系统，优先确认预装 JP5.1.4 信息、是否已有数据备份，以及目标 JetPack 版本是否在 Seeed 页面列出。
