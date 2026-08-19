---
date: 2026-08-12
channel: internal
reply_to: user_internal
product: Seeed J401 全系
issue_type: other
confidence: confirmed
final_customer_reply: false
---

## 问题摘要

内部条目 **R-02**：JP6.2→6.2.2 安全升级工具（`seeed-linux-bsp-upgrader`）推广不足。2026-06 论坛用户仍不知正确升级路径，仍按「千万别 apt upgrade」理解；社区误用 NVIDIA DevKit 裸 `apt upgrade` 口径。

## 核对资料

- [Linux_for_Tegra r36.5.0 Release](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0)（2026-05-26）：upgrader deb + upgrade bundle + apt-hook SOP。
- [Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)：裸 apt upgrade 与 Seeed BSP 冲突。
- [Seeed Jetson Developer Tool](https://github.com/Seeed-Projects/Seeed-Jetson-DevelopTool)：OTA Update 四步引导；J401 已有 JP5.1.3→JP6.2、JP6.x→JP7.2 等路径；JP6.2→6.2.2 以客户端列表为准。
- [论坛帖 295471](https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471)：用户反馈裸 upgrade 会损坏 J401 内核。

## 最终结论

- **口径调整**：「禁止裸 apt upgrade」→「须先走 Seeed 安全升级（DevelopTool OTA 首选，或 r36.5.0 upgrader 手动 SOP）再 upgrade」。
- **渠道建议**：Wiki 全 J 系列分散补手动命令覆盖面大、不便；**售后首推 Seeed Jetson Developer Tool OTA**；手动 upgrader 作备选/高级。
- **验收方向**：用户凭 FAQ + DevelopTool 或 Release SOP 完成 R36.4.x→R36.5.0，减少裸 upgrade 返工。

## 知识库更新

- [x] `docs/faq/j401-safe-upgrade-jetpack-6-2-2-r365.md`（active）
- [x] 更新 `docs/faq/seeed-jetson-install-browser-vs-apt-upgrade.md`
- [x] 更新 `docs/official_kit/common/jetpack-6-2-2-l4t-r36-5-release.md`
- [x] 更新 `docs/staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md`（指向 active FAQ）
- [x] 更新 `INDEX.md`

## 待跟进（非本 PR）

- 各 J 系列 Flash/升级 Wiki 醒目入口、论坛置顶 SOP：需 Wiki 仓库侧落地。
- DevelopTool 是否已/将 bundled JP6.2→6.2.2 OTA 路径：以客户端 `ota_paths.json` 为准，FAQ 已注明。
