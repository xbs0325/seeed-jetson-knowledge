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
source_type: internal_confirmation
source_note: "Zoho ## 366595 ## Novelic Sara Babic, 2026-08-25；支持侧确认 Linux_for_Tegra 构建里已有 GMSL overlay，但不能按 GitHub README 步骤刷。客户确认 OrbbecSDK/Viewer v2.4.8 可工作。"
status: active
---

* 问题
  * reComputer Robotics J5012（AGX Orin 64GB，模组 SKU `p3701-0005`）接 Orbbec Gemini 335Lg 走 GMSL：`jetson-io` 闪退、`/dev/video*` 不出、按 GitHub 仓库步骤刷完没有 overlay、Orbbec 最新 SDK 看不到设备，怎么处理？
* 适用产品
  * Seeed reComputer Robotics J501 / J5012（AGX Orin 64GB）及同载板 J5011（AGX Orin 32GB），配合 Robotics GMSL 扩展板 + Orbbec Gemini 335Lg。
* 适用平台类型：seeed_device
* 简洁答案
  * **按 Wiki 刷对应模组容量的官方 GMSL 镜像**（64GB 用 64GB 行），不要按 GitHub `Linux_for_Tegra` README 的构建/刷机步骤做。刷完后 `jetson-io` 选 **Orbbec Gemini 335Lg** overlay，相机 DIP 拨到 **M**。
  * GMSL 取流请使用文档指定的 **OrbbecSDK / OrbbecViewer v2.4.8**，不要默认装最新版。这是本单对外要记的重点。
* 注意事项
  * Seeed GMSL/Orbbec overlay **在 BSP 构建里是有的**。客户按 GitHub 公开步骤 `l4t_initrd_flash.sh` + `recomputer-robo-agx-orin-j501x` 刷出来的系统，经常看不到这些 `.dtbo`。售后不要说「仓库里没有 overlay」，应说：**不要按 GitHub 步骤刷，走 Wiki 官方镜像**。
  * Wiki J501 刷机表 **JetPack 6.2.1 / AGX Orin 64GB / GMSL ✅** 是 J5012 的官方路径；32GB 不要用 64GB 行。
  * `reserver-agx-orin-j501x-gmsl.conf` 是 **reServer** 配置，不是 Robotics J5012 的替代 DTB。
  * 部分出厂备份可能只有 `-0004` Robotics DTB。模组实际是 `-0005` 时，`jetson-io.py` 可能只闪一下就退出。处理方式是按 Wiki 重刷官方镜像，而不是手工改 `extlinux.conf` 或混用 reServer DTB。
  * J501 GMSL 扩展板解串器是 **MAX96712**。不要装 Orbbec `MIPI_Camera_Platform_Driver` 里面向 **MAX9296** 的 `copy_to_target_agx_orin_fg96.sh`。
  * 相机 DIP：**GMSL = M**，USB = U。USB 能出 `/dev/video*` 只说明相机本身正常，不能代替 GMSL overlay。
  * Orbbec 335Lg Wiki 下载链接钉在 **v2.4.8**（SDK deb + Viewer zip）。客户报告 **v2.9.3** 在 GMSL 下设备列表为空、无法取流，USB 模式两个版本都正常。对外可说「请使用文档指定的 v2.4.8」；**不要**断言已确认是 Orbbec SDK 回归，除非后续有官方/内部复现。
* 客服可复制英文简答（示例）
  * Thank you for the write-up. We have recorded this for other users. For Orbbec Gemini 335Lg over GMSL, please use OrbbecSDK/OrbbecViewer v2.4.8 as documented on the Wiki, rather than a newer release. We will look at calling that version out more explicitly.
* 相关链接
  * [reComputer Robotics J501 Getting Started（刷机与 GMSL overlay）](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
  * [Orbbec Gemini 335Lg Wiki（SDK/Viewer v2.4.8）](https://wiki.seeedstudio.com/orbbec_gemini_335lg/)
  * [OrbbecSDK v2.4.8 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.4.8)
  * [J501 JetPack 6.2.1 接口要点（本仓库）](../seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md)
