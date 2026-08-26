---
product: reComputer Robotics J5012 / J5011 (AGX Orin) + Orbbec Gemini 335Lg
vendor: seeed
platform: seeed_device
jetpack: "6.2.1"
l4t: "36.4.4"
tags:
  - faq
  - gmsl
  - camera
  - orbbec
  - j501
  - dtb
  - jetson-io
date: 2026-08-26
source_links:
  - https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
  - https://wiki.seeedstudio.com/orbbec_gemini_335lg/
  - https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.4.8
  - https://github.com/Seeed-Studio/Linux_for_Tegra/blob/r36.4.3/source/hardware/nvidia/t23x/nv-public/overlay/tegra234-seeed-orbbec-335lg-overlay.dts
source_type: internal_confirmation
source_note: "Zoho ## 366595 ## Novelic Sara Babic, 2026-08-25。源码有 Orbbec overlay DTS；Wiki 官方镜像是文档化刷机路径。客户确认 OrbbecSDK/Viewer v2.4.8 可工作。"
status: active
---

* 问题
  * reComputer Robotics J5012（AGX Orin 64GB，模组 SKU `p3701-0005`）接 Orbbec Gemini 335Lg 走 GMSL：`jetson-io` 闪退、`/dev/video*` 不出、按 GitHub README 刷完 `/boot` 里看不到 overlay、Orbbec 最新 SDK 看不到设备，怎么处理？
* 适用产品
  * Seeed reComputer Robotics J501 / J5012（AGX Orin 64GB）及同载板 J5011（AGX Orin 32GB），配合 Robotics GMSL 扩展板 + Orbbec Gemini 335Lg。
* 适用平台类型：seeed_device
* 简洁答案
  * **按 Wiki 刷对应模组容量的官方 GMSL 镜像**（64GB 用 64GB 行）。源码里已有 Orbbec overlay DTS，但产品刷机请走 Wiki，不要只跟 GitHub README 的 flash 命令。刷完后 `jetson-io` 选 **Orbbec Gemini 335Lg** overlay，相机 DIP 拨到 **M**。
  * GMSL 取流请使用 Wiki 安装步骤里的 **OrbbecSDK / OrbbecViewer v2.4.8**，不要默认装最新版。
* 注意事项
  * Overlay 源文件在仓库里：[tegra234-seeed-orbbec-335lg-overlay.dts](https://github.com/Seeed-Studio/Linux_for_Tegra/blob/r36.4.3/source/hardware/nvidia/t23x/nv-public/overlay/tegra234-seeed-orbbec-335lg-overlay.dts)（r36.4.3 / r36.4.4 均有）。**不要**对外说「GitHub 通用构建不能替代官方镜像」或「源码没有设备树」。
  * 客户按 README 的 `l4t_initrd_flash.sh` + `recomputer-robo-agx-orin-j501x` 刷完，系统里经常看不到 `.dtbo`。官方镜像 / CI 会把编译出的 `tegra234-seeed-orbbec-335lg-overlay.dtbo` 拷到 `rootfs/boot/`。售后口径：**源码有 DTS；刷机请按 Wiki 官方镜像，不要只跟 GitHub README 步骤。**
  * Wiki J501 刷机表 **JetPack 6.2.1 / AGX Orin 64GB / GMSL ✅** 是 J5012 的官方路径；不要混用 32GB / 64GB 行。
  * `reserver-agx-orin-j501x-gmsl.conf` 是 **reServer** 配置，不是 Robotics J5012 的替代 DTB。
  * 部分出厂备份可能只有 `-0004` Robotics DTB。模组实际是 `-0005` 时，`jetson-io.py` 可能只闪一下就退出。处理方式是按 Wiki 重刷官方镜像，而不是手工改 `extlinux.conf` 或混用 reServer DTB。
  * J501 GMSL 扩展板解串器是 **MAX96712**。不要装 Orbbec `MIPI_Camera_Platform_Driver` 里面向 **MAX9296** 的 `copy_to_target_agx_orin_fg96.sh`。
  * 相机 DIP：**GMSL = M**，USB = U。USB 能出 `/dev/video*` 只说明相机本身正常，不能代替 GMSL overlay。
  * Orbbec 335Lg Wiki「Download and Install Orbbec Viewer」用 wget 钉在 **v2.4.8**。客户报告 **v2.9.3** 在 GMSL 下设备列表为空、无法取流，USB 模式两个版本都正常。对外可说「请按该页安装 v2.4.8」；**不要**断言已确认是 Orbbec SDK 回归。
* 客服可复制英文简答（示例）
  * Thank you for the write-up. We have recorded both findings. For GMSL on Robotics J5012, please flash the Wiki official image (matching module size, GMSL row). The Orbbec overlay source is in our Linux_for_Tegra tree; please follow the Wiki flashing steps rather than the GitHub README flash procedure. For streaming, please use OrbbecSDK/OrbbecViewer v2.4.8 as shown on the Wiki.
* 相关链接
  * [reComputer Robotics J501 Getting Started（刷机与 GMSL overlay）](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
  * [Orbbec Gemini 335Lg Wiki（SDK/Viewer v2.4.8）](https://wiki.seeedstudio.com/orbbec_gemini_335lg/)
  * [OrbbecSDK v2.4.8 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.4.8)
  * [tegra234-seeed-orbbec-335lg-overlay.dts (r36.4.3)](https://github.com/Seeed-Studio/Linux_for_Tegra/blob/r36.4.3/source/hardware/nvidia/t23x/nv-public/overlay/tegra234-seeed-orbbec-335lg-overlay.dts)
  * [J501 JetPack 6.2.1 接口要点（本仓库）](../seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md)
