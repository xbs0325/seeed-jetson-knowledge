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
review_reason: "Seeed issue is closed and the conclusion is reusable, but latest per-product Wiki should be checked before promotion."
next_action: "If still consistent with current Wiki/BSP guidance, promote to active FAQ and update INDEX.md."
---

* 问题
  * Seeed Jetson 设备刷 JetPack 6.2 后，执行 `sudo apt upgrade` 导致 `nvidia-l4t-kernel`、`nvidia-l4t-bootloader`、`nvidia-l4t-kernel-dtbs` 等包配置失败，怎么办？
* 适用产品
  * Seeed reComputer、reComputer Industrial、reServer Industrial、Robotics 等使用 Seeed 自定义 BSP/设备树的 Jetson 设备；GitHub 案例为 reComputer mini carrier board。
* 适用平台类型：seeed_device
* 简洁答案
  * 不建议在 Seeed 自定义 BSP 设备上直接执行完整 `sudo apt upgrade`。Seeed GitHub issue 中维护者说明：`apt upgrade` 会更新官方 BSP 包，可能与 Seeed 自定义 BSP 冲突，导致系统异常。需要升级时应优先按 Seeed Wiki/BSP/OTA 指南处理。
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
