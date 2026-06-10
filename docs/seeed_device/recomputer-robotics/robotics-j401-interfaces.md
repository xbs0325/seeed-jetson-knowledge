---
product: reComputer Robotics J401 Carrier Board
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - recomputer-robotics
  - can
  - uart
  - i2c
  - gmsl
  - interfaces
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
status: active
---

# reComputer Robotics J401：JetPack 6.2 与接口使用要点

## 适用范围

- Seeed reComputer Robotics J401 Carrier Board / reComputer Robotics 系列。
- 适用平台类型：`seeed_device`。

## 关键硬件信息

- 支持 Jetson Orin Nano/Orin NX 模组，Super/MAXN 模式最高 157 TOPS。
- 预装 JetPack 6 与 Linux BSP；Seeed 页面提供 JetPack 6.2 镜像和 SHA256。
- 主要接口：
  - 2x RJ45 Gigabit Ethernet
  - 6x USB 3.2 Type-A
  - 1x USB 3.0 Type-C Host/DP 1.4
  - 1x USB 2.0 Type-C Device/Debug
  - M.2 Key M、M.2 Key E、M.2 Key B
  - CAN0/CAN1、UART、2x I2C、GMSL2 camera expansion header
  - 5V PWM fan 与 12V PWM fan
  - 19-54V XT30(2+2) 供电

## 刷机要点

- 使用 Ubuntu host PC、Robotics J401、Jetson Orin Nano/NX 模组、主动散热、NVMe SSD、USB Type-C 数据线。
- Seeed 提供按模组区分、带 GMSL 驱动的 JetPack 6.2 镜像。
- 下载镜像后用 `sha256sum` 校验。
- 进入 Force Recovery Mode 后使用 Seeed 镜像包内 initrd flash 命令刷 NVMe。

## CAN 使用要点

- CAN1 示例需要先配置 bitrate 并启用接口：

```bash
sudo ip link set can1 type can bitrate 500000
sudo ip link set can1 up
```

- Robotics J401 的 CAN transceiver 有 idle mode，需要用 GPIO 唤醒：

```bash
sudo apt-get update && sudo apt-get install -y libgpiod-utils
sudo gpioset --mode=wait 2 3=0 &
sudo gpioset --mode=wait 2 4=0 &
```

- Seeed 文档说明 `2 3=0` 对应 CAN0，`2 4=0` 对应 CAN1。
- CAN FD 需关闭接口后设置 `dbitrate` 与 `fd on`，并确认 120 ohm 终端电阻开关。

## UART/I2C/GMSL 注意事项

- UART 示例使用 4-pin GH header，示例串口为 `/dev/ttyTHS1`，波特率 115200。
- I2C 使用 `i2c-tools` 与 `i2cdetect` 扫描设备地址，接线需确认 SDA/SCL/GND/Power。
- GMSL 功能需要安装带 GMSL expansion board driver 的 JetPack 版本，并通过 Jetson-IO 选择 Seeed 对应 overlay。

## 售后提示

Robotics J401 的 CAN、GMSL、UART、I2C 依赖 Seeed Robotics J401 载板设计和对应 BSP。客户若使用 NVIDIA 官方开发套件教程或其他 Seeed J401 Classic 教程，应先核对是否为同一载板。
