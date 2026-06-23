---
product: reComputer Industrial R20xx (R2045-12 / R2045-10 / R2040 series)
vendor: seeed
platform: seeed_device
tags:
  - recomputer-industrial-r20xx
  - tpm
  - r2045-12
  - accessories
date: 2026-06-23
source_url: https://wiki.seeedstudio.com/recomputer_industrial_r20xx_getting_start/
source_links:
  - https://wiki.seeedstudio.com/recomputer_industrial_r20xx_getting_start/
  - https://www.seeedstudio.com/reComputer-Industrial-R2045-12-p-6544.html
status: active
---

# reComputer Industrial R20xx（含 R2045-12）：TPM 选配说明

## 适用范围

- reComputer Industrial **R20xx** 系列（Raspberry Pi CM5 平台），含 **R2045-12**（SKU **100080766**）。
- 与 Jetson 版 reComputer Industrial（J201/J301/J401）为不同产品线；TPM 配件 SKU 相同，但安装接口位置以对应 Wiki 为准。

## 结论摘要

| 问题 | 结论 |
| --- | --- |
| 标准 SKU 是否含 TPM？ | **不含**。规格表中 TPM 2.0 标有 `*`，说明需另购配件。 |
| 是否支持 TPM？ | **支持**。载板预留 SPI TPM 接口（R20xx 为 **J26**）。 |
| 如何订购？ | 单独购买 **TPM 2.0 Module with Infineon SLB9670**（SKU **114993114**）；R2045-12 商详页当前**未**将 TPM 列为可勾选配置项。 |
| 安装方式 | 打开机箱后插入 J26 插座；也可联系工业产品团队咨询出厂预装/定制。 |

## 配件信息

- **产品名**：TPM 2.0 Module with Infineon SLB9670
- **SKU**：114993114
- **芯片**：Infineon OPTIGA SLB9670，TCG TPM 2.0
- **接口**：SPI，接载板 **J26**

Wiki 配件表示例（R20xx）：

| Item | Product Name | SKU |
| --- | --- | --- |
| Encryption Chip TPM 2.0 | TPM 2.0 Module with infineon SLB9670 | 114993114 |

## 商详页可配置项（R2045-12）

当前 [R2045-12 商详](https://www.seeedstudio.com/reComputer-Industrial-R2045-12-p-6544.html) 可见配置：

- AI Accelerator（Hailo-8 / None）
- Memory（8GB+32GB / 16GB+32GB）

「Also Add」推荐配件含 LoRa、NVMe SSD 等，**不含 TPM**。客户若在商店找不到 TPM 选项，属预期表现，应引导按 SKU **114993114** 单独下单或联系销售/工业定制。

## 安装与验证

1. 参考 R20xx Wiki「Encryption Chip TPM 2.0」章节，将模块插入 **J26**。
2. 上电后验证：

```bash
ls /dev | grep tpm
```

若输出含 `tpm0`（及常见 `tpmrm0`），表示系统已识别 TPM。

## 定制与出厂安装

R20xx Wiki 注明可提供 logo、包装、固件烧录等定制；扩展模块清单与工业定制可联系 **industrial@seeed.cc**。若客户需要出厂预装 TPM，可由销售/订单团队与工业产品线确认是否支持及报价。

## 客服答复要点

1. **100080766 标准发货不含 TPM。**
2. TPM 为官方支持的**可选安全模块**，非网页下拉配置项时，请单独订购 SKU **114993114**。
3. 提供 Wiki 链接供客户查阅接口与配件表。
4. 需要预装或批量订单时，转销售/工业定制渠道跟进（价格、交期、库存不在技术支持范围）。
