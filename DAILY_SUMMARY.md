# DAILY_SUMMARY - 2026-06-11

## 今日新增内容

### FAQ / 摄像头 / GMSL

- `seeed_device` [reComputer Super J401 默认镜像是否带 GMSL？Arducam GMSL IMX219 是否可用？](docs/faq/recomputer-super-j401-gmsl-arducam-imx219.md)
  - 收录 Zoho 客户案例（Beewise，SKU 100090211）：Super J401 JetPack 6.2 无 Seeed GMSL BSP；Arducam GMSL 为第三方联调；Robotics J401 为 Seeed GMSL 官方路径。

### FAQ / 资料 / 官方套件

- `official_kit` [Jetson AGX Orin 64GB 官方开发套件有没有规格书？](docs/faq/agx-orin-64gb-developer-kit-datasheet.md)
  - 收录天猫/淘宝咨询：NVIDIA 官方 Developer Kit 规格资料在官网与 Jetson Download Center；附可复制中文简答与官方链接。

---

# DAILY_SUMMARY - 2026-06-10

## 今日新增内容

### NVIDIA 官方套件 / 模组

- `official_kit` [JetPack 7.2 / Jetson Linux r39.2 官方发布要点](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md)
  - 收录 JetPack 7.2、L4T 39.2、Ubuntu 24.04、kernel 6.8、CUDA 13.2.1、TensorRT 10.16.2、统一 ISO 安装方式、AGX Orin 32GB MAXN_SUPER。
- `official_kit` [Jetson Orin Nano Developer Kit：JetPack 7.2 ISO 安装方式](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md)
  - 记录 JetPack 7.2 不再提供 SD Card image，需使用 USB ISO 安装到 microSD/NVMe，并要求 JetPack 6.x generation UEFI/QSPI firmware。
- `official_kit` [Jetson AGX Orin Developer Kit：JetPack 7.2 BSP 更新路径](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md)
  - 记录 AGX Orin Developer Kit 使用 Jetson ISO 更新到 L4T r39.2 的前提与路径。
- `official_kit` [JetPack 6 GPIO：输出不生效与 pinmux/BCT 关系](docs/official_kit/common/jetpack-6-gpio-pinmux.md)
  - 收录 JetPack 6 upstream GPIO driver、pinmux/BCT、libgpiod 与 Jetson.GPIO 注意事项。

### Seeed Jetson 盒子 / 载板 / 整机

- `seeed_device` [Seeed reComputer J401/J301 系列刷 JetPack](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md)
  - 收录 J401/J301 预装 JetPack 5.1.3、Seeed 刷机包、Force Recovery、Hynix DRAM/JetPack 5.1.3 注意事项。
- `seeed_device` [Seeed reComputer Super：JetPack 6.2 与硬件要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md)
  - 收录 reComputer Super JetPack 6.2、接口、供电、SHA256 校验与 Seeed initrd flash。
- `seeed_device` [Seeed reComputer Industrial：预装系统、刷机与工业接口](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md)
  - 收录 Industrial 系列预装 JetPack 5.1.3、PoE、DI/DO、RS485、CAN、TPM、刷机边界。
- `seeed_device` [Seeed reServer Industrial：预装系统、刷机与硬件接口](docs/seeed_device/reserver/reserver-industrial-getting-started.md)
  - 收录 reServer Industrial JetPack 5.1.1、5x GbE/4x PoE、SATA、COM、DI/DO、CAN 与刷机要求。
- `seeed_device` [reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md)
  - 收录 Seeed 论坛 JetPack 6 下 PoE/GPIO libgpiod 示例，标记为 need_review。
- `seeed_device` [reComputer Robotics J401：JetPack 6.2 与接口使用要点](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md)
  - 收录 Robotics J401 CAN、UART、I2C、GMSL、风扇、USB 与 JetPack 6.2 镜像要点。

### 通用与 FAQ

- `common` [BSP 已匹配后安装 JetPack SDK 组件](docs/common/install-jetpack-components-after-bsp.md)
  - 区分 BSP 与 SDK 组件，说明 `sudo apt install nvidia-jetpack` 只适合 BSP 已匹配后的组件安装。
- 新增 5 条 FAQ：
  - [Orin Nano JetPack 7.2 无 SD 卡镜像](docs/faq/orin-nano-jetpack-7-2-no-sd-card-image.md)
  - [Seeed 设备是否可直接刷 NVIDIA 官方镜像](docs/faq/seeed-device-use-nvidia-official-image.md)
  - [JetPack 6 GPIO sysfs 缺失](docs/faq/jetpack-6-gpio-sysfs-missing.md)
  - [reServer Industrial J4012 JetPack 6 PoE](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md)
  - [Robotics J401 CAN transceiver 唤醒](docs/faq/recomputer-robotics-j401-can-wakeup.md)

## 今日更新内容

- 新增根目录 [INDEX.md](INDEX.md)，按 NVIDIA 官方套件、Seeed 设备、问题类型、FAQ、待复核内容建立索引。

## 需要人工复核内容

- `unknown` [待复核：Seeed J401/J501 是否支持 JetPack 7.2](docs/unknown_review/seeed-j401-jetpack-7-2-support.md)
  - NVIDIA 已发布 JetPack 7.2，但当前未确认 Seeed J401/J501 官方 JetPack 7.2 镜像/BSP。
- `seeed_device` [reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md)
  - 来源为 Seeed 论坛答复，建议结合最新 Wiki/BSP 复核后再作为正式售后脚本。
- `seeed_device` [reServer Industrial J4012 升级 JetPack 6 后 PoE 网口不供电怎么办？](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md)
  - FAQ 状态为 need_review。

## 已标记过时内容

- 今日未发现已有旧内容；无条目标记为 outdated。
