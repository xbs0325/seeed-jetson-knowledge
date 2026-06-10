---
product: reComputer Robotics J401 Carrier Board
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - faq
  - can
  - robotics
  - libgpiod
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
status: active
---

* 问题
  * reComputer Robotics J401 配好 CAN bitrate 后仍不能通信，需要做什么？
* 适用产品
  * Seeed reComputer Robotics J401 Carrier Board / reComputer Robotics 系列
* 适用平台类型：seeed_device
* 简洁答案
  * Robotics J401 的 CAN transceiver 有 idle mode。配置 `can0`/`can1` 后，还需要用 `gpioset --mode=wait` 拉低对应 STB GPIO 来唤醒 CAN transceiver。
* 注意事项
  * Seeed 文档示例：`sudo gpioset --mode=wait 2 3=0 &` 对应 CAN0，`sudo gpioset --mode=wait 2 4=0 &` 对应 CAN1。
  * `&` 让命令在后台保持 pin 状态；命令退出后 pin 状态可能复位。
  * CAN FD 还需设置 `dbitrate`、`fd on` 并确认 120 ohm 终端电阻开关。
* 相关链接
  * [reComputer Robotics J401 Interfaces Usage](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/)
