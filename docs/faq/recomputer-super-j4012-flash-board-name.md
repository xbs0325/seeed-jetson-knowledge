---
product: reComputer Super J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - faq
  - flashing
  - super
date: 2026-06-12
source_url: https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
status: active
---

* 问题
  * Super 刷机报错 `recomputer-orin-j401.conf` 不存在 / `Invalid target board`？
* 适用产品
  * reComputer Super J4011/J4012（Orin NX 16GB Recovery 常为 `0955:7323`）
* 简洁答案
  * Super **不要用** Classic 板级名 `recomputer-orin-j401`。
  * **推荐**：下载 Super 专用 mfi 包，解压后执行 `sudo ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs`。
  * **自编译**：板级名 **`recomputer-orin-super-j401`**，须存在 `recomputer-orin-super-j401.conf`。
* 客服可复制简答
  * 您好，Super 套件请用 Super 专用镜像文档：https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/ 。自编译时板级名是 `recomputer-orin-super-j401`，不是 `recomputer-orin-j401`。
* 相关链接
  * [Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [BSP 编译 Wiki](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/)
