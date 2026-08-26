---
date: 2026-08-26
channel: zoho
reply_to: customer
product: reComputer Robotics J5012 (AGX Orin 64GB, p3701-0005) + Orbbec Gemini 335Lg
issue_type: gmsl
resolved: yes
confidence: confirmed
final_customer_reply: true
---

## 问题摘要

Zoho **## 366595 ##**。Novelic（Sara Babic）两台 reComputer Robotics J5012，Orbbec Gemini 335Lg 走 GMSL。USB 模式 `/dev/video*` 正常。

客户先后遇到：

1. 出厂镜像 `jetson-io.py` 闪退；`/boot/dtb/` 只有 `-0004` Robotics DTB，模组实际是 **p3701-0005**。
2. 手工改 `extlinux.conf` 后驱动有加载，但仍无 `/dev/video*`。
3. 按 GitHub README（r36.4.4 / `recomputer-robo-agx-orin-j501x`）刷出 `-0005` DTB，但 `/boot` 里看不到 Seeed GMSL/Orbbec `.dtbo`。源码里有 overlay DTS：https://github.com/Seeed-Studio/Linux_for_Tegra/blob/r36.4.3/source/hardware/nvidia/t23x/nv-public/overlay/tegra234-seeed-orbbec-335lg-overlay.dts
4. 误装 Orbbec `copy_to_target_agx_orin_fg96.sh`（MAX9296，不是板上 MAX96712）。
5. 问 `reserver-agx-orin-j501x-gmsl.conf` 的 `-0005-reserver-gmsl.dtb` 能否用在 Robotics J5012。

前一轮已建议按 Wiki 刷 **JetPack 6.2.1 / AGX Orin 64GB / GMSL** 官方镜像后再做 jetson-io。

## 客户结案结论（2026-08-25）

客户自行确认已解决：

1. **镜像**：Wiki 官方镜像同时带匹配 DTB 和 overlay，GMSL 能起来。内部口径：源码有 DTS，不要说「GitHub 通用构建不能替代官方镜像」；应说请走 Wiki 刷机步骤，不要只跟 GitHub README。
2. **SDK**：OrbbecSDK/OrbbecViewer **v2.9.3** 在 GMSL 下设备列表为空、无法取流；降到 Wiki 安装步骤里的 **v2.4.8** 立即正常。USB 模式两个版本都不受影响。客户将固定使用 v2.4.8，并建议 Wiki 把版本钉得更醒目。

## 答复要点

- 外发两条都留：Wiki 官方镜像路径 + SDK **v2.4.8**。第一点不要写成源码没有设备树。
- 不把 v2.9.3 写成「已确认的 Orbbec SDK bug」。
- PR：https://github.com/xbs0325/seeed-jetson-knowledge/pull/48

## 知识库更新

- [x] `docs/faq/j501-orbbec-335lg-gmsl-wiki-image-sdk-248.md`（active）
- [x] `docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md`（补充 GMSL / 335Lg）
- [x] `INDEX.md`
- [ ] Wiki 加粗 v2.4.8 警告（客户建议，尚未改公开 Wiki）

## 来源

- https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
- https://wiki.seeedstudio.com/orbbec_gemini_335lg/
- https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.4.8
- https://github.com/Seeed-Studio/Linux_for_Tegra/blob/r36.4.3/source/hardware/nvidia/t23x/nv-public/overlay/tegra234-seeed-orbbec-335lg-overlay.dts
- Zoho ## 366595 ## / Sara Babic（Novelic）2026-08-25 结案邮件
