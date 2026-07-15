---
product: Mini AI Computer T506S
vendor: seeed
platform: seeed_device
jetpack: "4.6 / 4.6.1 (T506S BSP available); no JP5 BSP"
l4t: "32.6.x / 32.7.x class for JP4.6.1"
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
  - https://www.twowinit.com/jetsonxaviernx11/441.html
  - https://www.twowinit.com/web/userfiles/articlefile/systemos/Readme_T506S.pdf
  - https://www.twowinit.com/web/userfiles/articlefile/userguide/T506S-E4-BD-BF-E7-94-A8-E8-AF-B4-E6-98-8E-E6-89-8B-E5-86-8C.pdf
  - https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf
  - https://developer.nvidia.com/embedded/jetpack-archive
  - https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4
  - https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html
  - https://pan.baidu.com/s/17XiGh-tOFTh8RjGj4uUUjw?pwd=fgr7
status: need_review
review_target: docs/seeed_device/mini-ai-computer
review_reason: "OEM 官网公开有系统镜像 Readme（含 JP4.x/JP5.1.1 百度链）与中文手册 Recovery 步骤；Seeed 现网对客仍以 JP4.6.1 OneDrive 为主；Wi-Fi 走返厂；JP5.1.1 是否可对外承诺待确认"
next_action: "核对 OneDrive 是否含包内刷机脚本（非仅注意事项）；若可对外复用将刷机节迁 faq；JP5.1.1 是否支持需产品线确认"
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

### 原 Xavier NX 配置的 JetPack / BSP（内部确认）

| 层级 | 版本 |
| --- | --- |
| T506S 可提供 BSP（Seeed 现网） | **JetPack 4.6.1**（海外优先 **OneDrive**；百度备用：https://pan.baidu.com/s/17XiGh-tOFTh8RjGj4uUUjw?pwd=fgr7 ） |
| OEM（图为）公开镜像列表 | Readme 列出 JP4.4 / 4.5 / 4.5.1 / 4.6 / **4.6.1** / **5.1.1**（百度）；硬件后缀 **V1.3 / V2.3**，见设备二维码标签 |
| JetPack 5.x（对客承诺） | **待确认**：OEM 公开有 `T506S_JP5.1.1_V2.3`；Seeed 此前对客只发 JP4.6.1，**勿自行承诺 JP5** |
| Orin 模组升级 | **不支持** |

### BSP / 刷机说明

- 代售定制载板（约 2022 上架）：Seeed 现网优先发 **JP4.6.1** 完整包（需含刷机脚本，不止「注意事项」）。
- 海外客户常无法使用百度网盘，应改发 OneDrive / 直链。
- 不要用 NVIDIA DevKit / J202 包冒充 T506S 升级方案。
- **不要**用社区 SDK Manager「国产套件」通用教程冒充 T506S 定制镜像流程（会覆盖 OEM 设备树/驱动，PoE 等接口易坏）。

#### OEM 刷机文档入口（2026-07-15 实测可打开）

| 文档 | URL |
| --- | --- |
| 图为 T506S 资源页 | https://www.twowinit.com/jetsonxaviernx11/441.html |
| 系统镜像 / 版本说明 `Readme_T506S.pdf` | https://www.twowinit.com/web/userfiles/articlefile/systemos/Readme_T506S.pdf |
| 中文使用说明（含 Recover 按键） | https://www.twowinit.com/web/userfiles/articlefile/userguide/T506S-E4-BD-BF-E7-94-A8-E8-AF-B4-E6-98-8E-E6-89-8B-E5-86-8C.pdf |
| 英文 User Guide（Recover 同款） | https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf |

#### Recover 模式（手册原文要点）

1. 主机：x86 Ubuntu（OEM Readme 建议优先物理机；JP4.6.1 常用 18.04）。
2. 用 **Micro-USB（USB-OTG，刷机口）** 连主机；主机侧建议 USB 3.0 口、数据线需能传数据。
3. 进入 Recover：先按住 **REC** → 再按住 **RES/RST** → 约 2 秒后先松 **RES/RST** → 再松 **REC**。
4. 主机执行 `lsusb`，出现 **NVIDIA Corp** / APX 即成功。
5. 解压对应硬件版本镜像包后，按包内脚本执行。内部从包内确认的示例命令（**脚本名含硬件版本，V1.3 是否正确需看设备标签 / 包内实际脚本名**）：

```bash
cd JetPack_4.6_Linux_JETSON_XAVIER_NX_TARGETS
./nx.t506s.v1.3.flash.sh
```

若硬件为 V2.3，包内可能是 `nx.t506s.v2.3.flash.sh`（或同类命名）；进入目录后先 `ls *.flash.sh` / `ls nx.t506s*` 核对再跑。

### 全接口在「最新软件」下是否仍支持

客户列的接口（Ethernet、PoE、USB、NVMe、CAN、RS-232、RS-485、GPIO、HDMI、Wi-Fi、Bluetooth）依赖定制载板驱动与设备树。

- 在仅有出厂 JP4.6、且无 T506S 官方 JP5.x 验证报告前：  
  **不能承诺**「刷到 NVIDIA 最新 JetPack 后上述接口全部仍可用」。
- 即使未来提供定制 JP5.x 镜像，也必须以该镜像的发布说明为准，逐接口验证。

### Wi-Fi / Bluetooth

- 商详：Wi-Fi 为 surface mounted / optional，**modules not included**。
- M.2 E 在商详语境更偏 5G；Wi-Fi 与 DevKit 常见「自插 M.2 Key E 卡」不同。
- 官方标注底板图（商详/分销图）上，Wi-Fi 位可见丝印旁贴装模组；屏蔽罩品牌字样可读为 **Cdtech（中龙通）**，双 IPEX/U.FL，邮票孔贴装。
- 识图候选（内部）：**CDW-63822CU-01**（RTL8822CU / USB）；对比 **CDW-47822CS**（RTL8822CS / SDIO）。`CU`/`CS` 不可互换。
- **对外口径（2026-07-15 内部确认）**：OEM/图为无法提供可公开的精确料号；相关选配资料视为已遗失。**不要**再建议客户自行购买焊接。可转售后评估**寄回加装**是否可行。

### 旁支：Xavier 载板是否仍在售

见 [`docs/faq/seeed-xavier-nx-carrier-boards-availability.md`](../faq/seeed-xavier-nx-carrier-boards-availability.md)：J202 等商详仍在；库存问销售。与「本机能否插 Orin」分开答。

## 推断

- T506S 电气/电源/PoE 交换设计面向 Xavier，直接插 Orin 有 pinmux/供电风险，且无官方 validate。
- 客户要 Orin 算力时，正确产品建议是换购 Orin 整机/载板，而不是升级 T506S 模组。
- BSP 与 Wi-Fi SKU 大概率需内部走 OEM/产品线，公开渠道不够外发完整安装包。

## 建议

1. 明确告知：**T506S 载板不支持对外承诺的 Orin NX/Orin Nano 模组升级。**
2. JetPack：对客优先给 **JP4.6.1** 完整包 + Recover 步骤 + OEM 手册/Readme 链接；**勿主动承诺 JP5.1.1**，除非内部确认可支持且硬件为对应 V1.3/V2.3。
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
