---
product: Seeed Jetson product lines
vendor: seeed
platform: common
jetpack: "5.x / 6.x / 7.x"
l4t: "35.x / 36.x / 39.x"
tags:
  - product-line
  - disambiguation
  - j401
  - j501
  - h01
  - a603
  - support-routing
date: 2026-06-29
source_links:
  - https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
  - https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/
status: active
---

# Seeed Jetson 产品线辨析

## 目的

Seeed Jetson 产品线命名相近，客服和 Agent 容易把刷机包、BSP、GMSL、接口、SDK Manager 路径混用。处理技术问题时，应先确认客户具体产品、SKU、载板或整机形态，再引用对应 Wiki 和知识库条目。

## 事实

| 名称 | 常见模组 | 典型定位 | 关键注意 |
| --- | --- | --- | --- |
| reComputer J401/J301 Classic | Orin NX / Orin Nano | 标准 reComputer 载板/整机 | Classic J401 Wiki 不等于 Super 或 Robotics |
| reComputer Super J401 | Orin NX / Orin Nano | Super/MAXN 模式载板 | 使用 Super 对应 mfi/board name，不混用 Classic J401 |
| reComputer Robotics J401 | Orin NX / Orin Nano | 机器人载板，CAN/GMSL/多 USB | GMSL 路径与 Super J401 不同，需对应 BSP/overlay |
| reComputer Robotics J501 / J501 Mini | AGX Orin 32GB/64GB | AGX Orin 机器人/工业边缘 AI | 面向 AGX Orin，GMSL、CAN、DI/DO 依赖 J501 BSP |
| reComputer Industrial J4012 | Orin NX 16GB | 工业无风扇边缘 AI 盒子 | 2x RJ45，工业接口，使用 Industrial Wiki/BSP |
| reServer Industrial J4012 | Orin NX 16GB | 工业 AI/NVR server | 5x RJ45/PoE/SATA，更适合多 IP camera/NVR 场景 |
| AGX Orin H01 Kit | AGX Orin 32GB 等 | 套件/载板方案 | 不应默认当 reComputer/reServer；硬件细节可能需合作伙伴确认 |
| A603 / A601 等载板 | Orin NX/Nano 或 AGX 系列视型号而定 | 合作伙伴/代理/非标准 reComputer 形态可能存在 | Bazaar 或 Wiki 不一定完整；需确认来源、载板版本、公开资料 |
| NVIDIA 官方 Developer Kit | NVIDIA 官方套件 | NVIDIA 参考开发套件 | SDK Manager/官方镜像流程只默认适用于 NVIDIA 官方套件 |

## 推断

- 名称里都有 J401/J4012，不代表载板、BSP、刷机命令、GMSL 驱动或接口完全一致。
- Seeed 载板/整机通常需要 Seeed 对应 Wiki、镜像、BSP、device tree、overlay；不能直接套用 NVIDIA DevKit 流程。
- H01、A603、A601 等非 reComputer/reServer 命名产品，可能涉及合作伙伴或代理产品。公开资料不足时，应明确转内部/合作伙伴确认。

## 建议

处理客户问题时优先确认：

1. 产品完整名称、SKU、照片或订单页。
2. 是 NVIDIA 官方 DevKit、Seeed 标准产品，还是合作伙伴/代理产品。
3. 使用的 JetPack/L4T 版本与镜像来源。
4. 问题涉及的接口或外设是否依赖 Seeed BSP/overlay。

## 禁止

- 不要把 Classic J401、Super J401、Robotics J401 的刷机包或 board name 混用。
- 不要把 Super J401 的 MIPI CSI 说明当成 Robotics J401/J501 的 GMSL 支持说明。
- 不要把 NVIDIA AGX Orin Developer Kit 的 camera、pinout、SDK Manager 流程默认套到 H01 或其他合作伙伴载板。
- 不要仅凭 Seeed 标识判断某产品一定有完整公开 Wiki、BSP 或开源硬件资料。

## 客服提示

如果产品线不确定，优先问客户提供 SKU、产品链接、外壳铭牌或板卡照片；不要先给刷机包或兼容性结论。
