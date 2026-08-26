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
source_type: customer_confirmation
source_note: "Zoho ## 366595 ## Novelic Sara Babic, 2026-08-25；客户在 J5012 (p3701-0005, 64GB) 上自行确认 Wiki 官方镜像 + OrbbecSDK/Viewer v2.4.8 可工作"
status: active
---

* 问题
  * reComputer Robotics J5012（AGX Orin 64GB，模组 SKU `p3701-0005`）接 Orbbec Gemini 335Lg 走 GMSL：`jetson-io` 闪退、`/dev/video*` 不出、公共 GitHub 构建缺 overlay、Orbbec 官方最新 SDK 看不到设备，怎么处理？
* 适用产品
  * Seeed reComputer Robotics J501 / J5012（AGX Orin 64GB）及同载板 J5011（AGX Orin 32GB），配合 Robotics GMSL 扩展板 + Orbbec Gemini 335Lg。
* 适用平台类型：seeed_device
* 简洁答案
  * **先刷 Wiki 对应模组容量的官方 GMSL 镜像**（64GB 用 64GB 行，不要用 32GB 行），再 `jetson-io` 选 **Orbbec Gemini 335Lg** overlay，相机 DIP 拨到 **M**。
  * GMSL 取流请使用文档指定的 **OrbbecSDK / OrbbecViewer v2.4.8**，不要默认装最新版。
* 注意事项
  * Wiki J501 刷机表里 **JetPack 6.2.1 / AGX Orin 64GB / GMSL ✅** 这一行，才是 J5012 的官方路径。该镜像同时带匹配的 Robotics **`-0005` DTB** 和 Seeed GMSL/Orbbec **`.dtbo`**。
  * 公共仓库 `Seeed-Studio/Linux_for_Tegra` 按 `recomputer-robo-agx-orin-j501x` 自行构建，常能得到正确的 `-0005` DTB，但**不含** Seeed GMSL/Orbbec overlay；不能当 GMSL 出厂镜像用。
  * `reserver-agx-orin-j501x-gmsl.conf` 是 **reServer** 配置，不是 Robotics J5012 的替代 DTB。
  * 部分出厂备份可能只有 `kernel_tegra234-j501x-0000+p3701-0004-recomputer-robo.dtb`。模组实际是 `-0005` 时，`jetson-io.py` 可能只闪一下就退出。处理方式是重刷 Wiki 官方镜像，而不是手工改 `extlinux.conf` 或混用 reServer DTB。
  * J501 GMSL 扩展板解串器是 **MAX96712**。不要装 Orbbec `MIPI_Camera_Platform_Driver` 里面向 **MAX9296** 的 `copy_to_target_agx_orin_fg96.sh`。
  * 相机 DIP：**GMSL = M**，USB = U。USB 能出 `/dev/video*` 只说明相机本身正常，不能代替 GMSL overlay。
  * Orbbec 335Lg Wiki 下载链接钉在 **v2.4.8**（SDK deb + Viewer zip）。客户报告 **v2.9.3** 在 GMSL 下设备列表为空、无法取流，USB 模式两个版本都正常。对外可说「请使用文档指定的 v2.4.8」；**不要**断言已确认是 Orbbec SDK 回归，除非后续有官方/内部复现。
* 客服可复制英文简答（示例）
  * For GMSL on Robotics J5012 (AGX Orin 64GB), please flash the Wiki JetPack 6.2.1 / AGX Orin 64GB / GMSL image first — not a generic GitHub Linux_for_Tegra build. That package includes the matching Robotics DTB and our GMSL/Orbbec overlays. After flashing, set the camera DIP to M, run `sudo /opt/nvidia/jetson-io/jetson-io.py`, select the Orbbec Gemini 335Lg overlay, and reboot. For streaming, please use OrbbecSDK/OrbbecViewer v2.4.8 as documented on the Wiki, rather than a newer release.
* 相关链接
  * [reComputer Robotics J501 Getting Started（刷机与 GMSL overlay）](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
  * [Orbbec Gemini 335Lg Wiki（SDK/Viewer v2.4.8）](https://wiki.seeedstudio.com/orbbec_gemini_335lg/)
  * [OrbbecSDK v2.4.8 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.4.8)
  * [J501 JetPack 6.2.1 接口要点（本仓库）](../seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md)
