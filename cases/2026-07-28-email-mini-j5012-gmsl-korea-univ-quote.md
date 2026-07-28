---
date: 2026-07-28
channel: zoho
reply_to: user_internal
product: reComputer Mini J5012 with GMSL (SKU 100085113)
issue_type: gmsl | accessory | quote
confidence: needs_review
resolved: partial
final_customer_reply: false
---

## 问题摘要

韩国高丽大学 Embedded Security Laboratory（TaeHeon Kim）向 APAC Sales 询价 1 台 reComputer Mini J5012 with GMSL（官网 USD 3,899），要求官方报价/形式发票，并确认标配配件清单；同时计划连接 Hyundai Mobis 指定的 Sony GMSL2 相机，询问兼容性所需资料。用户要求：先解决技术问题，再转销售报价。

## 答复要点

### 技术（可给内部 / 后续外发）

- 产品对应 **Mini J501 载板 + AGX Orin 64GB + GMSL 扩展**；解串器 **MAX96712**，**2x Mini-Fakra**，datasheet 最多 **8x GMSL2**，支持 POC。
- 预装 JetPack **6.2 / 6.2.1**，有带 GMSL 的 JP **7.2** 镜像；须用 Seeed BSP，非 NVIDIA DevKit 官方镜像。
- 官方验证相机：SG3S-ISX031C-GMSL2F、SG2-AR0233C-5200-G2A、SG2-IMX390C-5200-G2A、SG8S-AR0820C-5300-G2A（及 Orbbec overlay）。
- **Sony / Hyundai Mobis 指定相机不在验证列表** → 不能承诺兼容；需客户提供型号、sensor、serializer、连接器/pin、POC、分辨率帧率、目标 JP、是否有驱动/DT。
- Mini-Fakra 相机线、地区 AC 线通常需另购；韩国专用电源线公开 SKU **未见**。
- SKU `100085113` **完整装箱单（SSD 容量、是否含适配器/风扇散热器等）公开页未列全** → 转销售/产品确认后再写入 PI。

### 非技术（转销售）

单价与是否确认 $3899、学术折扣、库存交期、运至首尔运费与方式、Incoterms、税/关税、付款方式、报价有效期、保修条款、韩国电源线、可选分项报价。

## 知识库更新

- [x] `docs/faq/recomputer-mini-j501-gmsl-camera-compatibility.md`（active）
- [x] `docs/staging/recomputer-mini-j5012-sku-100085113-bom.md`（待确认装箱单）
- [x] 更新 `INDEX.md`
- [x] 补充 `docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md` 交叉链接

## 来源

- https://www.seeedstudio.com/reComputer-Mini-J5012-with-GMSL-Extension-p-6878.html
- https://wiki.seeedstudio.com/recomputer_j501_mini_getting_started/
- https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_mini_J501_datasheet.pdf
- https://www.seeedstudio.com/reComputer-Jetson-AGX-Orintm-Developer-Kit-GMSL-Bundle.html
- 本仓库既有 `docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md`

## PR

- draft（本分支）
