---
product: Seeed Jetson carrier boards (J401 / Industrial / Super / Robotics J501 / reServer Industrial / reComputer R1000)
vendor: seeed
platform: seeed_device
tags:
  - faq
  - rtc
  - battery
  - maintenance
date: 2026-06-22
source_links:
  - https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
  - https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
  - https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
  - https://wiki.seeedstudio.com/recomputer_r/
  - https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v4.0/release/jetson_orin_nano_series_modules_data_sheet_ds-11105-001_v1.5.pdf
  - https://forums.developer.nvidia.com/t/jetson-orin-nano-rtc-power-consumption/307386/3
  - https://forums.developer.nvidia.com/t/jetson-orin-nano-orin-series-rtc-power-consumption/362502/11
status: need_review
---

* 问题
  * Seeed Jetson 载板 RTC 备用电池在正常使用下预期寿命是多少？是否有官方建议更换周期？
* 适用产品
  * 带 RTC 电池座的 Seeed Jetson 载板/整机（如 reComputer J401、reComputer Industrial、reComputer Super、reComputer Robotics J501、reServer Industrial、reComputer R1000 等）
* 适用平台类型：seeed_device
* 简洁答案
  * **已确认**：Seeed Jetson 载板 Wiki 说明了 RTC 电池型号与安装方式，但**未给出固定更换周期或官方预期寿命数值**。
  * **已确认（按型号）**：多数载板使用 **3V CR1220**；reComputer Super 使用 **3V CR1225**；reComputer R1000 预装 **CR2032**。
  * **已确认（Jetson Orin 模组 RTC 耗电）**：载板 RTC 电池为 Jetson 模组 **PMIC_BBAT** 供电；NVIDIA Orin Nano 系列 Data Sheet 写明电池备份工作电流为 **12–50 µA**（不可调）。这与 reTerminal 等独立 PCF8563 RTC（约 0.25 µA）**不是同一量级**。
  * **估算（按 NVIDIA 电流 + 电池容量，非 Seeed 官方承诺）**：
    * CR1220（约 40 mAh）：断电且 RTC 已启用时，约 **1–5 个月**（12 µA 理论上限约 4.6 个月；50 µA 约 1 个月；社区实测约 16 µA 时约 3–4 个月）。
    * CR1225（容量与 CR1220 相近）：量级与 CR1220 类似，**约 1–5 个月**。
    * CR2032（约 225 mAh，如 R1000）：约 **6 个月–2 年**（50 µA 约 6 个月；12 µA 理论上限约 2 年）。
  * **重要区分**：若设备**长期上电、仅偶尔断电**，日历时间上的电池寿命会显著长于「持续断电」理论值；实际以断电后 `hwclock` 能否保持时间为准。
  * **维护建议**：Seeed **无固定预防性更换周期**；断电后时间丢失即更换同规格非充电纽扣电池。对 CR1220/CR1225 载板，**不宜向客户承诺「可维持 3 年」**。
* 注意事项
  * 必须使用**非充电式**纽扣电池；PMIC_BBAT 不支持充电，不可接可充电电池或超级电容（除非外部独立充电电路，见 NVIDIA Design Guide）。
  * 安装时正极（+）朝上（Seeed Wiki 通用说明）。
  * RTC 需先完成配置/启用后，备份电流才代表真实待机耗电（NVIDIA 社区实测反馈）。
  * reTerminal 使用独立 PCF8563 + CR1220，备份电流约 0.25 µA，**不能代表 Jetson Orin 载板 RTC 寿命**。
* 相关链接
  * [J401 Interfaces Usage – RTC](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/)
  * [reComputer Industrial J40/J30 – RTC](https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/)
  * [reComputer Super – RTC (CR1225)](https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/)
  * [reComputer Robotics J501 – RTC](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
  * [reComputer R1000 – RTC (CR2032)](https://wiki.seeedstudio.com/recomputer_r/)
  * [Jetson Orin Nano Series Data Sheet – PMIC_BBAT 12–50 µA](https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v4.0/release/jetson_orin_nano_series_modules_data_sheet_ds-11105-001_v1.5.pdf)
  * [NVIDIA Forum – Orin RTC 50 µA worst case](https://forums.developer.nvidia.com/t/jetson-orin-nano-rtc-power-consumption/307386/3)
  * [NVIDIA Forum – 实测约 16.2 µA](https://forums.developer.nvidia.com/t/jetson-orin-nano-orin-series-rtc-power-consumption/362502/11)
