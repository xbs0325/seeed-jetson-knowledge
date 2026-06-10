---
product: reComputer Industrial J201/J301/J401 series
vendor: seeed
platform: seeed_device
jetpack: "5.1.3 / 6.x"
l4t: "35.x / 36.x"
tags:
  - recomputer-industrial
  - flashing
  - poe
  - dido
  - can
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
status: active
---

# Seeed reComputer Industrial：预装系统、刷机与工业接口

## 适用范围

- Seeed reComputer Industrial J4012/J4011/J3011/J3010/J2012/J2011。
- 适用平台类型：`seeed_device`。

## 产品要点

- 基于 Jetson Xavier NX、Orin Nano、Orin NX，AI 性能覆盖 20 TOPS 到 100 TOPS。
- 预装 JetPack 5.1.3 和 Seeed Linux OS BSP。
- Fanless 被动散热设计，页面标注 -20 至 60 摄氏度工作温度条件为 0.7m/s airflow。
- 支持桌面、DIN rail、壁挂、VESA 等安装方式。

## 工业接口

- 2x RJ45 GbE，其中 1 个为 PoE PSE 802.3af。
- 1x RS-232/RS-422/RS-485。
- 4x DI、4x DO、CAN。
- 3x USB 3.2、USB 2.0 Type-C device、USB 2.0 Type-C debug UART/RP2040。
- Mini PCIe、M.2 Key B、Nano SIM、TPM 2.0 connector、RTC、2-lane CSI。

## 刷机要点

- 如果无特殊需求，客户可使用预装系统，无需重刷。
- 重刷时应使用 Seeed 对应型号完整系统镜像，或按 Seeed 方法将 NVIDIA L4T/rootfs 与 Seeed 外设驱动组合。
- Seeed Wiki 列出 JetPack 5.1.1、5.1.3、6.0、6.1、6.2 相关刷机入口；使用前需按具体型号下载。
- 推荐物理 Ubuntu host；页面列出 Ubuntu 20.04 host，并说明 JetPack 5.x/6.x host 兼容表。
- 进入 Force Recovery Mode：Type-C 连接 USB2.0 DEVICE port，按住 RECOVERY 孔内按钮后上电，`lsusb` 应显示对应 Orin NX/Nano USB ID。

## 售后提示

工业接口（PoE、DI/DO、RS485、CAN、TPM、蜂窝模块）依赖 Seeed 载板 BSP 和设备树。若客户自行替换为 NVIDIA 官方开发套件 BSP，可能出现接口缺失或 GPIO 映射变化，应建议回到 Seeed 官方镜像或提交人工复核。
