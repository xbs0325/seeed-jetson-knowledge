---
product: Seeed Jetson devices
vendor: seeed
platform: seeed_device
jetpack: "5.x / 6.x / 7.x"
l4t: "35.x / 36.x / 39.x"
tags:
  - faq
  - flashing
  - bsp
  - sdk-manager
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
status: active
---

* 问题
  * Seeed reComputer/reServer/Robotics 能不能直接刷 NVIDIA 官方开发套件镜像或 SDK Manager 流程？
* 适用产品
  * Seeed reComputer J301/J401、reComputer Super、reComputer Industrial、reServer Industrial、reComputer Robotics J401 等 Seeed Jetson 盒子/载板/整机
* 适用平台类型：seeed_device
* 简洁答案
  * 默认不能直接套用。Seeed 设备使用自定义载板、接口、电源、设备树和 BSP，应优先使用 Seeed 对应型号 Wiki、镜像、BSP 和 flash config。
* 注意事项
  * NVIDIA 官方开发套件流程只对官方开发套件成立，不能默认覆盖 Seeed 载板。
  * 如果客户已经刷入 NVIDIA 官方镜像后出现 CAN、GPIO、PoE、CSI、风扇、网口或 M.2 异常，应先核对 Seeed BSP/设备树是否缺失。
  * 只有 Seeed 文档明确说明某个 NVIDIA 流程可用于该型号时，才能按通用流程处理。
* 相关链接
  * [Seeed reComputer J401/J301 Flash JetPack](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
  * [Seeed reComputer Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [Seeed reServer Industrial Getting Started](https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/)
