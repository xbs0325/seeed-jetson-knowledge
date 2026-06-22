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
  - https://wiki.seeedstudio.com/reTerminal-hardware-interfaces-usage/
  - https://wiki.seeedstudio.com/recomputer_r/
  - https://www.murata.com/-/media/webrenewal/products/batteries/micro/cr/tcn-cr-001-200722.ashx
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
  * **参考（电池/RTC 行业资料，非 Seeed Jetson 专项指标）**：RTC 备份电流极低（例如 reTerminal 文档中 PCF8563 典型备份电流约 0.25 µA），CR1220/CR1225 在非充电、常温、正常断电备份场景下，业界常见可用期约为 **3–5 年**；高温（>60°C）或长期高湿会缩短寿命。
  * **维护建议**：以功能为准——断电后若硬件时钟无法保持，即应更换同型号新电池；无固定周期时可按 **3–5 年预防性更换** 作为保守参考，并优先选用质量可靠的同规格非充电纽扣电池。
* 注意事项
  * 必须使用**非充电式**纽扣电池；CR1220/CR1225/CR2032 不可接入充电电路。
  * 安装时正极（+）朝上（Seeed Wiki 通用说明）。
  * 不同载板 RTC 芯片/电路可能不同，实际耗电略有差异；客户未说明具体型号时，应先确认产品型号与电池规格。
  * reComputer Industrial Wiki Method 2 提及 CR2032 + JST 外部连接为可选方案，与板载 CR1220 座二选一，勿混用错误规格。
* 相关链接
  * [J401 Interfaces Usage – RTC](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/)
  * [reComputer Industrial J40/J30 – RTC](https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/)
  * [reComputer Super – RTC (CR1225)](https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/)
  * [reComputer Robotics J501 – RTC](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/)
  * [reTerminal – RTC / PCF8563 backup current](https://wiki.seeedstudio.com/reTerminal-hardware-interfaces-usage/)
  * [reComputer R1000 – RTC (CR2032)](https://wiki.seeedstudio.com/recomputer_r/)
  * [Murata CR battery technical note (RTC application reference)](https://www.murata.com/-/media/webrenewal/products/batteries/micro/cr/tcn-cr-001-200722.ashx)
