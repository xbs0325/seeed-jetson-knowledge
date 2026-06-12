---
product: Seeed Jetson devices (reComputer Super 等)
vendor: seeed
platform: seeed_device
jetpack: "6.2"
tags:
  - inbox
  - apt
  - browser
date: 2026-06-12
collected_at: 2026-06-12
source_url: https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
source_links:
  - docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md
status: need_review
resolution: pending
---

* 问题
  * Seeed Jetson 镜像默认没有浏览器，能否自己安装？与「不要用 apt upgrade」是否矛盾？
* 简洁答案（待复核）
  * **可以自己装浏览器**，例如 `sudo apt update && sudo apt install firefox`。
  * 不建议的是 **`sudo apt upgrade` 整系统升级**（可能升级 `nvidia-l4t-kernel` 等与 Seeed BSP 冲突的包），不是禁止 `apt install` 单个软件。
* 注意事项
  * 系统大版本升级请走 Seeed Wiki / 官方镜像刷机或 OTA，不要习惯性 full upgrade。
* 相关链接
  * [Seeed Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
