---
product: reServer Industrial J3010/J3011/J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "5.1.1"
l4t: "35.3.1"
tags:
  - reserver-industrial
  - nvr
  - flashing
  - poe
  - storage
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/
status: active
---

# Seeed reServer Industrial：预装系统、刷机与硬件接口

## 适用范围

- Seeed reServer Industrial J4012/J4011/J3011/J3010。
- 适用平台类型：`seeed_device`。

## 产品定位

- Fanless compact edge AI/NVR server，基于 Jetson Orin Nano/Orin NX。
- AI 性能覆盖 20 TOPS 到 100 TOPS。
- 预装 JetPack 5.1.1，128GB SSD，并包含必要驱动、CUDA、cuDNN、TensorRT 等组件。

## 关键接口

- 5x RJ45 GbE，其中 4 个为 PoE PSE 口。
- 2 个 2.5 寸 SATA HDD/SSD drive bay，另有 M.2 2280 NVMe SSD。
- 1x DB9 COM，支持 RS232/RS422/RS485。
- 4x DI、4x DO、CAN、USB 3.1、USB Type-C device/debug、Mini PCIe、M.2 Key B、Nano SIM、RTC、TPM 2.0 连接器。
- 供电：DC 12V-36V terminal block，页面列出 24V/5A 电源适配器。

## 刷机注意事项

- Seeed Wiki 明确提示：如果无特殊需求，不需要重刷系统。
- 当前页面提供 JP5.1.1 指导；重刷到原 SSD 或新 SSD 时应使用 Seeed 提供的完整系统镜像，或按 Seeed 方法组合 NVIDIA L4T/rootfs 与 Seeed 外设驱动。
- 进入 Force Recovery Mode 时，需要用 Type-C 连接 DEVICE port，按住 REC 孔内 recovery button 后上电。
- `lsusb` 应显示与 Orin NX/Nano 模组匹配的 NVIDIA USB ID。

## 售后提示

reServer Industrial 不是 NVIDIA 官方开发套件。PoE、DI/DO、COM、CAN、SATA、mini PCIe/M.2 等接口依赖 Seeed 载板硬件与驱动；刷机或升级时必须确认 Seeed 对应型号的镜像/BSP。
