---
product: Seeed Jetson devices (reComputer 等)
vendor: seeed
platform: seeed_device
jetpack: "6.x"
tags:
  - faq
  - apt
  - browser
  - upgrade
date: 2026-06-12
source_url: https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
source_links:
  - docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md
status: active
---

* 问题
  * Seeed Jetson 镜像默认没有浏览器，能否自己安装？与「不要用 apt upgrade」是否矛盾？
* 适用产品
  * Seeed reComputer / reComputer Super / Industrial / reServer 等使用 Seeed 自定义 BSP 的 Jetson 设备
* 适用平台类型：seeed_device
* 简洁答案
  * **可以自己装浏览器**，例如：
    ```bash
    sudo apt update
    sudo apt install firefox
    ```
  * 不建议的是 **`sudo apt upgrade` 整系统升级**（可能升级 `nvidia-l4t-kernel`、`nvidia-l4t-kernel-dtbs` 等与 Seeed BSP 冲突），**不是禁止 `apt install` 单个软件**。
* 注意事项
  * JetPack / 系统大版本升级请走 Seeed Wiki 镜像刷机或 OTA，不要习惯性 full upgrade。
  * 若必须 `apt upgrade`，升级前 hold L4T 相关包，见 [apt upgrade 冲突 FAQ](seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md)（该条仍为 `need_review`）。
* 客服可复制简答
  * 您好，系统默认可能不带浏览器，可以执行 `sudo apt update && sudo apt install firefox` 自行安装。我们提醒的是尽量不要整包 `sudo apt upgrade`，以免升级 NVIDIA L4T 内核包与 Seeed BSP 冲突；单独 `apt install` 装软件一般没问题。
* 相关链接
  * [Seeed Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
