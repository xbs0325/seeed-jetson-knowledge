---
product: reComputer Robotics J4012 / Robotics J401 Carrier Board
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - faq
  - recomputer-robotics
  - wifi
  - bluetooth
  - accessory
  - m.2-key-e
date: 2026-08-17
source_links:
  - https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/
  - https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html
  - https://www.seeedstudio.com/reComputer-Robotics-J401-Carrier-Board-optional-accessories.html
  - https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html
  - https://www.seeedstudio.com/RTL8822CE-WIFI-Module-p-6313.html
  - https://www.seeedstudio.com/2-4G-5G-External-Antenna-with-RP-SMA-Male-Connector-and-1-13-Coaxial-Cable-130mm-Set-p-6316.html
  - https://www.manualslib.com/manual/4028534/Seeed-Studio-Recomputer-Robotics-Series.html
status: active
---

# reComputer Robotics J401：Wi-Fi / Bluetooth 模块选型

## 适用范围

- reComputer Robotics J401 Carrier Board
- reComputer Robotics J4012（Orin NX Super 16GB），含 **with GMSL Extension** 整机（商详 SKU **100026552**）
- 同系列 Robotics J301x / J401x 整机（同一块 Robotics J401 载板、同一 M.2 Key E）
- 适用平台类型：`seeed_device`

**不适用**：reComputer Classic J401、reComputer Super J401、reComputer Industrial、reServer。这些产品线虽也有 M.2 Key E，但官方配件表与机壳天线走线不同，不要直接套用本条目的 Robotics 配件清单。

## 事实

- Robotics J401 **不标配** Wi-Fi / Bluetooth 模组。Wiki 规格表写明：**1x M.2 Key E for WiFi/Bluetooth module**；机壳有 **5x Antenna Hole**。
- **M.2 Key B** 是给 **5G** 模组用的，不是 Wi-Fi/BT 槽。
- 带 GMSL 扩展板的整机（如 Robotics J4012 with GMSL Extension）不改变 M.2 Key E 用途；GMSL 走 Camera Expansion Header。
- Robotics 用户手册第 7.6 节写明：把无线模组接到 **M.2 Key E**，并接 RF 线与天线；举例为 **RTL8822CE Wireless NIC Kits** 或 AW-CB375NF Wireless NIC kits。
- Robotics 用户手册第 9 章配件表（M.2 Key E Slot）列出可购配件：**RTL8822CE Wireless NIC Kits**，SKU **E24121001**。
- Seeed 商详 **reComputer Robotics & optional accessories** 的 Wireless Module Kit 同样列出：
  - **RTL8822CE Wireless NIC**（Wi-Fi 5 + Bluetooth 5.0，M.2 2230 A/E key）
  - **2.4G/5G External Antenna**（RP-SMA Male，1.13 同轴 130mm）
- 对应商详 SKU：
  | 配件 | SKU | 说明 |
  | --- | --- | --- |
  | RTL8822CE Wireless NIC Kits | **E24121001** | 1× 模组 + 2× 天线，优先推荐 |
  | RTL8822CE 模组单品 | **114993556** | 不含天线 |
  | 2.4G/5G 外置天线 | **114993587** | 模组为 2T2R，需 **2 根** |

## 推断

- 客户只说「加 Wi-Fi 和 BT」时，官方路径就是 **M.2 Key E + RTL8822CE 套件**，不必再买 Key B 的 5G 模组。
- Intel AX210 / AC8265 等第三方 Key E 卡在其他 Seeed J401 产品线上有使用记录，但 **不是** Robotics J401 配件表中的官方选型；不能对外说「已验证可装到 Robotics J4012」。

## 建议

1. 优先推荐客户购买 **RTL8822CE Wireless NIC Kits（E24121001）**，一次配齐模组与两根天线。
2. 安装：断电 → 插入 **M.2 Key E** → 拧载板附带的 Key E 螺丝 → IPEX/MHF4 接天线 → 天线从机壳 Antenna Hole 引出。
3. 预装 JetPack 6.2 时，按 RTL8822CE Wiki：桌面 **Settings → Wi-Fi / Bluetooth**，或命令行 `iw` / `nmcli` / `bluetoothctl`。
4. 价格、库存、是否可加到原订单（如 #4000559723）转销售 / 店铺客服，技术侧只给型号。

## 禁止

- 不要说 Robotics J4012「没有无线接口」或「必须用 USB 网卡」。
- 不要让客户把 Wi-Fi 卡插到 **M.2 Key B** 或 **M.2 Key M**。
- 不要把 Super / Industrial 的 mini-PCIe LTE、EC25 方案当成 Robotics 的 Wi-Fi 方案。
- 不要承诺 Intel AX210、Infineon、未列入配件表的第三方模组「官方兼容」。
- 不要承诺库存、价格、交期。

## 客服可复制回复

**内部结论**：买 **RTL8822CE Wireless NIC Kits（SKU E24121001）**，装到 Robotics J401 的 **M.2 Key E**。

## 相关链接

- [Getting Started with reComputer Robotics](https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/)
- [Robotics J401 Interfaces Usage](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/)
- [RTL8822CE Wireless Module for Jetson](https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/)
- [Robotics J4012 with GMSL Extension 商详](https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html)
- [Robotics 选配配件页](https://www.seeedstudio.com/reComputer-Robotics-J401-Carrier-Board-optional-accessories.html)
- [RTL8822CE Wireless NIC Kits](https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html)
