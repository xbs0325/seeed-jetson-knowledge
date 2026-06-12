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
  - classic
date: 2026-06-12
source_url: https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
  - https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
status: active
---

* 问题
  * reComputer Super Orin NX 16GB 刷机报错 `recomputer-orin-j401.conf: 没有那个文件` / `Invalid target board - recomputer-orin-j401`？
* 适用产品
  * reComputer Super J4011/J4012（Recovery 时 Orin NX 16GB 常为 `lsusb` `0955:7323`）
* 适用平台类型：seeed_device
* 简洁答案
  * **Super 不要用 Classic 板级名 `recomputer-orin-j401`。**
  * **预编译镜像（推荐）**：下载 Super 专用 mfi 包，在解压目录执行：
    ```bash
    sudo ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs
    ```
  * **自编译 BSP**：合并 Seeed `Linux_for_Tegra` 后，板级名用 **`recomputer-orin-super-j401`**，并确认根目录存在 `recomputer-orin-super-j401.conf`。
* 注意事项
  * Classic J401 刷机 Wiki 与 Super Getting Started **不是同一条路径**。
  * Seeed 不推荐在虚拟机中刷机。
  * 客户自改 BSP（如 SPI 转 CAN）后刷机失败，属于二次开发，超出常规售后范围。
* 客服可复制简答
  * 您好，Super 套件请用 Super 专用镜像和文档，板级名是 `recomputer-orin-super-j401`，不是 Classic 的 `recomputer-orin-j401`。预编译包刷机：https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
* 相关链接
  * [reComputer Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [Seeed BSP 编译与板级名列表](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/)
  * [Classic J401 刷机（不含 Super）](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
  * [本仓库 Super 刷机要点](../seeed_device/recomputer/recomputer-super-jetpack-6-2.md)
