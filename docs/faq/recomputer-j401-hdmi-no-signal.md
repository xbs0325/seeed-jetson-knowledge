---
product: reComputer J3010/J3011/J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "5.1.x / 6.0 / 6.1 / 6.2"
l4t: "35.x / 36.x"
tags:
  - faq
  - hdmi
  - display
  - j401
date: 2026-06-22
source_url: https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
source_links:
  - https://wiki.seeedstudio.com/jetson_debug_guide/
  - https://github.com/Seeed-Studio/wiki-documents/discussions/1233
status: active
---

* 问题
  * reComputer Classic J401 载板（J301/J401 系列）刷机后显示器报 **No HDMI signal** / 黑屏，是否正常？是否与 HDMI 转接线有关？
* 适用产品
  * Seeed reComputer **Classic** J3010/J3011/J4011/J4012（J401 carrier board，**不含 Super / Robotics / Industrial**）
  * Jetson Orin Nano / Orin NX 模组
* 简洁答案
  * **Classic J401 载板是原生 HDMI 2.1 口**，不是 DisplayPort。客户若使用 **标准 HDMI 公对公线** 直连显示器，问题通常 **不是** NVIDIA 开发套件上常见的 **DP→HDMI 转接头/被动转接线** 兼容性（该问题多见于 DevKit 的 DP 口）。
  * 刷机成功、主机仍能看到 `L4T_README` 分区，多半表示 **USB Type-C 仍连着刷机 host** 或设备仍在 recovery/USB 相关状态；正常使用时请 **拔掉刷机用 USB-C**，确认 **FC REC 跳线已取下**，再单独上电启动。
  * 首次进桌面可能较慢；Seeed Wiki 提示若长时间无桌面可 **重新插拔电源**。
  * 常见排查顺序：换显示器/换一根 **认证 HDMI 线** → 确认 **9–19V 电源** 与刷机板级名（Classic 用 `recomputer-orin-j401`，**不是** Super 的 `recomputer-orin-super-j401`）→ 用 **12-pin UART** 串口看是否已进系统 → 仍无解联系 techsupport@seeed.io 并附串口日志。
  * Seeed 官方对类似无显示问题曾建议：**换一台显示器**、必要时 **按 Wiki 重刷 Seeed 镜像**。
* 客服可复制简答（中文）
  * 您好，J401 载板是 **HDMI 2.1 原生口**，若您用的是 **HDMI 直连线**（不是 DP 转 HDMI），一般不是转接头兼容问题。请先：1）拔掉连电脑的 USB-C 刷机线；2）确认刷机跳线已取下；3）只接电源+HDMI 重新上电，首次启动多等几分钟或重插电源；4）换显示器或换一根 HDMI 线试。若风扇转但一直无信号，请按 Wiki 用 12-pin 串口抓启动日志发我们：https://wiki.seeedstudio.com/jetson_debug_guide/ 。刷机文档：https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
* 客服可复制简答（英文）
  * Hi — the Classic J401 carrier board has a **native HDMI 2.1 port** (not DisplayPort). If you are using a **straight HDMI-to-HDMI cable**, this is usually **not** the DP-to-HDMI adapter issue seen on NVIDIA dev kits. Please: (1) disconnect the USB-C cable to your Ubuntu host; (2) remove the FC REC jumper if still installed; (3) power on with only power + HDMI — first boot can take several minutes, or try reconnecting power; (4) try another monitor and a known-good HDMI cable. If the fan spins but there is still no signal, capture boot logs over the **12-pin UART** (see https://wiki.seeedstudio.com/jetson_debug_guide/ ) and contact techsupport@seeed.io with your flash method and logs.
* 相关链接
  * [Classic J401 Flash JetPack](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
  * [Seeed Jetson Debug Guide](https://wiki.seeedstudio.com/jetson_debug_guide/)
  * [Wiki Q&A：J401 无显示官方建议换显示器/重刷](https://github.com/Seeed-Studio/wiki-documents/discussions/1233)
