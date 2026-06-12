---
product: Seeed reComputer / reComputer Super
vendor: seeed
platform: seeed_device
jetpack: "6.x"
tags:
  - faq
  - taobao
  - ecommerce
  - naming
  - flashing
date: 2026-06-12
source_url: https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
status: active
---

* 问题
  * 淘宝标题写「Jetson Orin NX 16G Super 官方核心模组 开发套件」是 NVIDIA 官方套件还是 Seeed 产品？该用哪套刷机文档？
* 适用产品
  * Seeed reComputer / reComputer Super（如 Super J4012，Orin NX 16GB）
* 适用平台类型：seeed_device
* 简洁答案
  * 此类标题通常指 **NVIDIA 正品核心模组 + Seeed 载板开发套件**，属于 **Seeed 产品**，不是 NVIDIA 整机官方 Developer Kit。刷机应走 **Seeed Wiki / Seeed mfi 或 Linux_for_Tegra**，不要默认给 NVIDIA 官方 DevKit 刷机链接。
* 注意事项
  * 淘宝标题常为搜索优化，「官方」多修饰 **核心模组**，不是整机官方套件。
  * **NVIDIA 官方 Developer Kit** 指 NVIDIA 销售的整机参考套件（如 Orin Nano Super DevKit、AGX Orin DevKit）；与 Seeed reComputer 不同。
  * 「Super」在 Seeed 场景常对应 **reComputer Super** + JetPack 6.2 Super/MAXN 模式。
  * 若载板为微雪、亚邦等第三方，则走载板商文档 + NVIDIA L4T，不是 Seeed `recomputer-orin-j401`。
  * 仍不确定时索要：店铺商品链接、SKU、外壳型号、Recovery 时 `lsusb`（Orin NX 16GB 常为 `0955:7323`）。
* 客服可复制简答
  * 您好，标题里「官方核心模组」一般指 NVIDIA 正品模组，「开发套件/主板」指我们 Seeed 载板套件，不是 NVIDIA 原厂整机开发套件。刷机请按 Seeed reComputer 文档操作。Classic J401：https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/ ；Super 系列：https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
* 相关链接
  * [reComputer J401 刷机 Wiki](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
  * [reComputer Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [按产品选镜像](https://wiki.seeedstudio.com/flash/jetpack_to_selected_product/)
  * [Seeed 设备能否用 NVIDIA 官方镜像（本仓库）](seeed-device-use-nvidia-official-image.md)
  * [AGX Orin 官方 DevKit 规格书（对比用）](agx-orin-64gb-developer-kit-datasheet.md)
