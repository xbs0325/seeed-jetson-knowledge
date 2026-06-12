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
  * 不建议的是 **`sudo apt upgrade` 整系统升级**（可能升级 L4T 内核包与 Seeed BSP 冲突），不是禁止 `apt install`。
* 客服可复制简答
  * 可以自行安装浏览器，例如 `sudo apt install firefox`。请勿习惯性整包 `sudo apt upgrade`；单独安装软件一般没问题。
* 相关链接
  * [Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
  * [staging：apt upgrade 详情](../staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md)
