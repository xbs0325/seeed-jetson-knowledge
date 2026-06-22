---
date: 2026-06-22
channel: other
product: reComputer J4012 (Orin NX 16GB, Classic J401 carrier)
resolved: partial
confidence: need_review
---

## 问题摘要

客户：Ubuntu 22.04 host 刷 JetPack 6.2 到 Orin NX 16GB + Classic J401 载板，刷机成功；主机出现 `L4T_README` 分区；自认为已启动，但 Dell 显示器 **No HDMI signal**。使用 **HDMI 公对公线** 直连。

客服怀疑 HDMI 转接线；需判断 J401 是否也存在类似问题。

## 答复要点

- **置信度：中高（软件/接线可验证部分）**；是否硬件故障需串口日志或换屏后确认。
- Classic J401 为 **原生 HDMI 2.1**，客户描述的 **HDMI 直连** 场景下，**优先排除 DP→HDMI 转接问题**（该问题多见于 NVIDIA DevKit DP 口）。
- `L4T_README` 在 laptop 上出现 → 提示检查是否仍接 USB-C 刷机线、跳线未拔、未正常冷启动。
- 给出分步排查：拔 USB-C / 拔跳线 / 重插电源 / 换显示器与 HDMI 线 / 确认 `recomputer-orin-j401` 刷机包 / 12-pin UART 抓日志。
- 未拿到串口日志前，不断言板子损坏。

## 知识库更新

- [x] `docs/faq/recomputer-j401-hdmi-no-signal.md`（active）
- [ ] `docs/staging/...`
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
- https://wiki.seeedstudio.com/jetson_debug_guide/
- https://github.com/Seeed-Studio/wiki-documents/discussions/1233
- https://forum.seeedstudio.com/t/newly-aquired-jetson-orin-nx-will-not-boot-up-on-inital-setup/274882

## PR

- cursor/j401-hdmi-no-signal-a066
