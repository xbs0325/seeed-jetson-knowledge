---
product: reComputer Robotics J401
vendor: seeed
platform: seeed_device
jetpack: "6.2 / 7.2"
l4t: "36.4.x / 39.2"
tags:
  - faq
  - boot
  - serial
  - recovery
  - robotics
date: 2026-08-11
source_url: https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/jetson_debug_guide/
  - https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
status: active
---

* 问题
  * reComputer Robotics J401 上电后 PWR 灯亮，Debug 口能认出 CP210x，但串口无输出、无显示、也无法进 Recovery？
* 适用产品
  * Seeed reComputer **Robotics** J401 + Jetson Orin Nano / Orin NX 模组
  * 预装或重刷 JetPack 6.x / 7.2 场景
* 简洁答案
  * **先分清两个 Type-C**：USB 2.0 Device/Debug（CP210x 串口 + Recovery）≠ USB 3.0 Host/DP（显示）。显示请走 Host/DP，见 [display FAQ](recomputer-robotics-j401-display-dp-not-hdmi.md)。
  * **串口**：REC 拨码拨到 **debug** 模式；Host 用 picocom/minicom，`115200 8N1`、无流控；Linux 上可先 `sudo systemctl stop ModemManager`，避免占用 `/dev/ttyUSB0`。上电/复位后应能看到 bootloader/kernel 日志；仅黑屏闪标、无任何字符 = 启动日志未出来。
  * **Force Recovery**：REC 拨码拨到 Wiki 所述 **RESET/REC** 位置 → 上电 → Type-C 数据线接 **Device/Debug** 口 → `lsusb` 应按模组出现 NVIDIA ID（如 Orin NX 16GB：`0955:7323`）。能进 Recovery 则可按 Wiki 用对应 Robotics mfi 包 `--flash-only` 重刷 NVMe。
  * **仍无 NVIDIA 设备、且串口始终无 bootloader 输出**：在确认数据线、拨码、电源（建议官网推荐 19V/4.74A 5525）、模组与散热座安装后，再走硬件/售后路径；**未完成 Recovery 实测前不断言板子损坏**。
* 客服可复制简答（中文）
  * Robotics J401 没有 HDMI，显示请接 **Type-C Host（DP）** + DP/HDMI 转接。串口请用 **Device/Debug** 口，拨码到 debug，115200，可先停 ModemManager。请再试：拨码进 Recovery → 上电 → 同一 Debug 口接电脑 → 把完整 `lsusb` 发我们。能看到 `0955:7xxx` 即可按 Wiki 重刷：https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
* 注意事项
  * minicom「打不出字」在无人登录/无 bootloader 时常见，不单独等于串口坏。
  * 刷机必须用 **Robotics J401** 对应模组镜像，勿用 Classic / Super 包。
  * Wiki 刷机步骤写 “switch to RESET mode”；板上为 **REC DIP**，按丝印与 Wiki 图示操作。
* 相关链接
  * [Getting Started / Flash](https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/)
  * [Interfaces / Debug UART](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/)
  * [Jetson Serial Debugging Guide](https://wiki.seeedstudio.com/jetson_debug_guide/)
