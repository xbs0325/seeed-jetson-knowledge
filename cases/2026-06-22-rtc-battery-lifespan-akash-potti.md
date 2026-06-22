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
- **参考答复**：行业资料下 RTC 备份场景常见可用期约 3–5 年；以断电后时间是否保持为准决定是否更换。
- 客户未提供具体产品型号，外发邮件中已按常见 Seeed Jetson 载板说明，并建议其告知型号以便精确确认电池规格。

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
- https://wiki.seeedstudio.com/reTerminal-hardware-interfaces-usage/
- https://wiki.seeedstudio.com/recomputer_r/
- https://www.murata.com/-/media/webrenewal/products/batteries/micro/cr/tcn-cr-001-200722.ashx

## PR

- cursor/rtc-battery-lifespan-faq-1963
