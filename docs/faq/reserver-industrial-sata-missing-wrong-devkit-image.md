---
product: reServer Industrial J4012/J4011/J3011/J3010
vendor: seeed
platform: seeed_device
jetpack: "7.2"
l4t: "39.2"
tags:
  - faq
  - reserver-industrial
  - sata
  - flashing
  - device-tree
  - developtool
date: 2026-08-14
source_links:
  - https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reserver_industrial_hardware_interface_usage/#sata-connectors
  - https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/
  - https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/RM/PackageManifest.html
status: active
---

* 问题
  * reServer Industrial 升级到 JetPack 7.2 后，`lsblk` 看不到 SATA 盘（只有 NVMe），`lspci` 也没有 SATA/AHCI 控制器，怎么办？
* 适用产品
  * Seeed reServer Industrial J4012 / J4011 / J3011 / J3010（载板带 2× 2.5" SATA bay）
* 适用平台类型：seeed_device
* 简洁答案
  * 先查 `cat /proc/device-tree/model`。若显示 **`NVIDIA Jetson Orin NX Engineering Reference Developer Kit Super`**（或同类 NVIDIA Orin Nano/NX DevKit Super / p3768 工程参考板字符串），说明当前刷入的是 **NVIDIA DevKit Super 板级配置**，不是 reServer Industrial 专用镜像；载板 PCIe-to-SATA 桥不会枚举，SATA 盘不会出现。应使用 Wiki / DevelopTool 中的 **reServer Industrial** 对应型号 JP7.2 包完整重刷。
* 诊断命令
  * `cat /proc/device-tree/model`
  * `cat /etc/nv_tegra_release`
  * `uname -a`
  * `lspci -nn | grep -iE 'sata|ahci|asmedia|jmicron|marvell|1b21|197b'`
  * `lsblk`
* 正确刷机包（J4012 / JP7.2 示例）
  * 包名：`mfi_reserver-industrial-orin-nx-16g-7.2.0-39.2.0-2026-06-24.tar.gz`（以 Wiki 表为准）
  * DevelopTool：产品选 **reServer Industrial J4012**（`j4012reserver`），L4T **39.2 / JetPack 7.2**
  * 勿选：`orin-nano-devkit-super`、reComputer Super、reComputer Industrial、或其他仅名称相近的板型
* 重刷后验收
  * `/proc/device-tree/model` **不再**是 NVIDIA Engineering Reference / DevKit Super 字符串
  * `lspci` 能看到 SATA/AHCI（或载板桥接控制器）
  * `lsblk` 出现 `sda` / `sdb`（在硬盘已正确安装并上电的前提下）
* 注意事项
  * reServer Industrial 的 SATA bay 走载板 PCIe-to-SATA，依赖 Seeed 设备树/BSP，不能套用 NVIDIA Orin Nano DevKit Super 镜像。
  * L4T 版本是 R39.2、内核是 6.8 **只说明 JetPack 大版本对了**，不能说明板级配置正确；必须以 device-tree model / 刷机包名核对。
  * DevelopTool 里同时存在 `orin-nano-devkit-super`（39.2）与 `j4012reserver`（39.2），选错产品会导致本症状。
  * 若重刷正确镜像后仍无 SATA 控制器，再查硬件连接、供电，并收集完整 `lspci -nn` / `dmesg | grep -iE 'pci|ahci|sata'` 升级排查（此时再考虑硬件）。
* 相关链接
  * [reServer Industrial Getting Started — Flash JetPack](https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/)
  * [Hardware Interface — SATA](https://wiki.seeedstudio.com/reserver_industrial_hardware_interface_usage/#sata-connectors)
  * [Flash and OTA to JetPack 7.2](https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/)
  * [Seeed 设备勿直接刷 NVIDIA 官方镜像](seeed-device-use-nvidia-official-image.md)
