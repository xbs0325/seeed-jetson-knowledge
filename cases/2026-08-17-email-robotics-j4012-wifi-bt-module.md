---
date: 2026-08-17
channel: zoho
reply_to: user_internal
product: reComputer Robotics J4012 with GMSL Extension (SKU 100026552)
issue_type: accessory
resolved: yes
confidence: confirmed
final_customer_reply: false
---

## 问题摘要

英文客户 Peter Chow（Cyber Robotics Technology Ltd.，info@robotics.com.hk）已购 **reComputer Robotics J4012 with GMSL Extension**（NVIDIA Jetson Orin NX Super 16GB），询问应购买哪款 **Wi-Fi + Bluetooth** 模组才能装到该设备上。邮件下方为订单 #4000559723 的运输保险通知，与选型无关。

## 答复要点

- **已确认**：该机 M.2 Key E 用于 Wi-Fi/BT，模组不标配；M.2 Key B 用于 5G；GMSL 扩展板不占用 Key E。
- **已确认**：官方配件为 **RTL8822CE Wireless NIC Kits，SKU E24121001**（1× 模组 + 2× 天线）。模组单品 114993556，天线单品 114993587（需 2 根）。
- **依据**：Robotics Wiki 规格表、Robotics 用户手册 7.6 / 第 9 章配件表、Robotics 选配商详 Wireless Module Kit。
- **需转交**：加购、库存、价格、是否并入原订单 → 销售 / 店铺。
- **外发英文**：待用户确认后再写。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/faq/recomputer-robotics-j401-wifi-bt-module.md`（active）
- [x] `docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md`（补充 Key E 配件指向）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
- https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
- https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/
- https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html
- https://www.seeedstudio.com/reComputer-Robotics-J401-Carrier-Board-optional-accessories.html
- https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html
- https://www.manualslib.com/manual/4028534/Seeed-Studio-Recomputer-Robotics-Series.html

## PR

- cursor/robotics-j401-wifi-bt-module-f680
