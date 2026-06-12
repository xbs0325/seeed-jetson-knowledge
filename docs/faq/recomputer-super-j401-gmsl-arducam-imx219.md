---
product: reComputer Super J401 Carrier Board
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - faq
  - gmsl
  - camera
  - imx219
  - arducam
  - csi
sku: "100090211"
date: 2026-06-11
source_url: https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
status: active
---

* 问题
  * reComputer Super J401 默认镜像是否带 GMSL 驱动？能否用 Arducam GMSL IMX219，四路 GMSL 同时接四个 MIPI 口（不用 virtual channel）是否可行？驱动是否好装？
* 适用产品
  * reComputer Super J401 Carrier Board（SKU 100090211，J3010/J3011/J4011/J4012 系列载板）
* 适用平台类型：seeed_device
* 简洁答案
  * Super J401 的 Seeed JetPack 6.2 镜像是标准 **4× MIPI CSI** 方案，**默认不带 Seeed 官方 GMSL 驱动/BSP**。若使用 Arducam GMSL2 IMX219，需按 Arducam 文档第三方安装并自行联调；该组合**非 Seeed 官方验证方案**，不能承诺四路 GMSL 同时无 VC 一定可用，也不能说驱动很好装。
* 注意事项
  * Super J401 Wiki 仅描述 **4× 标准 MIPI CSI 摄像头**，未列出 GMSL 扩展或 GMSL 驱动包。
  * Seeed 文档化的 GMSL 路径在 **reComputer Robotics J401**（专用 GMSL 扩展板 + 带 GMSL 驱动的 JetPack 6.2 镜像 + Jetson-IO overlay），与 Super J401 **不是同一载板**，不能混用教程。
  * Arducam Jetson GMSL IMX219（如 B0570）为 **beta**；单块 GMSL2 RX 解串板通常 **最多 2 路通道**；四路需自行规划多块解串板、camera/device tree 配置。
  * 若不需要 GMSL 长线，**直连 MIPI CSI IMX219** 是 Super J401 官方文档路径，无需 GMSL 驱动。
  * 对客户外发回复宜简短；不能承诺「完全可以 work」或「驱动很容易装」。
* 客服可复制英文简答（示例）
  * The reComputer Super J401 JetPack 6.2 image does not include a Seeed-validated GMSL driver. For Arducam GMSL2 IMX219, follow Arducam's Jetson GMSL docs for third-party install and bring-up; this is not officially validated on Super J401. We cannot confirm four simultaneous GMSL cameras without virtual channels. Seeed's documented GMSL support is on the reComputer Robotics J401 platform.
* 相关链接
  * [reComputer Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
  * [reComputer Super Hardware - CSI](https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/)
  * [reComputer Super J401 商详 SKU 100090211](https://www.seeedstudio.com/reComputer-Super-J401-Carrier-Board-p-6642.html)
  * [reComputer Robotics J401 GMSL 要点（本仓库）](../seeed_device/recomputer-robotics/robotics-j401-interfaces.md)
  * [Arducam GMSL for NVIDIA](https://docs.arducam.com/GMSL-Camera-Solution/GMSL-Camera-for-NVIDIA/Introduction/)
