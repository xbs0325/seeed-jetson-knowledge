---
product: reServer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "6.x"
l4t: "36.x"
tags:
  - faq
  - reserver-industrial
  - poe
  - gpio
  - libgpiod
date: 2026-06-10
source_url: https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727
status: need_review
---

* 问题
  * reServer Industrial J4012 升级 JetPack 6 后 PoE 网口不供电怎么办？
* 适用产品
  * Seeed reServer Industrial J4012
* 适用平台类型：seeed_device
* 简洁答案
  * Seeed 论坛给出的 JetPack 6 示例是安装 gpiod 后执行 `gpioset gpiochip2 15=1` 启用 PoE。该条目需结合最新 Seeed Wiki/BSP 人工复核。
* 注意事项
  * 此命令只针对论坛上下文中的 reServer Industrial J4012，不适用于其他型号。
  * 如果客户使用非 Seeed 官方 JetPack 6 镜像，PoE 相关 device tree/GPIO 可能不完整。
  * JetPack 6 不应继续默认使用 `/sys/class/gpio` 旧方法。
* 相关链接
  * [Seeed Forum: reServer Industrial J4012 JetPack 6 Missing GPIO](https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727)
  * [reServer Industrial Getting Started](https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/)
