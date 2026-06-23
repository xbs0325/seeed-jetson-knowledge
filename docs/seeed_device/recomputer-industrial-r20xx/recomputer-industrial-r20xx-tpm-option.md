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
  - https://www.digikey.cn/zh/products/detail/seeed-technology-co-ltd/114993114/20842454
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
| 如何订购？ | 单独购买 **TPM 2.0 Module with Infineon SLB9670**（SKU **114993114**）。R2045-12 商详页未将 TPM 列为配置项；可通过代理商订购，例如 [DigiKey（114993114）](https://www.digikey.cn/zh/products/detail/seeed-technology-co-ltd/114993114/20842454)。 |
| 安装方式 | 打开机箱后插入 J26 插座；也可联系工业产品团队咨询出厂预装/定制。 |

## 配件信息

- **产品名**：TPM 2.0 Module with Infineon SLB9670
- **SKU**：114993114
- **芯片**：Infineon OPTIGA SLB9670，TCG TPM 2.0
- **接口**：SPI，接载板 **J26**
- **订购链接（代理商示例）**：[DigiKey — Seeed 114993114](https://www.digikey.cn/zh/products/detail/seeed-technology-co-ltd/114993114/20842454)

Wiki 配件表示例（R20xx）：

| Item | Product Name | SKU |
| --- | --- | --- |
| Encryption Chip TPM 2.0 | TPM 2.0 Module with infineon SLB9670 | 114993114 |

## 商详页可配置项（R2045-12）

当前 [R2045-12 商详](https://www.seeedstudio.com/reComputer-Industrial-R2045-12-p-6544.html) 可见配置：

- AI Accelerator（Hailo-8 / None）
- Memory（8GB+32GB / 16GB+32GB）

「Also Add」推荐配件含 LoRa、NVMe SSD 等，**不含 TPM**。客户若在 Seeed 网店找不到 TPM 选项，属预期表现；可说明载板已预留接口，引导单独购买 SKU **114993114**（代理商如 DigiKey 有售）。

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
2. 载板**已预留 TPM 接口**（J26 SPI），可后装官方 TPM 模块。
3. 配件 SKU **114993114**；Seeed 网店未作配置项时，可提供代理商链接，例如 [DigiKey](https://www.digikey.cn/zh/products/detail/seeed-technology-co-ltd/114993114/20842454)。
4. 安装说明见 [R20xx Wiki](https://wiki.seeedstudio.com/recomputer_industrial_r20xx_getting_start/)；出厂预装/批量订单转销售跟进。
