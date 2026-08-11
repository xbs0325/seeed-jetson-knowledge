---
product: reComputer Robotics J401
vendor: seeed
platform: seeed_device
jetpack: "6.2 / 7.2"
l4t: "36.4.x / 39.2"
tags:
  - faq
  - display
  - dp
  - hdmi
  - robotics
date: 2026-08-11
source_url: https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
status: active
---

* 问题
  * reComputer Robotics J401 接 HDMI 无画面 / 找不到 HDMI 口，怎么办？
* 适用产品
  * Seeed reComputer **Robotics** J401（载板 / 整机）
  * **不适用** Classic J401（原生 HDMI 2.1）、Super、Industrial 等其他产品线
* 简洁答案
  * Robotics J401 **没有原生 HDMI 口**。视频输出是 **USB 3.0 Type-C Host 上的 DP 1.4**。
  * 接显示器时：用 **Type-C Host（带 DP）** 口 + **DP/PD→HDMI 转接器** 接 HDMI 显示器，或用支持 DP/PD 输入的线直连显示器。
  * **不要**把显示线接到 **USB 2.0 Type-C Device Mode/Debug** 口（该口是刷机/串口调试，出 CP210x，不是视频口）。
* 注意事项
  * 客户说「HDMI 无信号」时，先核对是否误当 Classic J401（有 HDMI），以及是否接错 Type-C 口。
  * 无画面且串口也无启动日志时，按无启动排查（REC 拨码、Force Recovery、`lsusb`），不要只换 HDMI 线。
* 相关链接
  * [Getting Started with reComputer Robotics](https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/)
  * [Robotics J401 Interfaces Usage](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/)
  * [Classic J401 HDMI FAQ](recomputer-j401-hdmi-no-signal.md)（仅 Classic，勿混用）
