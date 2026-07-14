---
date: 2026-07-14
channel: zoho
product: Mini AI Computer T506S (SKU 114110167, Jetson Xavier NX 8GB)
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户拥有 Mini AI Computer T506S（Xavier NX 8GB），询问：

1. 载板是否可升级到 Orin NX / Orin Nano（同 260-pin）
2. 原 Xavier NX 配置最新支持的 JetPack，以及 BSP / flash 镜像 / 设备树 / 安装说明
3. 最新软件下 Ethernet、PoE、USB、NVMe、CAN、RS-232、RS-485、GPIO、HDMI、Wi-Fi、BT 是否仍可用
4. 未配 Wi-Fi，希望加装：兼容模块型号与在最新 JetPack 下的限制

用户侧关注点：**Seeed 是否还有支持 Jetson Xavier 系列的载板在售。**

## 答复要点

- **不要**建议把 Orin NX/Nano 直接插到 T506S 载板：NVIDIA 官方为 form-factor compatible、**非 pin-compatible**；Seeed/TWOWIN 公开资料仅写 Xavier NX，无 Orin 升级证明。
- T506S 商详预装 **JetPack 4.6**；NVIDIA 端 Xavier 最新为 **JetPack 5.1.6 / L4T 35.6.4**，但 **JetPack 6/7 不支持 Xavier**。T506S 为定制载板，**不能**承诺可直接刷 NVIDIA 官方 DevKit JP5.1.6 并保留全部工业接口。
- Seeed Wiki **未见** T506S 独立刷机页 / BSP 下载（对比同系列 T906 有 Wiki）。OEM 手册（TWOWIN TW-T506S）明确警告勿随意 `apt upgrade` 覆盖内核/设备树。
- Wi-Fi 为可选表面贴装位 + 天线口，商详写 modules not included；**公开资料未给出可售后自装的具体模组 SKU**，需销售/产品线确认。
- Xavier 载板/整机商详仍可见在售：J202 载板、Industrial J2012、J2021、T506S 等；A203 停产。**库存以销售后台为准**（属非技术项）。

## 知识库更新

- [x] `docs/staging/mini-ai-computer-t506s-orin-upgrade-bsp-wifi.md`（待确认）
- [x] `docs/faq/seeed-xavier-nx-carrier-boards-availability.md`（active，强调库存需销售确认）
- [x] 更新 `INDEX.md`

## 来源

- https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
- https://www.pi-shop.ch/mini-ai-computer-t506s
- https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf
- https://developer.nvidia.com/embedded/jetpack-archive
- https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4
- https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html
- https://www.seeedstudio.com/reComputer-Industrial-J2012-p-5685.html
- https://www.seeedstudio.com/reComputer-J2021-p-5438.html
- https://wiki.seeedstudio.com/reComputer_J2021_J202_Flash_Jetpack/

## PR

- cursor/t506s-xavier-carrier-support-923a
