# Seeed 天猫/淘宝 Jetson 技术支持知识库索引

> 收录范围：仅 Jetson 相关资料。NVIDIA 官方开发套件、Seeed Jetson 盒子/载板/整机、通用 Jetson 软件问题需分别标注适用平台类型。
>
> **仓库结构**：指令 [`AGENTS.md`](AGENTS.md)、[`instructions/`](instructions/)；记忆 [`memory/`](memory/)；知识库 [`docs/README.md`](docs/README.md) + 本文件。
>
> **客服优先引用 `status: active` 条目。** 收集区见 [`docs/inbox/`](docs/inbox/)、[`docs/community_questions/`](docs/community_questions/)。清洗审计见 [`KNOWLEDGE_AUDIT.md`](KNOWLEDGE_AUDIT.md)。

## 按 NVIDIA 官方套件索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T |
| --- | --- | --- | --- |
| [JetPack 6.2.2 / Jetson Linux r36.5 官方发布要点](docs/official_kit/common/jetpack-6-2-2-l4t-r36-5-release.md) | Jetson Orin family | official_kit | 6.2.2 / 36.5 |
| [JetPack 7.2 / Jetson Linux r39.2 官方发布要点](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md) | Jetson Orin family | official_kit | 7.2 / 39.2 |
| [Jetson Orin Nano Developer Kit：JetPack 7.2 ISO 安装方式](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md) | Jetson Orin Nano Developer Kit | official_kit | 7.2 / 39.2 |
| [Jetson AGX Orin Developer Kit：JetPack 7.2 BSP 更新路径](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md) | Jetson AGX Orin Developer Kit | official_kit | 7.2 / 39.2 |
| [JetPack 6 GPIO：输出不生效与 pinmux/BCT 关系](docs/official_kit/common/jetpack-6-gpio-pinmux.md) | Jetson Orin series GPIO | official_kit | 6.x / 36.x |

## 按 Seeed 设备索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T | 备注 |
| --- | --- | --- | --- | --- |
| [Seeed reComputer J401/J301 系列刷 JetPack](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) | reComputer **Classic** J3010/J3011/J4011/J4012 | seeed_device | 5.1.x/6.x | **不含 Super** |
| [Seeed reComputer Super：JetPack 6.2 与硬件要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) | reComputer **Super** J3010/J3011/J4011/J4012 | seeed_device | 6.2 / 36.4.3 | mfi `--flash-only` |
| [Seeed Linux_for_Tegra：JetPack 6.2 BSP 与升级边界](docs/seeed_device/recomputer/seeed-linux-for-tegra-jetpack-6-2-bsp.md) | Seeed Jetson reComputer/reServer BSP | seeed_device | 6.2 / 36.4.3 | 自编译参考 |
| [Seeed reComputer Industrial：预装系统、刷机与工业接口](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md) | reComputer Industrial J201/J301/J401 | seeed_device | 5.1.3/6.x | |
| [Seeed reServer Industrial：预装系统、刷机与硬件接口](docs/seeed_device/reserver/reserver-industrial-getting-started.md) | reServer Industrial J301/J401 | seeed_device | 5.1.1 / 35.3.1 | |
| [reComputer Robotics J401：JetPack 6.2 与接口使用要点](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md) | reComputer Robotics J401 | seeed_device | 6.2 / 36.4.3 | |
| [Seeed reComputer Robotics J501 / J501 Mini：JetPack 6.2.1 与接口要点](docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md) | reComputer Robotics J501 / J501 Mini | seeed_device | 6.2.1 / 36.4.4 | |

## 通用条目索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T |
| --- | --- | --- | --- |
| [BSP 已匹配后安装 JetPack SDK 组件](docs/common/install-jetpack-components-after-bsp.md) | Jetson software stack | common | 6.x/7.x |

## 按问题类型索引（已确认 `active`）

### 刷机 / 系统安装

- [Seeed reComputer **Super** 刷机要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) - `seeed_device`
- [Super 刷机板级名 `recomputer-orin-super-j401`](docs/faq/recomputer-super-j4012-flash-board-name.md) - `seeed_device`
- [Seeed reComputer **Classic** J401 刷机](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) - `seeed_device`
- [Seeed 设备能否刷 NVIDIA 官方镜像？](docs/faq/seeed-device-use-nvidia-official-image.md) - `seeed_device`
- [淘宝标题「官方核心模组 开发套件」辨析](docs/faq/taobao-title-official-module-vs-nvidia-devkit.md) - `seeed_device`
- [JetPack 7.2 无 Orin Nano DevKit SD 卡镜像](docs/faq/orin-nano-jetpack-7-2-no-sd-card-image.md) - `official_kit`

### 系统维护 / apt

- [自己装浏览器与 apt upgrade 的区别](docs/faq/seeed-jetson-install-browser-vs-apt-upgrade.md) - `seeed_device`

### GPIO / 接口 / 外设

- [JetPack 6 GPIO pinmux](docs/official_kit/common/jetpack-6-gpio-pinmux.md) - `official_kit`
- [JetPack 6 sysfs GPIO 缺失](docs/faq/jetpack-6-gpio-sysfs-missing.md) - `common`
- [Robotics J401 CAN 唤醒](docs/faq/recomputer-robotics-j401-can-wakeup.md) - `seeed_device`
- [Super J401 GMSL / Arducam](docs/faq/recomputer-super-j401-gmsl-arducam-imx219.md) - `seeed_device`

### 资料 / 规格

- [AGX Orin 64GB DevKit 规格书](docs/faq/agx-orin-64gb-developer-kit-datasheet.md) - `official_kit`

## 待人工复核（`need_review` — 客服勿当最终结论）

| 内容 | 路径 | 来源 |
| --- | --- | --- |
| apt upgrade 与 Seeed BSP 冲突 | [faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md](docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md) | [GitHub issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41) |
| reServer J4012 PoE 不供电 | [faq/reserver-industrial-j4012-poe-jetpack-6.md](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md) | [Forum](https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727) |
| reServer J4012 PoE/GPIO 排查记录 | [seeed_device/.../reserver-industrial-j4012-jetpack-6-gpio-poe.md](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md) | 同上 |
| Seeed J401/J501 是否支持 JetPack 7.2 | [unknown_review/seeed-j401-jetpack-7-2-support.md](docs/unknown_review/seeed-j401-jetpack-7-2-support.md) | [Forum](https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471) |

## 收集草稿（`docs/inbox/` — 待晋升）

当前无条目。见 [inbox/README.md](docs/inbox/README.md)。

## 社区开放问题（`docs/community_questions/`）

当前无条目。见 [community_questions/README.md](docs/community_questions/README.md)。
