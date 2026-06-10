---
product: Jetson Orin GPIO
vendor: common
platform: common
jetpack: "6.x"
l4t: "36.x"
tags:
  - faq
  - gpio
  - libgpiod
  - sysfs
  - pinmux
date: 2026-06-10
source_url: https://github.com/NVIDIA/jetson-gpio/issues/114
status: active
---

* 问题
  * JetPack 6 上为什么找不到 `/sys/class/gpio`，或者 Jetson.GPIO 输出不生效？
* 适用产品
  * Jetson Orin 系列官方开发套件；Seeed Orin 设备仅在核对 Seeed BSP 后参考
* 适用平台类型：common
* 简洁答案
  * JetPack 6 使用 upstream GPIO driver，旧 sysfs GPIO 方式已废弃，推荐使用 libgpiod 工具。某些引脚若未在 pinmux/BCT 中配置为 GPIO，用户态无法直接作为输出使用。
* 注意事项
  * NVIDIA 官方说明中，必要时需修改 pinmux spreadsheet 生成 `pinmux.dtsi`/`gpio.dtsi` 并重新刷入。
  * Seeed 载板不要直接套 NVIDIA 官方开发套件 pinmux；应找 Seeed 对应型号 BSP 或提交人工复核。
  * 若只是安装新版 Jetson.GPIO，通常不能替代 pinmux/BCT 配置。
* 相关链接
  * [NVIDIA Jetson.GPIO issue #114](https://github.com/NVIDIA/jetson-gpio/issues/114)
  * [NVIDIA pinmux changes](https://docs.nvidia.com/jetson/archives/r36.3/DeveloperGuide/HR/JetsonModuleAdaptationAndBringUp/JetsonAgxOrinSeries.html?highlight=pin%20direction#pinmux-changes)
