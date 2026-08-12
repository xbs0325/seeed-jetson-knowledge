---
product: Seeed Jetson devices
vendor: seeed
platform: seeed_device
jetpack: "6.x"
tags:
  - faq
  - apt
  - browser
date: 2026-06-12
source_url: https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
status: active
---

* 问题
  * 默认没有浏览器，能否自己安装？和「不要用 apt upgrade」矛盾吗？
* 简洁答案
  * 可以：`sudo apt update && sudo apt install firefox`。
  * 不建议的是 **未走 Seeed 安全流程的裸 `sudo apt upgrade`**（可能升级 NVIDIA 官方 L4T 包并覆盖 Seeed BSP），不是禁止 `apt install`。
  * 若需从 JP6.2/6.2.1 升到 **6.2.2（R36.5）**：优先用 [Seeed Jetson Developer Tool OTA](../faq/j401-safe-upgrade-jetpack-6-2-2-r365.md)，或先装 [seeed-linux-bsp-upgrader](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0) 再 `apt upgrade`。
* 客服可复制简答
  * 可以自行安装浏览器，例如 `sudo apt install firefox`。单独 `apt install` 一般没问题。整系统升级请不要裸跑 `sudo apt upgrade`；J401 升到 6.2.2 请用 DevelopTool OTA 或 Seeed r36.5.0 upgrader，详见 FAQ。
* 相关链接
  * [J401 安全升级至 6.2.2（R36.5）](j401-safe-upgrade-jetpack-6-2-2-r365.md)
  * [Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
  * [staging：apt upgrade 冲突背景](../staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md)
