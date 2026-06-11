# DAILY_SUMMARY - 2026-06-11

## 今日新增内容

### NVIDIA 官方套件 / 模组

- `official_kit` [JetPack 6.2.1 / Jetson Linux r36.4.4 官方发布要点](docs/official_kit/common/jetpack-6-2-1-l4t-r36-4-4-release.md)
  - 收录 NVIDIA JetPack 6.2.1 / L4T 36.4.4 维护版本、Docker v28.0.x 兼容性修复、SDK Manager 刷机修复、HSM boot image signing、Argus 与 GStreamer 更新。
  - 明确该条目仅适用于 NVIDIA 官方 Orin 模组/开发套件；Seeed 设备需另核对 Seeed BSP/镜像。

### Seeed Jetson 盒子 / 载板 / 整机

- `seeed_device` [Seeed reComputer：JetPack 5.1.3 到 6.2 OTA 更新](docs/seeed_device/recomputer/recomputer-ota-jetpack-5-1-3-to-6-2.md)
  - 收录 reComputer mini J4012 JP5.1.3 -> JP6.2 OTA payload、SHA256、设备端 OTA 步骤、版本验证命令，以及 Orin NX reComputer mini 不要启用 MAXN SUPER 的散热警告。
- `seeed_device` [Seeed Jetson Flash Center：图形化下载与刷机流程](docs/seeed_device/common/seeed-jetson-flash-center.md)
  - 收录 Seeed Flash Center 下载、SHA256 校验、解压 BSP、Recovery mode 检测和 Start Flash 流程；强调只适用于工具支持列表中的 Seeed Jetson 设备。
- `seeed_device` [Seeed Jetson AGX Orin 32GB H01 Kit：刷 JetPack 与外设驱动](docs/seeed_device/agx-orin-h01/agx-orin-32gb-h01-flash-jetpack.md)
  - 收录 H01 Kit 预装 JetPack 5.1.4、默认账号、JP5/JP6 外设驱动、Recovery USB ID、eMMC 刷机示例和 JP5.1.1 PCN overlay 异常处理。

### 通用与 FAQ

- 新增 1 条 FAQ：
  - `seeed_device` [Seeed Jetson 设备刷机时 USB timeout、NFS mount failure、tegrarcm_v2 找不到或首次启动卡在 OEM 配置怎么办？](docs/faq/seeed-jetson-flashing-usb-nfs-errors.md)

## 今日更新内容

- 更新根目录 [INDEX.md](INDEX.md)，把今日新增资料按 NVIDIA 官方套件、Seeed 设备、问题类型和 FAQ 加入索引。
- 更新 `unknown` [待复核：Seeed J401/J501 是否支持 JetPack 7.2](docs/unknown_review/seeed-j401-jetpack-7-2-support.md)，补充 2026-06-11 论坛复查记录，状态保持 need_review。

## 需要人工复核内容

- `unknown` [待复核：Seeed J401/J501 是否支持 JetPack 7.2](docs/unknown_review/seeed-j401-jetpack-7-2-support.md)
  - 今日复查 Seeed 论坛原帖后仍未确认 Seeed J401/J501 官方 JetPack 7.2 镜像/BSP；保持 need_review。
- `seeed_device` [reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录](docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md)
  - 来源为 Seeed 论坛答复，仍建议结合最新 Wiki/BSP 复核后再作为正式售后脚本。
- `seeed_device` [reServer Industrial J4012 升级 JetPack 6 后 PoE 网口不供电怎么办？](docs/faq/reserver-industrial-j4012-poe-jetpack-6.md)
  - FAQ 状态为 need_review。

## 已标记过时内容

- 今日未发现已有旧内容；无条目标记为 outdated。
