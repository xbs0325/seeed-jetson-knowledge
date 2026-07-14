---
product: Mini AI Computer T506S
vendor: seeed
platform: seeed_device
jetpack: "4.6 (shipped) / 5.1.x (NVIDIA Xavier ceiling, T506S BSP TBD)"
l4t: "32.6.x shipped; 35.6.x NVIDIA Xavier latest"
tags:
  - t506s
  - xavier-nx
  - orin-upgrade
  - bsp
  - wifi
  - carrier-board
date: 2026-07-14
source_links:
  - https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
  - https://www.pi-shop.ch/mini-ai-computer-t506s
  - https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf
  - https://wiki.seeedstudio.com/Mini_AI_Computer_T906/
  - https://developer.nvidia.com/embedded/jetpack-archive
  - https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4
status: need_review
review_target: docs/seeed_device/mini-ai-computer
review_reason: "T506S 缺少 Seeed 官方 Wiki/BSP 页面；Wi-Fi 具体可采购 SKU、是否可升级到 JP5.1.x 且保留全接口，需产品线或 OEM 确认"
next_action: "确认后迁入 seeed_device 或 faq，并补充 BSP 下载链接与 Wi-Fi SKU"
---

# Mini AI Computer T506S：模组升级、JetPack/BSP、接口与 Wi-Fi（待确认）

## 适用范围

- Seeed Mini AI Computer **T506S**，SKU **114110167**，搭载 Jetson Xavier NX 8GB。
- 相关 OEM 文档常写作 TWOWIN **TW-T506S**（硬件描述与 Seeed 商详高度一致，作参考）。
- **不适用**：reComputer Classic/Super/Industrial J401、reServer、T906（AGX Orin）及其他 Orin 载板的直接结论套用。

## 事实

### 产品与接口（公开商详 / 分销页）

- 边缘 AI 整机，Jetson Xavier NX 8GB，商详标注预装 **JetPack 4.6**。
- 接口摘要：5x PoE GbE（4x PSE + 1x PD）、4x USB 3.0、Micro-USB device、HDMI、RS-232、RS-485、CAN、4x GPIO、I2C、M.2 Key M（预装 128GB SSD）、TF、mini PCIe（4G）、M.2 E（商详写 5G）、Wi-Fi/蓝牙为可选（modules not included）。
- Wi-Fi 描述为 **surface mounted**（表面贴装位）+ 天线口，与 DevKit 常见「客户自插 M.2 Key E Wi-Fi 卡」形态不同；M.2 E 在商详语境下更偏 5G。

### Orin 模组兼容性（NVIDIA）

- NVIDIA 官方说明：Orin NX / Orin Nano 与 Xavier NX **form-factor compatible（同 260-pin SODIMM）**，但 **not pin-compatible**。
- 可为「公共 I/O」专门设计双模组载板；**不能**据此认定任意 Xavier 载板可安全直接换装 Orin。
- Seeed T506S / TWOWIN TW-T506S 公开规格**仅写 Xavier NX**，**未**声明支持 Orin NX / Orin Nano。

### JetPack 版本边界（NVIDIA）

- Xavier 系列仍包含在 **JetPack 5.1.6 / L4T 35.6.4** 支持列表。
- **JetPack 6.x / 7.x 不支持** Jetson Xavier NX（仅 Orin / Thor 等）。
- T506S 出厂宣传为 JP4.6；从 JP4.6 升到 JP5.1.x **依赖定制载板 BSP**，不能默认等于 NVIDIA Xavier NX DevKit 流程。

### BSP / 刷机资料公开情况

- Seeed Wiki 有 **T906** 独立页面与刷机说明；检索时**未找到** T506S 对等 Wiki / SourceForge BSP 入口。
- Seeed Jetson DevelopTool / Linux_for_Tegra 公开支持列表以 reComputer / reServer Orin 系列为主，**未列出 T506S**。
- TWOWIN TW-T506S User Guide 写明：接口驱动为厂商定制，与 NVIDIA 开发板不同；**直接 `apt upgrade` 会升级内核并覆盖设备树**。手册给出先备份 `nvidia-l4t-apt-source.list` 再升级的警告流程。
- 恢复模式：按住 REC，再按住 RST，约 2 秒后先松 RST 再松 REC；主机 `lsusb` 应看到 NVIDIA Corp。

### Wi-Fi / Bluetooth

- 标准件不含 Wi-Fi 模组；可选安装后可用图形界面或 `nmcli` 连接。
- 公开商详 / 用户手册**未列出**具体兼容芯片 SKU（如 Intel 8265 等）或 Seeed 可售配件编号。
- 在未获产品线确认前，**不能**把通用 Jetson M.2 Key E Wi-Fi 攻略当作 T506S 售后加装方案。

## 推断

- T506S 载板大概率**不能**作为 Orin NX/Nano 的即插即用升级底座；换模组存在电气 / pinmux / 供电风险。
- 即便 NVIDIA 侧 Xavier 可到 JP5.1.6，T506S 若要用新版软件，仍需 OEM/Seeed 提供对应镜像与设备树；否则 Ethernet 交换芯片、PoE、串口、CAN、GPIO 可能失效。
- Wi-Fi 更可能是厂内焊接/定制可选件，而非用户可随意购买的标准 M.2 卡；售后加装通常要转销售/产品线核实。

## 建议

1. 对外：**明确不建议**在 T506S 上更换 Orin NX/Orin Nano。
2. JetPack：说明出厂 JP4.6；NVIDIA Xavier 天花板 JP5.1.6；T506S 专用 BSP 需内部向产品线/OEM 索取，**暂勿对外承诺可提供完整镜像包**。
3. 接口连续性：在无 T506S 官方 JP5.x 镜像前，**不能**承诺「刷最新 JetPack 后全部工业接口仍工作」。
4. Wi-Fi：转销售确认是否仍有可选模组、天线套件、是否需返厂安装；询问客户当前 JetPack 版本与是否可接受返厂。
5. 若客户目标是 Orin 算力 + 多 PoE，引导评估 **reServer Industrial / reComputer Industrial** 等 Orin 产品线，而不是 T506S 换芯。

## 禁止

- 禁止回答「260-pin 所以 Orin 可以直接插」。
- 禁止把 NVIDIA DevKit 或 J202 的刷机包直接发给 T506S 客户当官方方案。
- 禁止承诺「刷到 JP5.1.6 后 PoE/CAN/RS485 全部正常」。
- 禁止仅凭通用 Jetson 经验指定某一 Wi-Fi 卡型号给客户购买安装。
- 库存、报价、是否还能下单 → 转销售，不硬答成技术结论。

## 客服可复制回复（内部稿，待 Wi-Fi/BSP 确认后可外发）

内部判断：不支持 Orin 直换；JP 以出厂 4.6 与定制 BSP 为准；Wi-Fi SKU 与 JP5 BSP 仍待产品线确认。Xavier 载板商详仍有 J202 等在售入口，库存问销售。

## 相关链接

- [T506S 商详](https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html)
- [TWOWIN TW-T506S User Guide](https://twowintech.com/wp-content/uploads/2025/07/TW-T506S-User-Guide.pdf)
- [NVIDIA JetPack Archive](https://developer.nvidia.com/embedded/jetpack-archive)
- [NVIDIA Orin vs Xavier carrier FAQ 讨论](https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4)
