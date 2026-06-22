---
date: 2026-06-22
channel: other
product: reComputer Industrial J4012 (Jetson Orin NX 16GB)
resolved: yes
confidence: need_review
---

## 问题摘要

英文客户 Akash Potti 已成功安装 RTC 电池，询问：
1. 正常使用条件下 RTC 电池预期寿命；
2. 是否有建议更换周期。

**产品型号（已确认）**：reComputer Industrial J4012，Jetson Orin NX 16GB。

## 答复要点

- **已确认（产品）**：J4012 属 reComputer Industrial J40/J30 系列；RTC 板载座为 **3V CR1220**（正极朝上），可选 2-pin JST 外接 CR2032（二选一，见 Wiki）。
- **已确认**：Wiki 未发布固定更换周期；JetPack 6 及以上 RTC 无需额外配置即可工作。
- **已确认（耗电）**：Orin NX 模组 PMIC_BBAT 备份电流与 Orin 系列一致，NVIDIA 规格 **12–50 µA**。
- **估算**：CR1220 持续断电备份约 **1–5 个月**；设备长期上电、仅偶尔断电时日历寿命更长。**不宜承诺 3 年**。
- **维护建议**：断电后 `sudo hwclock` 验证；时间丢失即更换同规格非充电 CR1220。

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
