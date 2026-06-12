# Seeed Jetson 技术支持知识库索引（库 1）

> **本仓库仅技术支持闭环。** 三库架构见 [`ARCHITECTURE.md`](ARCHITECTURE.md)。
>
> 客服 **只优先引用 `status: active`**。`docs/staging/` 为待你确认的结案草稿。

## 已确认（`active`）

### Seeed 设备

| 内容 | 产品 | JetPack | 来源 |
| --- | --- | --- | --- |
| [Classic J401 刷机](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) | Classic J301/J401 | 5.1.x/6.x | [Wiki](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/) |
| [Super 刷机要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) | Super J301/J401 | 6.2 | [Wiki](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/) |
| [Linux_for_Tegra BSP](docs/seeed_device/recomputer/seeed-linux-for-tegra-jetpack-6-2-bsp.md) | Seeed BSP | 6.2 | [GitHub](https://github.com/Seeed-Studio/Linux_for_Tegra) |
| [Industrial](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md) | Industrial | 5.1.3/6.x | Wiki |
| [reServer Industrial](docs/seeed_device/reserver/reserver-industrial-getting-started.md) | reServer | 5.1.1 | Wiki |
| [Robotics J401 接口](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md) | Robotics J401 | 6.2 | Wiki |
| [Robotics J501](docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md) | J501 | 6.2.1 | Wiki |

### FAQ（已确认）

| 内容 | 标签 |
| --- | --- |
| [Super 刷机板级名](docs/faq/recomputer-super-j4012-flash-board-name.md) | 刷机 |
| [装浏览器 vs apt upgrade](docs/faq/seeed-jetson-install-browser-vs-apt-upgrade.md) | apt |
| [淘宝标题辨析](docs/faq/taobao-title-official-module-vs-nvidia-devkit.md) | 电商 |
| [Seeed 能否刷 NVIDIA 官方镜像](docs/faq/seeed-device-use-nvidia-official-image.md) | 刷机 |
| [Super GMSL / Arducam](docs/faq/recomputer-super-j401-gmsl-arducam-imx219.md) | 摄像头 |
| [Robotics CAN 唤醒](docs/faq/recomputer-robotics-j401-can-wakeup.md) | CAN |
| [GPIO sysfs 缺失](docs/faq/jetpack-6-gpio-sysfs-missing.md) | GPIO |
| [AGX Orin 64GB 规格书](docs/faq/agx-orin-64gb-developer-kit-datasheet.md) | 资料 |

### 官方 DevKit / 通用

| 内容 | 标签 |
| --- | --- |
| [JP 6.2.2 发布](docs/official_kit/common/jetpack-6-2-2-l4t-r36-5-release.md) | 官方 |
| [JP 7.2 发布](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md) | 官方 |
| [Orin Nano JP7.2 ISO](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md) | 官方 |
| [AGX Orin JP7.2 更新](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md) | 官方 |
| [GPIO pinmux](docs/official_kit/common/jetpack-6-gpio-pinmux.md) | GPIO |
| [Orin Nano 无 SD 镜像](docs/faq/orin-nano-jetpack-7-2-no-sd-card-image.md) | 官方 |
| [BSP 后装 SDK 组件](docs/common/install-jetpack-components-after-bsp.md) | 通用 |

## 待确认（`docs/staging/` — 勿当最终答案）

| 内容 | 来源 |
| --- | --- |
| [Seeed J401/J501 是否支持 JP7.2](docs/staging/seeed-j401-jetpack-7-2-support.md) | [Forum](https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471) |

## 待复核（历史 `need_review` in faq/ — 宜迁入 staging 或晋升）

| 内容 | 来源 |
| --- | --- |
| [apt upgrade 冲突](docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md) | [issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41) |
| [reServer PoE](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md) | [Forum](https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727) |
| [reServer PoE/GPIO 记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md) | 同上 |

## 结案日志

见 [`cases/`](cases/)。

## 其他仓库

- 收集与反馈：`seeed-jetson-collect`（待建）— 骨架 [`templates/collect-repo/`](templates/collect-repo/)
- 资讯日报：`seeed-jetson-news`（待建）— 骨架 [`templates/news-repo/`](templates/news-repo/)
