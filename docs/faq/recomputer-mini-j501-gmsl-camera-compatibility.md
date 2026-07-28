---
product: reComputer Mini J501 / Mini J5012 with GMSL
vendor: seeed
platform: seeed_device
jetpack: "6.2.1 / 7.2"
l4t: "36.4.4 / 39.2"
tags:
  - faq
  - gmsl
  - camera
  - mini-j501
  - j5012
  - max96712
sku: "100085113"
date: 2026-07-28
source_links:
  - https://wiki.seeedstudio.com/recomputer_j501_mini_getting_started/
  - https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_mini_J501_datasheet.pdf
  - https://www.seeedstudio.com/reComputer-Mini-J5012-with-GMSL-Extension-p-6878.html
  - https://www.seeedstudio.com/reComputer-Jetson-AGX-Orintm-Developer-Kit-GMSL-Bundle.html
status: active
---

# reComputer Mini J501 / Mini J5012 GMSL：兼容性与标配要点

## 问题

客户询价 / 技术确认 reComputer Mini J5012 with GMSL 时，常问：整机含哪些硬件、GMSL 接口规格、第三方索尼/车规摄像头能否直连、需要哪些相机资料才能判断兼容性。

## 适用产品

- reComputer Mini J5012 with GMSL（AGX Orin 64GB，SKU `100085113`）
- reComputer Mini J5011 with GMSL（AGX Orin 32GB）
- reComputer Mini J501 Carrier Board with GMSL Extension（SKU `100020039` 等）
- 相关可配置套件：reComputer Jetson AGX Orin Developer Kit GMSL Bundle（SKU `E26020301`）

## 事实（公开资料已确认）

### 平台与软件

- Mini J5012 = Mini J501 载板 + **Jetson AGX Orin 64GB** + GMSL 扩展形态；商详标注预装 **JetPack 6.2**（Wiki 写 **6.2.1**），并提供带 GMSL 驱动的 **JetPack 7.2** 镜像。
- 刷机须使用 Seeed Mini J501 对应 mfi 包，不可默认套用 NVIDIA AGX Orin Developer Kit 官方镜像流程。
- Wiki 质保标注：**2 Years**；认证含 RoHS、REACH、CE、FCC、UKCA、**KC**。

### GMSL 硬件

- GMSL 扩展板解串器：**MAX96712**（Mini J501 datasheet）。
- 接口： **2x Mini-Fakra**（4-in-1），datasheet 写 **Up to 8x GMSL2**；连接方式为 GMSL2 Fakra 1-to-4 M-M 线缆。
- **POC（Power-over-Coax）**：datasheet 标注支持电源与数据同传。
- Wiki 正文有一处写「可同时连接并运行 four GMSL cameras」，但同页 `media-ctl` 示例覆盖 **ser_0…ser_7 / des_0…des_1**（8 路）。对外说明优先以 datasheet「最多 8 路」为准，同时提示客户以实际 BSP overlay / 联调结果为准。

### 官方已验证摄像头（Wiki）

- SG3S-ISX031C-GMSL2F
- SG2-AR0233C-5200-G2A
- SG2-IMX390C-5200-G2A
- SG8S-AR0820C-5300-G2A
- Overlay 另含 Orbbec Gemini 335Lg

Jetson-IO overlay 示例：`Seeed GMSL 1X4 3G`（SG3S）、`Seeed GMSL 1X4 6G`（SG2/SG8S）、Orbbec overlay。

### 配件边界（易与「整机是否标配」混淆）

| 项目 | 公开资料结论 |
| --- | --- |
| AGX Orin 64GB（J5012） | 产品定义包含 |
| Mini J501 + GMSL 扩展 | 产品定义包含 |
| Mini-Fakra / GMSL 相机线 | 商详可选购 **Mini-Fakra 4-in-1 Cable**；**不作为默认已含相机线** |
| 19V/4.74A 适配器、地区 AC 线 | Wiki 推荐适配器；Bundle 页可加购；电源线仅见 US/UK/EU/JP/CN，**未见韩国专用线 SKU** |
| 载板包装清单（Wiki Part List） | 载板、电源/JST 扩展板、XT30-DC 线、USB-A-C、扩展板散热片、螺丝螺柱、说明书等；**不含模组/SSD/市电适配器表述** |
| Developer Kit GMSL Bundle 可选件 | 可选 heatsink with fan、128/256/512GB NVMe、19V 适配器、地区电源线、Wi-Fi 套件、GMSL 相机与线缆 |

**SKU `100085113` 官网抓取页未给出完整 BOM 明细**（SSD 容量、是否含风扇散热器/适配器/电源线）→ 报价前须产品/销售确认装箱单。

### 第三方 / 未验证相机（含索尼、Hyundai Mobis 指定机）

- 不在上述官方列表内时，**不能承诺兼容或免驱可用**。
- 判断兼容性至少需要客户提供：完整相机型号与料号、Sony sensor 型号、**GMSL2 serializer 型号**、连接器与 pin/线序、POC 电压与电流需求、分辨率与帧率、目标 JetPack/L4T、是否已有 BSP/驱动/device tree。
- 板端为 **MAX96712**；serializer 与链路速率（3G/6G）、数据格式须与 Seeed GMSL overlay/驱动匹配；否则通常需定制驱动与 device tree，耗时与可行性需硬件/BSP 团队评估。

## 建议

1. 询价邮件：技术侧先回复「标配边界 + GMSL 规格 + 需客户补齐的相机资料」；价格/库存/运费/Incoterms/税务/学术折扣一律转销售。
2. 若客户相机非官方列表：明确「currently not in our validated camera list」，请发 datasheet；不要写「支持」或「不支持」的绝对结论。
3. 韩国 AC 线：公开 SKU 无 KR；可与销售确认是否可用 EU cloverleaf 或需本地采购。
4. 注意别与 **reComputer Robotics J5012**（SKU `100032662`，带壳工业整机）混淆。

## 禁止

- 不承诺 Hyundai Mobis / 任意索尼 GMSL2 相机开箱即用。
- 不把 Robotics J501、reServer Industrial J501、Mini J501 的解串器/摄像头教程混用而不核对产品。
- 不在未核对立装箱单前断言 `100085113`「一定含 / 一定不含」SSD 容量或电源适配器。
