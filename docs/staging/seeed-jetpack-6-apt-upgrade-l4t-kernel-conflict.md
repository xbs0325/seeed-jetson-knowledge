---
product: Seeed Jetson devices with custom BSP
vendor: seeed
platform: seeed_device
jetpack: "6.2 / 6.2.1"
l4t: "36.4.x"
tags:
  - faq
  - apt
  - bsp
  - kernel
  - bootloader
date: 2026-06-12
source_url: https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
status: need_review
review_target: docs/faq
review_reason: "Background on bare apt upgrade risk; active upgrade SOP now in j401-safe-upgrade-jetpack-6-2-2-r365.md."
next_action: "Keep as conflict background; point customers to active FAQ + DevelopTool OTA for JP6.2→6.2.2."
---

* 问题
  * Seeed Jetson 设备刷 JetPack 6.2 后，执行 `sudo apt upgrade` 导致 `nvidia-l4t-kernel`、`nvidia-l4t-bootloader`、`nvidia-l4t-kernel-dtbs` 等包配置失败，怎么办？
* 适用产品
  * Seeed reComputer、reComputer Industrial、reServer Industrial、Robotics 等使用 Seeed 自定义 BSP/设备树的 Jetson 设备；GitHub 案例为 reComputer mini carrier board。
* 适用平台类型：seeed_device
* 简洁答案
  * 不建议在 Seeed 自定义 BSP 设备上**裸跑**完整 `sudo apt upgrade`（未安装 Seeed 安全升级 hook 前）。issue #41 说明这会拉取 NVIDIA 官方 L4T 包并覆盖 Seeed BSP。
  * **JP6.2/6.2.1 → 6.2.2（R36.5）** 已确认路径：优先 [Seeed Jetson Developer Tool OTA](../faq/j401-safe-upgrade-jetpack-6-2-2-r365.md)；备选 [r36.5.0 seeed-linux-bsp-upgrader](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0) 后再 `apt upgrade`。
* 注意事项
  * 已确认来源为 Seeed-Studio/Linux_for_Tegra issue #41，状态 closed；仍建议售后正式回复前按具体型号复核最新 Wiki。
  * issue 中失败包包括 `nvidia-l4t-bootloader`、`nvidia-l4t-kernel`、`nvidia-l4t-kernel-headers`、`nvidia-l4t-jetson-io`、`nvidia-l4t-kernel-oot-modules`、`nvidia-l4t-display-kernel`、`nvidia-l4t-kernel-oot-headers`、`nvidia-l4t-kernel-dtbs`。
  * Seeed 维护者建议如确有原因必须执行 `apt upgrade`，升级前先 hold 部分 L4T 内核/DTB/显示包：

```bash
sudo apt-mark hold nvidia-l4t-display-kernel nvidia-l4t-kernel nvidia-l4t-kernel-dtbs nvidia-l4t-kernel-headers nvidia-l4t-kernel-oot-headers nvidia-l4t-kernel-oot-modules
```

  * 这不是 NVIDIA 官方开发套件的通用限制；官方开发套件应按 NVIDIA JetPack/L4T 文档升级。
* 相关链接
  * [Seeed-Studio/Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
  * [Seeed Linux_for_Tegra](https://github.com/Seeed-Studio/Linux_for_Tegra)
  * [NVIDIA JetPack 6.2.2 页面](https://developer.nvidia.com/embedded/jetpack-sdk-622)
