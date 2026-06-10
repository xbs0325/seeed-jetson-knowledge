---
product: reComputer J30/J40 with NVIDIA Jetson Orin
platform: Seeed Studio Wiki
tags:
  - recomputer
  - jetson
  - orin
  - specs
  - jetpack
  - nvme
  - troubleshooting
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/
---

# reComputer J30/J40 Jetson Orin 规格、JetPack 与刷机 FAQ

## 适用场景

适合电商客服快速回答 reComputer J3010/J3011/J4011/J4012 的型号差异、预装系统、接口扩展、供电和刷机问题。

## FAQ

### 问题：J3010、J3011、J4011、J4012 主要区别是什么？

简洁答案：J3010/J3011 使用 Jetson Orin Nano，AI 性能分别约 20 TOPS/40 TOPS；J4011/J4012 使用 Jetson Orin NX，AI 性能分别约 70 TOPS/100 TOPS。J4012 为 16GB Orin NX，性能和内存规格最高。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/

### 问题：收到后是否已经预装系统？

简洁答案：官方 Wiki 说明 reComputer J30/J40 随附 NVMe SSD 预装 JetPack 5.1.3，可开箱进行初始化和开发；如果买家自行更换 SSD 或需要重刷系统，可按 J401 carrier board 刷机教程操作。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/
- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/

### 问题：有哪些常用接口和扩展位？

简洁答案：J30/J40 使用 J401 carrier board，提供 1 个千兆网口、4 个 USB 3.2 Type-A、1 个 USB2.0 Type-C 设备口、HDMI 2.1、2 个 15-pin CSI、M.2 Key M 2280 NVMe、M.2 Key E Wi-Fi/BT、CAN、40-pin 扩展排针、RTC 和 4-pin PWM 风扇接口。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
### 问题：电源要求是什么？

简洁答案：J401 carrier board 支持 9-19V DC 输入。具体套装是否包含电源适配器以商品页/销售页面为准；客服应提醒买家使用稳定、功率足够的适配器，避免因电压跌落导致启动异常或负载下重启。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/

### 问题：重刷 JetPack 需要什么主机环境？

简洁答案：需要 Ubuntu 主机、USB Type-C 数据线和设备进入 Force Recovery Mode。官方建议使用实体 Ubuntu 主机，不推荐虚拟机或 ARM 架构 Ubuntu 主机。Jetson Orin NX 支持 JetPack 5.1 及以上；Orin Nano 支持 JetPack 5.1.1 及以上。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/

### 问题：进入 Force Recovery Mode 后如何确认识别成功？

简洁答案：按官方步骤短接 FC REC 与 GND、上电并用 Type-C 连接 Ubuntu 主机后执行 `lsusb`。不同模块会显示 NVIDIA USB ID，例如 Orin NX 16GB 常见为 `0955:7323 NVidia Corp`。确认后移除跳线再继续刷机。

相关链接：

- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/

