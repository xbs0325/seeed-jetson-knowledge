---
product: reComputer Super J3010/J3011/J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - recomputer-super
  - flashing
  - bsp
  - power
  - can
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
status: active
---

# Seeed reComputer Super：JetPack 6.2 与硬件要点

## 适用范围

- Seeed reComputer Super J3010、J3011、J4011、J4012。
- 适用平台类型：`seeed_device`。

## 关键规格

- 模组：Jetson Orin Nano 4GB/8GB、Jetson Orin NX 8GB/16GB。
- AI 性能：Orin Nano Super 最高 34/67 TOPS，Orin NX Super/MAXN 最高 117/157 TOPS。
- 预装 JetPack 6.2 与 Linux OS BSP。
- 载板接口包含 M.2 Key M、M.2 Key E、mini-PCIe、双 RJ45 千兆网口、4x USB 3.2、HDMI 2.1、4x CSI、CAN、40-pin 扩展、12-pin control/UART、RTC 和双风扇接口。

## 供电与配件

- Jetson Orin Nano 版本：推荐 12V 5A 5525 圆口电源。
- Jetson Orin NX 版本：推荐 19V 4.74A 5525 圆口电源。
- Seeed 页面建议使用官方电源适配器与推荐配件，摄像头/无线模块等外设需核对兼容性。

## 刷机方式摘要

- 使用 Ubuntu host PC、reComputer Super 与 USB Type-C 数据线。
- Seeed 提供按模组区分的 JetPack 6.2 镜像包和 SHA256。
- 下载约 14.1GB 镜像后，应先用 `sha256sum` 校验完整性。
- 通过板上 RESET/REC 方式进入 Force Recovery Mode，`lsusb` 应显示对应 Orin NX/Nano USB ID。
- 解压 `mfi_xxxx.tar.gz` 后运行 Seeed 包内的 initrd flash 命令：

```bash
sudo ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs
```

自编译 BSP 后刷机时，板级名用 **`recomputer-orin-super-j401`**（不是 Classic 的 `recomputer-orin-j401`）。见 [Seeed BSP 编译 Wiki](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/)。

## 售后提示

客户询问 reComputer Super 能否直接刷 NVIDIA JetPack 7.2 ISO 时，应标记为需核对 Seeed 是否发布对应镜像/BSP。当前 Seeed Wiki 明确提供的是 JetPack 6.2 的设备镜像与流程。
