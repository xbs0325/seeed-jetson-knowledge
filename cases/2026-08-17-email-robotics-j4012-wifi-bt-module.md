---
date: 2026-08-17
channel: zoho
reply_to: customer
product: reComputer Robotics J4012 with GMSL Extension (SKU 100026552)
issue_type: accessory
resolved: yes
confidence: confirmed
final_customer_reply: true
---

## 问题摘要

英文客户 Peter Chow（Cyber Robotics Technology Ltd.，info@robotics.com.hk）已购 **reComputer Robotics J4012 with GMSL Extension**（NVIDIA Jetson Orin NX Super 16GB），询问应购买哪款 **Wi-Fi + Bluetooth** 模组才能装到该设备上。邮件下方为订单 #4000559723 的运输保险通知，与选型无关。

## 答复要点

- **已确认**：该机 M.2 Key E 用于 Wi-Fi/BT，模组不标配；M.2 Key B 用于 5G；GMSL 扩展板不占用 Key E。
- **已确认**：官方配件为 **RTL8822CE Wireless NIC Kits，SKU E24121001**（1× 模组 + 2× 天线）。模组单品 114993556，天线单品 114993587（需 2 根）。
- **依据**：Robotics Wiki 规格表、Robotics 用户手册 7.6 / 第 9 章配件表、Robotics 选配商详 Wireless Module Kit。
- **需转交**：加购、库存、价格、是否并入原订单 → 销售 / 店铺。
- **外发英文**：已按用户要求起草（见下方）。

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

## 外发英文

Hi Peter,

Thank you for reaching out. On reComputer Robotics J4012 with GMSL Extension, Wi-Fi and Bluetooth are added through the onboard **M.2 Key E** slot. This slot is empty by default, and the GMSL extension board does not use it.

Please purchase our **RTL8822CE Wireless NIC Kits (SKU E24121001)**. The kit includes the M.2 2230 Wi-Fi 5 + Bluetooth 5.0 module and two antennas:

https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html

Install the module in **M.2 Key E**. M.2 Key B is for a 5G module. After installation, you can connect Wi-Fi and Bluetooth from the desktop settings. Installation notes are here:

https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/

If you would like help placing the order, please let us know and we can loop in our sales team.

Best regards,

## 外发中文对照

Peter 您好，

感谢来信。reComputer Robotics J4012 with GMSL Extension 通过机内 **M.2 Key E** 加装 Wi-Fi 和蓝牙。该槽位出厂为空，GMSL 扩展板不占用此槽。

请购买我们的 **RTL8822CE Wireless NIC Kits（SKU E24121001）**。套件含 M.2 2230 Wi-Fi 5 + Bluetooth 5.0 模组及两根天线：

https://www.seeedstudio.com/RTL8822CE-Wireless-NIC-Kits-for-Nvidia-Jetson-Orin.html

请将模组安装到 **M.2 Key E**。M.2 Key B 用于 5G 模组。安装后可在桌面设置中连接 Wi-Fi 和蓝牙。安装说明：

https://wiki.seeedstudio.com/rtl8822ce_wireless_module_for_jetson/

如需协助下单，请告知我们，我们会转交销售团队跟进。

此致

## PR

- cursor/robotics-j401-wifi-bt-module-f680
