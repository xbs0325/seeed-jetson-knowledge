---
date: 2026-07-29
channel: email
product: Seeed Jetson carrier boards (CSI lane count)
resolved: yes
confidence: confirmed
---

## 问题摘要

英文客户询问 Seeed Jetson carrier boards 是否支持 4-lane MIPI CSI，还是全部都是 2-lane；部分产品规格未写明 lane 数。

## 答复要点

- 不是全部 2-lane。
- Classic J401 / Super / Industrial 常见 15-pin CSI：官方规格为 **2-lane**。
- **A608** 明确为 **2×4-lane CSI**。
- J501 为每连接器 8 lanes 的扩展口（可配合 GMSL；解串侧有 4-lane MIPI），用法不同于 15-pin FPC。
- Super 的「4x CSI」= 四个 2-lane 口，不是 4-lane。
- 回复客户前建议确认具体板型与摄像头型号。

## 知识库更新

- [x] `docs/faq/seeed-jetson-carrier-mipi-csi-lane-count.md`（active）
- [x] `INDEX.md` 已更新

## 来源

- https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
- https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
- https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
- https://www.seeedstudio.com/blog/wp-content/uploads/2024/01/Seeed_A608_Carrier_Board_for_NVIDIA_Jetson_Orin_NX_Nano_Datasheet.pdf
- https://files.seeedstudio.com/wiki/Seeed_Jetson/Seeed-NVIDIA_Jetson_Catalog_V1.4.pdf
- https://wiki.seeedstudio.com/reserver_j501_getting_started/
- https://files.seeedstudio.com/wiki/reComputer-Jetson/J501/reServer_Industrial_J501_Carrier_Board_Datasheet.pdf

## PR

- draft PR（本分支）
