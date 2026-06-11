# Seeed 天猫/淘宝 Jetson 技术支持知识库索引

> 收录范围：仅 Jetson 相关资料。NVIDIA 官方开发套件、Seeed Jetson 盒子/载板/整机、通用 Jetson 软件问题需分别标注适用平台类型。
>
> **仓库结构**：指令层见 [`AGENTS.md`](AGENTS.md) 与 [`instructions/`](instructions/)；本文件及 `docs/` 为知识库层。

## 按 NVIDIA 官方套件索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T |
| --- | --- | --- | --- |
| [JetPack 7.2 / Jetson Linux r39.2 官方发布要点](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md) | Jetson Orin family | official_kit | 7.2 / 39.2 |
| [JetPack 6.2.1 / Jetson Linux r36.4.4 官方发布要点](docs/official_kit/common/jetpack-6-2-1-l4t-r36-4-4-release.md) | Jetson Orin modules and developer kits | official_kit | 6.2.1 / 36.4.4 |
| [Jetson Orin Nano Developer Kit：JetPack 7.2 ISO 安装方式](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md) | Jetson Orin Nano Developer Kit | official_kit | 7.2 / 39.2 |
| [Jetson AGX Orin Developer Kit：JetPack 7.2 BSP 更新路径](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md) | Jetson AGX Orin Developer Kit | official_kit | 7.2 / 39.2 |
| [JetPack 6 GPIO：输出不生效与 pinmux/BCT 关系](docs/official_kit/common/jetpack-6-gpio-pinmux.md) | Jetson Orin series GPIO | official_kit | 6.x / 36.x |

## 按 Seeed 设备索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T |
| --- | --- | --- | --- |
| [Seeed reComputer J401/J301 系列刷 JetPack](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) | reComputer J3010/J3011/J4011/J4012 | seeed_device | 5.1.x/6.x |
| [Seeed reComputer Super：JetPack 6.2 与硬件要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) | reComputer Super J3010/J3011/J4011/J4012 | seeed_device | 6.2 / 36.4.3 |
| [Seeed reComputer：JetPack 5.1.3 到 6.2 OTA 更新](docs/seeed_device/recomputer/recomputer-ota-jetpack-5-1-3-to-6-2.md) | reComputer mini J4012 and Orin-based reComputers | seeed_device | 5.1.3 -> 6.2 / 35.5.0 -> 36.4.3 |
| [Seeed Jetson Flash Center：图形化下载与刷机流程](docs/seeed_device/common/seeed-jetson-flash-center.md) | Supported Seeed Studio Jetson devices | seeed_device | varies |
| [Seeed Jetson AGX Orin 32GB H01 Kit：刷 JetPack 与外设驱动](docs/seeed_device/agx-orin-h01/agx-orin-32gb-h01-flash-jetpack.md) | Jetson AGX Orin 32GB H01 Kit | seeed_device | 5.0.2/5.1.1/5.1.4/6.0/6.1/6.2 |
| [Seeed reComputer Industrial：预装系统、刷机与工业接口](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md) | reComputer Industrial J201/J301/J401 | seeed_device | 5.1.3/6.x |
| [Seeed reServer Industrial：预装系统、刷机与硬件接口](docs/seeed_device/reserver/reserver-industrial-getting-started.md) | reServer Industrial J301/J401 | seeed_device | 5.1.1 / 35.3.1 |
| [reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md) | reServer Industrial J4012 | seeed_device | 6.x / 36.x |
| [reComputer Robotics J401：JetPack 6.2 与接口使用要点](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md) | reComputer Robotics J401 | seeed_device | 6.2 / 36.4.3 |

## 通用条目索引

| 内容 | 产品 | 适用平台类型 | JetPack / L4T |
| --- | --- | --- | --- |
| [BSP 已匹配后安装 JetPack SDK 组件](docs/common/install-jetpack-components-after-bsp.md) | Jetson software stack | common | 6.x/7.x |

