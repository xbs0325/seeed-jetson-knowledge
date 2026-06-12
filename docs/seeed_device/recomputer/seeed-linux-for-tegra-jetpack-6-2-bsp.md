---
product: Seeed Jetson reComputer / reServer Linux_for_Tegra BSP
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - bsp
  - linux-for-tegra
  - device-tree
  - ota
  - flashing
date: 2026-06-12
source_url: https://raw.githubusercontent.com/Seeed-Studio/Linux_for_Tegra/r36.4.3/readme.md
status: active
---

# Seeed Linux_for_Tegra：JetPack 6.2 BSP 与升级边界

## 适用范围

- Seeed Jetson reComputer、reComputer Industrial、reServer Industrial 等使用 Seeed Linux_for_Tegra BSP 的设备。
- 适用平台类型：`seeed_device`。
- 不适用于 NVIDIA 官方开发套件的标准刷机流程说明；官方开发套件应按 NVIDIA 文档处理。

## 资料来源与定位

Seeed `Linux_for_Tegra` 仓库说明：该软件是 Seeed Jetson reComputer、reServer 等产品默认出货固件的源代码，基于 NVIDIA JetPack 6.2 构建，并在此基础上增加了 Seeed 硬件驱动和板级配置，方便用户构建 Seeed Jetson 系统或衍生系统。

## 已列出的支持硬件

仓库 r36.4.3 README 列出的 Seeed Orin 设备包括：

- reComputer Industrial J4011/J4012/J3011/J3010。
- reServer Industrial J4011/J4012/J3011/J3010。
- reComputer J4011/J4012/J3011/J3010。

README 也提示产品命名中的 reComputer、Industrial、reServer 对应不同产品形态，需按具体型号选择文档和配置。

## Seeed 增加的板级内容

- 在 NVIDIA 原始 Linux_for_Tegra 基础上增加 Seeed `extra_scripts`、内核/驱动构建脚本和板级配置。
- README 列出的主要配置文件包括：
  - `recomputer-industrial-orin-j201.conf`
  - `recomputer-orin-j401.conf`
  - `reserver-agx-orin-j501x.conf`
  - `reserver-agx-orin-j501x-gmsl.conf`
  - `reserver-industrial-orin-j401.conf`
- 示例刷机命令使用 Seeed 配置名，例如 `recomputer-orin-j401`，并通过 initrd flash 写入 NVMe。

## OTA 与升级注意事项

- README 提供了生成 OTA payload 的流程：准备 BASE_BSP 与 TARGET_BSP，在 `Linux_for_Tegra/tools/ota_tools/` 下执行 `start_generate_ota_pkg.sh`，按提示输入目标板名和升级前 BSP 版本。
- README 说明 JetPack 5.1.3 及以后的版本可直接 OTA 到当前版本；更早版本需先 OTA 到 5.1.3 后再升级。
- OTA 完成后系统会替换为 TARGET_BSP 中的系统；如需保留文件，应使用 `nv_ota_preserve_data.sh` 与 `ota_backup_files_list.txt`。

## 售后提示

Seeed Linux_for_Tegra 是 Seeed 设备的 BSP/设备树/驱动来源之一。客户遇到刷机、OTA、GPIO/CAN/网口/CSI/GMSL/风扇等板级问题时，应先核对正在使用的 Seeed 配置、镜像版本和对应 Wiki，而不是直接按 NVIDIA 官方开发套件配置名或 SDK Manager 流程处理。

## 相关链接

- [Seeed Linux_for_Tegra GitHub](https://github.com/Seeed-Studio/Linux_for_Tegra)
- [r36.4.3 README raw](https://raw.githubusercontent.com/Seeed-Studio/Linux_for_Tegra/r36.4.3/readme.md)
- [Seeed reComputer J401/J301 Flash JetPack](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)
