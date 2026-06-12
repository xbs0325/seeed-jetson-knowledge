---
product: reComputer J3010/J3011/J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "5.1.1 / 5.1.2 / 5.1.3 / 6.0 / 6.1 / 6.2"
l4t: "35.x / 36.x"
tags:
  - flashing
  - bsp
  - nvme
  - j401
  - force-recovery
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
status: active
---

# Seeed reComputer Classic J401/J301 系列刷 JetPack

## 适用范围

- Seeed reComputer **Classic** J3010、J3011、J4011、J4012（**非 Super 系列**）。
- 这些设备内部使用 Classic J401 carrier board，刷机步骤相同。
- **reComputer Super**（J301x/J401x Super）请用 [`recomputer-super-jetpack-6-2.md`](recomputer-super-jetpack-6-2.md)。
- 适用平台类型：`seeed_device`。

## 关键硬件与系统信息

- 模组覆盖 Jetson Orin Nano 4GB/8GB 与 Jetson Orin NX 8GB/16GB。
- J401 载板提供 1x GbE、4x USB 3.2 Type-A、1x USB 2.0 Type-C device mode、M.2 Key M、M.2 Key E、2x CSI、HDMI 2.1、CAN、40-pin header、12-pin control/UART header、RTC 与风扇接口。
- 供电范围为 9-19V，原页面提示电源适配器不随部分载板包含。
- reComputer J40/J30 系列预装 JetPack 5.1.3 于 NVMe SSD。

## 刷机前提

- 使用 Ubuntu Host Computer 与 USB Type-C 数据线。
- Seeed 不推荐使用虚拟机或 ARM 架构 Ubuntu 做刷机 host。
- 进入 Force Recovery Mode：用跳线连接 FC REC 与 GND，给设备上电，并通过 Type-C 连接 host；`lsusb` 应显示对应 NVIDIA USB ID。
- Orin NX 模组支持 JetPack 5.1 及以上；Orin Nano 模组支持 JetPack 5.1.1 及以上。

## 版本注意事项

- Seeed Wiki 列出 JP5.1.1、JP5.1.2、JP5.1.3、JP6.0、JP6.1、JP6.2。
- 页面提示 NVIDIA 更新过模组 DRAM；若模组 DRAM 来自 Hynix，Seeed 推荐刷 JetPack 5.1.3。
- 对 J401/J301 设备，应使用 Seeed 对应包、配置和板级支持，不要直接套用 NVIDIA 官方开发套件镜像。

## 常见刷机命令片段

Seeed 页面示例会在 host 上安装依赖，准备 NVIDIA L4T/rootfs 与 Seeed 驱动后，用 initrd flash 刷 NVMe：

```bash
sudo apt install qemu-user-static sshpass abootimg nfs-kernel-server libxml2-utils binutils -y
sudo ./tools/kernel_flash/l4t_initrd_flash.sh --external-device nvme0n1p1 \
  -c tools/kernel_flash/flash_l4t_external.xml \
  -p "-c bootloader/t186ref/cfg/flash_t234_qspi.xml" \
  --showlogs --network usb0 p3509-a02+p3767-0000 internal
```

具体命令需以 Seeed Wiki 对应 JetPack 版本和设备包为准。

## 售后提示

客户问“能否用 NVIDIA SDK Manager 直接刷 reComputer J401/J301”时，应说明该设备为 Seeed 自定义载板/整机，需要 Seeed 的 BSP、设备树和刷机包；NVIDIA 官方套件流程不能默认适用。
