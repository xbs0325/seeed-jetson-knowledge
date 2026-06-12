---
product: reComputer Super J4011/J4012
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - inbox
  - flashing
  - super
  - classic
date: 2026-06-12
collected_at: 2026-06-12
source_url: https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
  - https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
status: need_review
resolution: pending
---

* 问题
  * reComputer Super Orin NX 16GB 自编译刷机报错 `recomputer-orin-j401.conf: 没有那个文件` / `Invalid target board`？
* 适用产品
  * reComputer Super J4011/J4012（`lsusb` Orin NX 16GB 常为 `0955:7323`）
* 简洁答案（待复核）
  * **Super 不要用 Classic 板级名 `recomputer-orin-j401`。**
  * 预编译镜像：下载 Super 专用 mfi 包，在解压目录执行 `--flash-only --massflash 1 --network usb0 --showlogs`。
  * 自编译刷机：合并 Seeed `Linux_for_Tegra` 后，板级名用 **`recomputer-orin-super-j401`**，并确认根目录存在 `recomputer-orin-super-j401.conf`。
* 注意事项
  * Classic J401 刷机 Wiki 与 Super Getting Started **不是同一条路径**。
  * Seeed 不推荐在虚拟机中刷机。
  * 客户改 BSP 做 SPI-CAN 等二次开发导致的刷机失败，超出常规售后范围。
* 相关链接
  * [Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [Seeed BSP 编译](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/)
