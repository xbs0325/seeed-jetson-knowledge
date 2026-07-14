---
date: 2026-07-14
channel: zoho
product: Mini AI Computer T506S (SKU 114110167, Jetson Xavier NX 8GB)
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户拥有 Mini AI Computer T506S（Xavier NX 8GB），核心意图是：

**现有 T506S 载板能否升级到更新的 260-pin 模组（Orin NX / Orin Nano）**，并配套问 JetPack、BSP/镜像/设备树、全接口是否仍可用、可加装 Wi-Fi/BT 型号。

内部另有关注：Seeed 是否还有支持 Xavier 系列的载板在售（旁支，非客户主问）。

> 备注：中间曾误判成「换载板」；按英文原句应以 **本机升模组** 为主答。

## 答复要点

1. **Orin 直插 T506S：不支持对外承诺**  
   NVIDIA 为外形兼容、非 pin 兼容；Seeed/OEM 公开规格仅 Xavier NX。

2. **原 Xavier 配置 JetPack / BSP**  
   可提供支持到 **JetPack 4.6.1** 的包：  
   https://pan.baidu.com/s/17XiGh-tOFTh8RjGj4uUUjw?pwd=fgr7 （pwd: `fgr7`）  
   **无 JetPack 5 BSP** 可提供。

3. **Orin 模组升级**  
   不支持。

4. **全接口 +「最新软件」**  
   无定制镜像验证前，**禁止承诺** Ethernet/PoE/USB/NVMe/CAN/RS232/RS485/GPIO/HDMI/Wi-Fi/BT 在最新软件下全部仍可用。

5. **Wi-Fi**  
   可选表面贴装，标准件不含；公开 **无** 售后自装精确 SKU → 销售/产品线确认。

6. **Xavier 载板是否还在售（内部旁支）**  
   商详仍见 J202 / J2021 / Industrial J2012 / T506S；A203 停产。库存问销售。

## 知识库更新

- [x] staging：主叙事改回「本机升模组」
- [x] FAQ：Xavier 载板在售（旁支）
- [x] INDEX / case 同步

## 来源

- https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
- https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf
- https://developer.nvidia.com/embedded/jetpack-archive
- https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4
- https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html

## PR

- cursor/t506s-xavier-carrier-support-923a
