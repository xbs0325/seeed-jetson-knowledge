---
date: 2025-06-18
channel: other
product: DepthEye S2 (101990866)
resolved: partial
confidence: need_review
---

## 问题摘要

Mouser 渠道客户收到 P/N 101990866（DepthEye S2 ToF 相机）1 台，Windows PC 无法识别。Device Manager 显示「Unknown USB Device (Device Descriptor Request Failed)」。客户已按手册连接，并使用 ipTIME 带独立电源的 USB 3.0 Hub，仍失败。Date code: 04/25/22，Mouser PO: 029-0H483。

## 答复要点

- 产品为 DepthEye S2，非 Jetson 模组；SDK 由 PointCloud.AI / libDepthEye 提供。
- 包装**不含** 12V 电源适配器，仅含电源线；需客户自备 **12V DC / ≥1A** 适配器。
- USB 需 **USB 3.0/3.1 Gen1**；官方 SDK 建议**带独立供电的 USB Hub**。
- 「Device Descriptor Request Failed」表示 USB 枚举阶段失败，常见原因为电源/线缆/端口问题，**尚不能仅凭当前信息判定硬件不良**。
- 建议交叉验证：确认 12V 电源规格 → 主板后置 USB 3.0 直连 → 换线/换 PC → 再考虑 RMA。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/staging/deptheye-s2-usb-troubleshooting.md`（待确认）
- [ ] `memory/...`

## 来源

- https://www.seeedstudio.com/DepthEye-S2-VGA-Resolution-ToF-Camera-p-5095.html
- https://core-electronics.com.au/deptheye-s2-h67-x-v51-vga-tof-camera-with-sony-imx556plr-depthsense.html
- https://github.com/pointcloudAI/libDepthEye
- https://learn.microsoft.com/en-us/answers/questions/5903639/unknown-usb-device-(device-descriptor-request-fail

## PR

- cursor/deptheye-s2-usb-troubleshoot-a02a
