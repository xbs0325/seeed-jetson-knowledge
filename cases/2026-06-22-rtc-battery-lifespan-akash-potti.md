---
date: 2026-06-22
channel: other
product: Seeed Jetson carrier board (model not specified)
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户 Akash Potti 已成功安装 RTC 电池，询问：
1. 正常使用条件下 RTC 电池预期寿命；
2. 是否有建议更换周期。

## 答复要点

- **已确认**：Seeed Jetson 载板 Wiki 仅说明电池型号与安装/验证步骤，**未发布固定更换周期**。
- **已确认（型号）**：多数载板 CR1220；Super 为 CR1225；R1000 为 CR2032。
- **更正（2026-06-22）**：初版误将 reTerminal PCF8563（~0.25 µA）寿命外推到 Jetson Orin 载板。**Jetson Orin 模组 PMIC_BBAT 备份电流为 12–50 µA**（NVIDIA Data Sheet），CR1220/CR1225 在持续断电备份下约 **1–5 个月**，**不能承诺 3 年**。
- **维护建议**：以断电后 `hwclock` 是否保持为准；设备长期上电时日历寿命会更长。
- 客户未提供具体产品型号，外发邮件需按 Jetson Orin 载板更正说明。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [ ] `docs/faq/...`（active）
- [x] `docs/staging/jetson-rtc-battery-lifespan-replacement.md`（待确认）
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
- https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
- https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
- https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
- https://wiki.seeedstudio.com/recomputer_r/
- https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v4.0/release/jetson_orin_nano_series_modules_data_sheet_ds-11105-001_v1.5.pdf
- https://forums.developer.nvidia.com/t/jetson-orin-nano-rtc-power-consumption/307386/3

## PR

- cursor/rtc-battery-lifespan-faq-1963
