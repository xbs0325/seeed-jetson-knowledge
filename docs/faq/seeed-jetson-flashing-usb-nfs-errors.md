---
product: Seeed Jetson devices
vendor: seeed
platform: seeed_device
jetpack: "5.x / 6.x"
l4t: "35.x / 36.x"
tags:
  - faq
  - flashing
  - usb
  - nfs
  - recovery
date: 2026-06-11
source_url: https://wiki.seeedstudio.com/usb_timeout_during_flash/
status: active
---

* 问题
  * Seeed Jetson 设备刷机时 USB timeout、NFS mount failure、`tegrarcm_v2` 找不到或首次启动卡在 OEM 配置怎么办？
* 适用产品
  * Seeed reComputer、reServer、reComputer Industrial、reComputer Robotics、Jetson AGX Orin H01 Kit 等 Seeed Jetson 设备
* 适用平台类型：seeed_device
* 简洁答案
  * 先确认 host 系统和 JetPack 版本匹配：JetPack 5.x 推荐 Ubuntu 18.04/20.04，JetPack 6.x 推荐 Ubuntu 20.04/22.04。优先使用 x86 物理 Ubuntu host、稳定电源和短的高质量 USB-C 数据线，并确认设备进入 Recovery mode 后再重试。
* 注意事项
  * USB timeout 常见于刷机过程中设备重启并重新枚举 USB；VM/WSL 环境可能需要手动重新连接 USB，Seeed 强烈推荐专用物理 Ubuntu host。
  * initrd flash 的 NFS mount failure 可能与 host 的 `nfs-kernel-server`、防火墙、VPN、磁盘空间、NVMe 格式或不稳定虚拟化环境有关。
  * `Stat for blob_boot0.imgimg failed` / return value 19 在 Seeed 页面中与 host 工具链环境不兼容相关，建议改用 Ubuntu 20.04 或 22.04，不要用 Ubuntu 24.04。
  * `could not find tegrarcm_v2` 常见于使用非 x86 host，例如另一台 Jetson；应换 x86 Ubuntu host PC。
  * 首次启动卡在 OEM configuration 时，先关机，仅保留 HDMI 显示器和电源后重启，必要时多重启几次。
* 相关链接
  * [Seeed Common Flashing Errors and How to Fix Them](https://wiki.seeedstudio.com/usb_timeout_during_flash/)
  * [Seeed Flash BSP with Jetpack to Selected Jetson](https://wiki.seeedstudio.com/flash/jetpack_to_selected_product/)
