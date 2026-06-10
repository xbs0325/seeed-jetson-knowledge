---
product: "reComputer Super J3010/J3011/J4011/J4012"
platform: "Seeed Studio Wiki"
tags:
  - Jetson
  - reComputer Super
  - specifications
  - JetPack
  - flashing
  - ecommerce-support
date: 2026-06-10
source_url: "https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/"
---

# reComputer Super 规格、供电与 JetPack 刷机 FAQ

## 适用范围

适用于咨询 reComputer Super J3010、J3011、J4011、J4012 的买家，重点覆盖下单前规格确认、供电/配件选择、JetPack 系统刷机和首次启动。

## FAQ

### 问题：reComputer Super 各型号对应哪些 Jetson 模组和 AI 性能？

**简洁答案：** reComputer Super 覆盖 Jetson Orin Nano 4GB/8GB 与 Jetson Orin NX 8GB/16GB。官方规格中 J3010/J3011/J4011/J4012 分别覆盖约 34 TOPS、67 TOPS、117 TOPS、157 TOPS 的 AI 性能档位，适合从入门边缘 AI 到更高性能机器人/视觉推理场景。

**相关链接：**
- [Getting Started with reComputer Super - Specifications](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

### 问题：买家应该配多大功率的电源？

**简洁答案：** Orin Nano 版本建议使用 12V 5A、5525 圆口电源；Orin NX 版本建议使用 19V 4.74A、5525 圆口电源。优先建议使用官方适配器，并按地区选择对应梅花尾电源线。

**相关链接：**
- [Getting Started with reComputer Super - Power & Accessory Guidelines](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

### 问题：设备出厂系统是什么版本？

**简洁答案：** reComputer Super 官方资料标注预装 JetPack 6.2 与 Linux OS BSP，产品面向开发和量产场景，可直接进入系统初始化流程。

**相关链接：**
- [Getting Started with reComputer Super - Introduction](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

### 问题：刷机需要准备什么主机环境？

**简洁答案：** 准备 Ubuntu 主机、reComputer Super、USB Type-C 数据线。JetPack 6.x 建议使用物理 Ubuntu 20.04 或 22.04 主机；不要优先推荐虚拟机环境，因为恢复模式 USB 重连容易不稳定。

**相关链接：**
- [Getting Started with reComputer Super - Prerequisites](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

### 问题：如何判断已进入 Force Recovery Mode？

**简洁答案：** 将开关拨到 RESET 模式，接通电源，用 USB-C 数据线连接 Ubuntu 主机后执行 `lsusb`。根据模组不同，应能看到 NVIDIA 设备 ID，例如 Orin NX 16GB 为 `0955:7323`，Orin NX 8GB 为 `0955:7423`，Orin Nano 8GB 为 `0955:7523`，Orin Nano 4GB 为 `0955:7623`。

**相关链接：**
- [Getting Started with reComputer Super - Enter Force Recovery Mode](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

### 问题：刷机会清空数据吗？

**简洁答案：** 官方流程会将 JetPack 系统刷写到 NVMe SSD。售前/售后沟通时应提醒买家提前备份重要数据，并确保下载的镜像 SHA256 与官方页面一致。

**相关链接：**
- [Getting Started with reComputer Super - Prepare the Jetpack Image](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)

## 电商客服提示

- 规格咨询优先确认买家选择的是 Orin Nano 还是 Orin NX 版本。
- 电源、摄像头、无线模组等配件优先推荐官方或官方验证清单，减少兼容性售后。
- 刷机问题先确认主机系统版本、是否物理 Ubuntu、USB-C 线是否支持数据传输、是否进入恢复模式。
