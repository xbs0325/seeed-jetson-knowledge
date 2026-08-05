---
product: Seeed Jetson devices with custom BSP
vendor: seeed
platform: seeed_device
jetpack: "6.x / 6.2.x"
l4t: "36.4.x"
tags:
  - faq
  - apt
  - bsp
  - kernel
  - bootloader
date: 2026-08-05
source_url: https://wiki.seeedstudio.com/Jetson_FAQ/
source_links:
  - https://wiki.seeedstudio.com/Jetson_FAQ/
  - https://wiki.seeedstudio.com/upgrade_software_packages_for_jetson/
  - https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
  - https://forum.seeedstudio.com/t/recomputer-j401-orin-nx-sudo-apt-upgrade-or-package-installation-error-jetpack-6-1/289628
status: active
---

* 问题
  * Seeed Jetson（reComputer Classic / Super 等）刷 Seeed BSP 后执行 `sudo apt upgrade`，`nvidia-l4t-bootloader` / `nvidia-l4t-kernel` 等包配置失败（例如 `ERROR. … recomputer-orin-*-j401- does not match any known boards`），怎么办？官方推荐的更新方式是什么？
* 适用产品
  * Seeed reComputer Classic / Super、reComputer Industrial、reServer Industrial、Robotics 等使用 Seeed 自定义 BSP / 设备树的 Jetson 设备
* 适用平台类型：seeed_device
* 简洁答案
  * **预期现象**：在 Seeed 自定义载板上，从 NVIDIA 官方源做完整 `sudo apt upgrade` **不被支持**，常在 `nvidia-l4t-bootloader` / `nvidia-l4t-kernel` 等包上失败；Seeed 板级名（如 `recomputer-orin-j401`、`recomputer-orin-super-j401`）不被 NVIDIA stock 包识别。
  * **不要**把 NVIDIA DevKit 的 apt OTA / 官方 bootloader 包当作 Seeed 设备的升级路径。
  * Seeed **未**提供替代 NVIDIA `nvidia-l4t-*` 的公开 APT 源；BSP / JetPack 升级以 Wiki 对应型号的 **mfi 完整刷机镜像**（及文档明确给出的 OTA 路径）为准。
  * 日常：用 `sudo apt update` + `sudo apt install <pkg>` 装应用；**避免**整系统 `apt upgrade`。若必须跑 upgrade，先 hold L4T 相关包。
  * 已半配置失败、系统异常时：优先按对应型号 Wiki **重新刷 Seeed 镜像**；刷完后立即 hold，避免再次踩坑。
* 客服可复制简答（英文要点）
  1. Yes — full `apt upgrade` from NVIDIA repos is expected to fail / is not recommended on Seeed custom BSP boards.
  2. Use Seeed Wiki mfi / BSP images; there is no Seeed APT repo that replaces NVIDIA L4T bootloader/kernel packages for these board IDs.
  3. After reflash, the same apt upgrade failure will recur unless L4T packages are held / upgrade is avoided.
  4. Long-term: install apps with `apt install`; keep JetPack/BSP via Seeed full image (or Seeed-documented OTA); hold nvidia-l4t-* kernel packages.
  5. JP 6.2.x → newer Seeed-supported 6.2.x / later: prefer reflash with the matching Seeed image; do not rely on stock NVIDIA apt for bootloader/kernel.
* hold 命令（issue #41 / Forum 常用）

```bash
sudo apt-mark hold nvidia-l4t-display-kernel nvidia-l4t-kernel nvidia-l4t-kernel-dtbs nvidia-l4t-kernel-headers nvidia-l4t-kernel-oot-headers nvidia-l4t-kernel-oot-modules
```

  * 客户错误若落在 `nvidia-l4t-bootloader`，也可一并 hold：`sudo apt-mark hold nvidia-l4t-bootloader`（Wiki Q15 示例为 `nvidia-l4t-core`；以降低 L4T 包被 NVIDIA 源覆盖为准）。
* 注意事项
  * 这不是单机故障；多台复现符合预期。
  * 设备信息里 `COMPATIBLE_SPEC` / 板级名含 `recomputer-orin-super-j401` → **Super**；`recomputer-orin-j401` → **Classic**。刷机链接勿混用。
  * 可单独 `apt install`（如 firefox、nvidia-jetpack 组件）；禁止的是无保护的整包 `apt upgrade`。
  * 应用层安全更新：对确认不依赖 L4T 系统包的软件用 `apt install`；开源可自行编译；系统级安全/驱动以 Seeed 发布的完整 JetPack 镜像为准（Wiki Q9）。
* 相关链接
  * [Seeed Jetson FAQ Q8 / Q15](https://wiki.seeedstudio.com/Jetson_FAQ/)
  * [Upgrade Software Packages for Jetson (Q9)](https://wiki.seeedstudio.com/upgrade_software_packages_for_jetson/)
  * [Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
  * [Forum: J401 apt upgrade](https://forum.seeedstudio.com/t/recomputer-j401-orin-nx-sudo-apt-upgrade-or-package-installation-error-jetpack-6-1/289628)
  * [reComputer Classic Flash](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
  * [reComputer Super Getting Started](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/)
