---
product: reComputer Mini J5012 with GMSL
vendor: seeed
platform: seeed_device
sku: "100085113"
tags:
  - staging
  - bom
  - packing-list
  - quote
date: 2026-07-28
source_links:
  - https://www.seeedstudio.com/reComputer-Mini-J5012-with-GMSL-Extension-p-6878.html
  - https://wiki.seeedstudio.com/recomputer_j501_mini_getting_started/
  - https://www.seeedstudio.com/reComputer-Jetson-AGX-Orintm-Developer-Kit-GMSL-Bundle.html
status: need_review
---

# staging：Mini J5012 with GMSL（SKU 100085113）完整装箱单待确认

## 背景

韩国高丽大学客户询价 SKU **100085113**（官网 Early Bird 标价 USD 3,899），需确认整机配件清单。商详页抓取内容未列出完整 Part List；Wiki Part List 主要对 **Mini J501 载板**；Developer Kit GMSL Bundle（`E26020301`）有可配置配件，但价格体系与 `100085113` 不一致。

## 待产品 / 销售确认

1. `100085113` 是否固定包含：
   - Jetson AGX Orin 64GB 模组（预期是）
   - Mini J501 + GMSL 扩展板（预期是）
   - 模组用 heatsink + cooling fan（预期有，需确认）
   - NVMe SSD 及 **确切容量**
   - 19V/4.74A AC/DC 适配器
   - 地区 AC 电源线（韩国 Type C/F 是否可提供）
   - Mini-Fakra / GMSL 相机线（预期不含，需书面确认）
   - 安装螺丝 / 壁挂件等
2. 预装 JetPack 确切版本（商详写 JP6.2，Wiki 写 6.2.1）及是否已含 GMSL overlay/驱动。
3. `100085113`（约 $3899 Early Bird）与 `E26020301` Developer Kit GMSL Bundle（64GB 配置约 $2143 量级，第三方报道）的产品差异与报价口径。
4. 韩国出货：电源线、KC 认证相关说明是否需写在 PI 上。

## 确认后动作

- 将确认后的 BOM 写入 `docs/faq/` 或 `docs/seeed_device/recomputer-robotics/`，`status: active`，并更新 `INDEX.md`。
- 同步销售报价模板口径。
