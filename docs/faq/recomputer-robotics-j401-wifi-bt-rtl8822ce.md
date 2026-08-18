---
product: reComputer Robotics J401 / J4012 with GMSL Extension
vendor: seeed
platform: seeed_device
jetpack: "6.2"
tags:
  - faq
  - recomputer-robotics
  - wifi
  - bluetooth
  - accessory
  - m.2
  - gmsl
sku: "100026552"
date: 2026-08-18
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/
  - https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html
  - https://www.seeedstudio.com/reComputer-Robotics-J401-Carrier-Board-optional-accessories.html
  - https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html
status: active
---

# reComputer Robotics J401：Wi-Fi / Bluetooth 配件

## 问题

reComputer Robotics J4012 with GMSL Extension 要加 Wi-Fi 和 Bluetooth，应买哪款模组？GMSL 扩展板会不会占用无线槽位？

## 适用产品

- reComputer Robotics J401 Carrier Board
- reComputer Robotics J4012 / J4011 / J3011 等 Robotics 整机（含 with GMSL Extension，SKU 如 **100026552**）
- 适用平台类型：`seeed_device`

## 简洁答案

Wi-Fi / Bluetooth 走载板 **M.2 Key E**。该槽位默认空置，需另购官方 **RTL8822CE Wireless NIC Kits（SKU E24121001）**，装入 Key E 并接天线。GMSL 扩展板走 **Camera Expansion Header**，不占用 Key E。**M.2 Key B** 用于 5G 模组，不要把 Wi-Fi 卡插到 Key B。

## 事实

- Robotics J401 Wiki 规格：`1x M.2 Key E for WiFi/Bluetooth module`；`1x M.2 Key B for 5G module`；GMSL2 为可选扩展板，连接 **Camera Expansion Header**。
- Robotics 配件页将 **RTL8822CE Wireless NIC** 列为官方 Wireless Module Kit。
- RTL8822CE 套件 SKU **E24121001**：M.2 2230、Wi-Fi 5（802.11a/b/g/n/ac）+ Bluetooth 5.0，含模组与两根天线。
- 安装：断电后插入 **M.2 Key E**，接 MHF4 天线；系统桌面 `Settings → Wi-Fi` / `Settings → Bluetooth` 连接。安装说明见 RTL8822CE Wiki。

## 注意事项

- RTL8822CE Wiki 的「Supported Devices」示例写的是 Classic **reComputer J4012/J4011/J3011/J3010**；Robotics J401 以载板 Wiki 的 Key E 说明 + 配件页官方选配为准，推荐同一套件。
- 不要承诺库存、价格、交期。
- 客户若还要蜂窝网，应另走 Key B 的 5G 方案，与 Wi-Fi 套件不是同一配件。

## 客服可复制英文简答（示例）

On reComputer Robotics J4012 with GMSL Extension, Wi-Fi and Bluetooth use the onboard M.2 Key E slot. This slot is empty by default, and the GMSL extension board does not use it. Please purchase our RTL8822CE Wireless NIC Kits (SKU E24121001), install the module in M.2 Key E, and connect Wi-Fi/Bluetooth from the desktop settings. M.2 Key B is for a 5G module.

## 相关链接

- [reComputer Robotics J401 Interfaces Usage](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/)
- [RTL8822CE Wireless Module for Jetson](https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/)
- [RTL8822CE Wireless NIC Kits（SKU E24121001）](https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html)
- [reComputer Robotics J4012 with GMSL Extension（SKU 100026552）](https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html)
- [reComputer Robotics & optional accessories](https://www.seeedstudio.com/reComputer-Robotics-J401-Carrier-Board-optional-accessories.html)
- [Robotics J401 接口要点（本仓库）](../seeed_device/recomputer-robotics/robotics-j401-interfaces.md)
