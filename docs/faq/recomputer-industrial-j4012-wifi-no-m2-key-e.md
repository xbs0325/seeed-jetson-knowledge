---
product: reComputer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "5.1.3 / 6.x / 7.2"
tags:
  - recomputer-industrial
  - wifi
  - bluetooth
  - m2-key-e
  - accessory
  - smd
date: 2026-08-14
source_links:
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
  - https://www.seeedstudio.com/reComputer-Industrial-J4012-p-5684.html
  - https://www.seeed.cc/product/recomputer-industrial-fanless-edge-ai-device-with-jetson-module
  - https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/
  - https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
status: active
---

# reComputer Industrial J4012：不能直接插 RTL8822CE M.2 Key-E Wi-Fi

## 适用范围

- reComputer Industrial J4012（Orin NX 16GB，SKU **110110191**；客户邮件偶见笔误写成 1101110191）
- 同载板 Industrial 系列（J4011 / J301x / J201x）规格表述一致：Wi-Fi 为 SMD 选配，无 M.2 Key E
- 客户常见问题：是否可用 RTL8822CE 等 **M.2 Key-E** Wi-Fi 模组

## 事实

| 项目 | Industrial J4012（官方规格） |
| --- | --- |
| M.2 Key E（Wi-Fi/BT） | **无**；规格表未列出 Key E |
| Wi-Fi | **Support SMD Wi-Fi/Bluetooth (Module optional)** |
| 扩展口 | Mini PCIe（4G/LoRaWAN）、M.2 Key B（4G/5G）、M.2 Key M（NVMe SSD） |
| 标配 Wi-Fi | **否**；出厂不含 Wi-Fi/Bluetooth |

### SMD Wi-Fi 含义（Hardware Wiki / Reference Guide）

1. PCB 上预留 **焊接位**（USB to Wi-Fi/Bluetooth，U50），不是用户可插拔的 M.2 Key-E 槽。
2. 官方预留/验证模组为 **BL-M8723DU1**（芯片 **RTL8723DU**），经 USB 接口，另接天线座（J24/J25，IPEX）。
3. Wiki 明确：不建议客户自行焊接；自行损坏可能导致保修失效。建议通过 Seeed 专业服务焊接，联系 **order@seeed.cc**。
4. 商详/系列页亦写明：SMD Wi-Fi/Bluetooth 为 **Customized production**，需联系 order@seeed.cc。

### 与 Classic reComputer J4012 / RTL8822CE 的区别

| 产品 | Wi-Fi 接口 | RTL8822CE M.2 Key-E |
| --- | --- | --- |
| reComputer **Industrial** J4012 | SMD 焊接选配（RTL8723DU 路径） | **不支持直接安装**（无 Key-E 口） |
| reComputer **Classic** J4012（J401 载板） | **1× M.2 Key E** | Wiki 示例可用 RTL8822CE |

RTL8822CE Wiki（`rtl8822ce_wireless_module_for_jetson`）以 **Classic reComputer J4012** 为例，**不适用于** Industrial 载板。

## 客服口径

### 中文（内部/销售可转述）

Industrial J4012 载板**没有** M.2 Key-E，因此 **不能** 像 Classic J401 那样直接插入 RTL8822CE。规格里的「Support SMD Wi-Fi/Bluetooth」指 PCB 预留焊接位（官方示例 BL-M8723DU1 / RTL8723DU），需定制/专业焊接，请联系 order@seeed.cc。Mini PCIe / M.2 Key B 面向 4G/5G，不是 Key-E Wi-Fi 槽。

### 英文要点（待用户确认后再写完整外发邮件）

- No M.2 Key-E on Industrial J4012; RTL8822CE cannot be plugged in.
- Official Wi-Fi path: optional **SMD** module (factory/custom solder; BL-M8723DU1), contact order@seeed.cc.
- Do not self-solder if warranty matters; Wiki recommends Seeed professional service.
- Classic J4012 has Key-E; do not mix product lines.

## 禁止

- 不要说 Industrial「支持 RTL8822CE / M.2 Key-E」。
- 不要把 Classic J401 / Super / Robotics 的 Key-E 说明套用到 Industrial。
- 不要承诺 USB Wi-Fi 网卡或第三方模组的官方兼容性（公开资料未验证）。
- 不要自行承诺定制交期、价格、能否加焊到已发货订单 → 转销售 / order@seeed.cc。

## 来源

- [Industrial Getting Started — Specs](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/)
- [Industrial J40/J30 Hardware — WiFi and Bluetooth](https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/)
- [Industrial J4012 商详 SKU 110110191](https://www.seeedstudio.com/reComputer-Industrial-J4012-p-5684.html)
- [Industrial 系列页 — Customized SMD Wi-Fi](https://www.seeed.cc/product/recomputer-industrial-fanless-edge-ai-device-with-jetson-module)
- [RTL8822CE Wiki（Classic J4012 示例）](https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/)
- [Classic J401 Flash — 含 M.2 Key E](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