## 按问题类型索引

### 刷机 / 系统安装 / JetPack / L4T

- [JetPack 7.2 / Jetson Linux r39.2 官方发布要点](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md) - `official_kit`
- [JetPack 6.2.1 / Jetson Linux r36.4.4 官方发布要点](docs/official_kit/common/jetpack-6-2-1-l4t-r36-4-4-release.md) - `official_kit`
- [Jetson Orin Nano Developer Kit：JetPack 7.2 ISO 安装方式](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md) - `official_kit`
- [Jetson AGX Orin Developer Kit：JetPack 7.2 BSP 更新路径](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md) - `official_kit`
- [Seeed reComputer J401/J301 系列刷 JetPack](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) - `seeed_device`
- [Seeed reComputer Super：JetPack 6.2 与硬件要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) - `seeed_device`
- [Seeed reComputer：JetPack 5.1.3 到 6.2 OTA 更新](docs/seeed_device/recomputer/recomputer-ota-jetpack-5-1-3-to-6-2.md) - `seeed_device`
- [Seeed Jetson Flash Center：图形化下载与刷机流程](docs/seeed_device/common/seeed-jetson-flash-center.md) - `seeed_device`
- [Seeed Jetson AGX Orin 32GB H01 Kit：刷 JetPack 与外设驱动](docs/seeed_device/agx-orin-h01/agx-orin-32gb-h01-flash-jetpack.md) - `seeed_device`
- [Seeed reComputer Industrial：预装系统、刷机与工业接口](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md) - `seeed_device`
- [Seeed reServer Industrial：预装系统、刷机与硬件接口](docs/seeed_device/reserver/reserver-industrial-getting-started.md) - `seeed_device`

### GPIO / BSP / 设备树 / 外设接口

- [JetPack 6 GPIO：输出不生效与 pinmux/BCT 关系](docs/official_kit/common/jetpack-6-gpio-pinmux.md) - `official_kit`
- [reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md) - `seeed_device`
- [reComputer Robotics J401：JetPack 6.2 与接口使用要点](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md) - `seeed_device`

### CUDA / TensorRT / SDK 组件

- [BSP 已匹配后安装 JetPack SDK 组件](docs/common/install-jetpack-components-after-bsp.md) - `common`
- [JetPack 6.2.1 / Jetson Linux r36.4.4 官方发布要点](docs/official_kit/common/jetpack-6-2-1-l4t-r36-4-4-release.md) - `official_kit`

### FAQ

- [JetPack 7.2 为什么找不到 Jetson Orin Nano Developer Kit 的 SD 卡镜像？](docs/faq/orin-nano-jetpack-7-2-no-sd-card-image.md) - `official_kit`
- [Seeed reComputer/reServer/Robotics 能不能直接刷 NVIDIA 官方开发套件镜像或 SDK Manager 流程？](docs/faq/seeed-device-use-nvidia-official-image.md) - `seeed_device`
- [JetPack 6 上为什么找不到 /sys/class/gpio，或者 Jetson.GPIO 输出不生效？](docs/faq/jetpack-6-gpio-sysfs-missing.md) - `common`
- [reServer Industrial J4012 升级 JetPack 6 后 PoE 网口不供电怎么办？](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md) - `seeed_device`
- [reComputer Robotics J401 配好 CAN bitrate 后仍不能通信，需要做什么？](docs/faq/recomputer-robotics-j401-can-wakeup.md) - `seeed_device`
- [Seeed Jetson 设备刷机时 USB timeout、NFS mount failure、tegrarcm_v2 找不到或首次启动卡在 OEM 配置怎么办？](docs/faq/seeed-jetson-flashing-usb-nfs-errors.md) - `seeed_device`

## 待人工复核

- [待复核：Seeed J401/J501 是否支持 JetPack 7.2](docs/unknown_review/seeed-j401-jetpack-7-2-support.md) - `unknown`
