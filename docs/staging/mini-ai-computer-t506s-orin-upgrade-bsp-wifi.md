---
product: Mini AI Computer T506S
vendor: seeed
platform: seeed_device
jetpack: "4.6 (shipped) / 5.1.x (NVIDIA Xavier ceiling; T506S BSP TBD)"
l4t: "32.6.x shipped; 35.6.x NVIDIA Xavier latest"
tags:
  - t506s
  - xavier-nx
  - orin-upgrade
  - module-upgrade
  - bsp
  - wifi
date: 2026-07-14
source_links:
  - https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
  - https://www.pi-shop.ch/mini-ai-computer-t506s
  - https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf
  - https://developer.nvidia.com/embedded/jetpack-archive
  - https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4
  - https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html
status: need_review
review_target: docs/seeed_device/mini-ai-computer
review_reason: "T506S 缺公开 Wiki/BSP；Wi-Fi 售后 SKU 与是否存在任何 Orin 兼容验证需产品线确认"
next_action: "产品线确认：①本机可否 Orin；②可提供的 JP/BSP；③Wi-Fi 模组 SKU"
---

# Mini AI Computer T506S：本机升模组、JetPack/BSP、接口与 Wi-Fi（待确认）

## 适用范围

- Seeed Mini AI Computer **T506S**（SKU **114110167**，Jetson Xavier NX 8GB）。
- 客户主问：这块载板能否换成 Orin NX / Orin Nano；原 Xavier 的最新 JetPack 与资料；最新软件下接口；加装 Wi-Fi/BT。
- **不适用**：把本 case 当成「拆 Xavier 去插别的 Seeed 载板」为主叙事（那是旁支库存问题）。

## 事实

### 客户意图（按英文原句）

- `upgrade options for its carrier board` + `Does this carrier board support any newer 260-pin … Orin NX or Orin Nano`  
  → 主意图是：**同一块 T506S 载板上，模组能否升级到 Orin 一代**。

### Orin NX / Orin Nano 能否上 T506S

- NVIDIA：Orin NX/Nano 与 Xavier NX **form-factor compatible（同 260-pin）**，但 **not pin-compatible**。
- Seeed 商详 / OEM（TW-T506S）规格 **仅 Xavier NX**，无 Orin 支持声明。
- 对外结论：**不建议、不承诺** 在 T506S 上更换 Orin NX 或 Orin Nano。若要 Orin，应选购 Orin 载板/整机（如 reComputer / reServer Industrial 等）。

### 原 Xavier NX 配置的 JetPack

| 层级 | 版本 |
| --- | --- |
| T506S 出厂宣传 | **JetPack 4.6** |
| NVIDIA Xavier 官方最新 | **JetPack 5.1.6 / L4T 35.6.4** |
| JetPack 6.x / 7.x | **不支持** Xavier NX |

### BSP / 刷机镜像 / 设备树 / 安装说明

- Seeed Wiki 有 T906 刷机页；检索时 **未见 T506S 对等 Wiki / 官方镜像下载入口**。
- 公开 Seeed Linux_for_Tegra / DevelopTool 列表以 Orin 类 reComputer/reServer 为主，**未列 T506S**。
- OEM 手册：接口驱动为定制；恢复模式为 REC+RST；警告勿随意 `apt upgrade` 覆盖内核/设备树。
- 现状：**不能**把 NVIDIA Xavier DevKit 或 J202 的 BSP 当成 T506S 官方升级包外发。

### 全接口在「最新软件」下是否仍支持

客户列的接口（Ethernet、PoE、USB、NVMe、CAN、RS-232、RS-485、GPIO、HDMI、Wi-Fi、Bluetooth）依赖定制载板驱动与设备树。

- 在仅有出厂 JP4.6、且无 T506S 官方 JP5.x 验证报告前：  
  **不能承诺**「刷到 NVIDIA 最新 JetPack 后上述接口全部仍可用」。
- 即使未来提供定制 JP5.x 镜像，也必须以该镜像的发布说明为准，逐接口验证。

### Wi-Fi / Bluetooth

- 商详：Wi-Fi 为 surface mounted / optional，**modules not included**。
- M.2 E 在商详语境更偏 5G；Wi-Fi 与 DevKit 常见「自插 M.2 Key E 卡」不同。
- 官方标注底板图（商详/分销图）上，Wi-Fi 位可见丝印旁贴装模组；屏蔽罩品牌字样可读为 **Cdtech（中龙通）**，双 IPEX/U.FL，邮票孔贴装。完整料号第二行在公开图分辨率下 **未能可靠辨认**。
- 形态吻合的常见同厂候选：**CDW-47822CS** 系列（RTL8822CS，Wi‑Fi 5 2T2R + BT，SDIO/UART 邮票孔）。**未经 BOM/产品线确认前，不得当作最终可焊料号外发。**
- 正确路径：销售/产品确认 T506S 可选 Wi‑Fi 官方料号与是否支持返厂加装；禁止引导客户自行对不符封装的模块进行焊接。

### 旁支：Xavier 载板是否仍在售

见 [`docs/faq/seeed-xavier-nx-carrier-boards-availability.md`](../faq/seeed-xavier-nx-carrier-boards-availability.md)：J202 等商详仍在；库存问销售。与「本机能否插 Orin」分开答。

## 推断

- T506S 电气/电源/PoE 交换设计面向 Xavier，直接插 Orin 有 pinmux/供电风险，且无官方 validate。
- 客户要 Orin 算力时，正确产品建议是换购 Orin 整机/载板，而不是升级 T506S 模组。
- BSP 与 Wi-Fi SKU 大概率需内部走 OEM/产品线，公开渠道不够外发完整安装包。

## 建议

1. 明确告知：**T506S 载板不支持对外承诺的 Orin NX/Orin Nano 模组升级。**
2. JetPack：说明出厂 4.6；Xavier 官方上限 5.1.6；T506S 若要升版软件须等/索取定制 BSP，暂不承诺可立即提供。
3. 接口：在无验证镜像前，不对「最新软件下全接口仍支持」做保证。
4. Wi-Fi：内部问销售有无可选模组与是否返厂安装。
5. 若客户坚持要 Orin：引导 reComputer / reServer Industrial 等 Orin 产品线，并说明接口需重新选型匹配。

## 禁止

- 「260-pin 一样所以 Orin 可以直接插」。
- 用 NVIDIA DevKit / J202 刷机包冒充 T506S 官方方案。
- 承诺 JP5.1.6 后 PoE/CAN/串口等全部正常。
- 指定未经验证的 Wi-Fi 卡型号让客户自行拆机安装。

## 相关链接

- [T506S 商详](https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html)
- [TWOWIN TW-T506S User Guide](https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf)
- [NVIDIA JetPack Archive](https://developer.nvidia.com/embedded/jetpack-archive)
- [Xavier 载板在售 FAQ](../faq/seeed-xavier-nx-carrier-boards-availability.md)
