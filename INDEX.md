# 技术支持知识库索引

客服与 Agent 优先引用 **`status: active`** 条目。`docs/staging/` 为待确认草稿，勿作最终答案。

各子目录含义见 [`docs/README.md`](docs/README.md)。

## 已确认（active）

### 常见问题（faq）

| 条目 | 来源 |
|------|------|
| [淘宝标题辨析](docs/faq/taobao-title-official-module-vs-nvidia-devkit.md) | [Wiki](https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/) |
| [Super 刷机板级名](docs/faq/recomputer-super-j4012-flash-board-name.md) | [BSP Wiki](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/) |
| [装浏览器 vs apt upgrade](docs/faq/seeed-jetson-install-browser-vs-apt-upgrade.md) | [issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41) |
| [Seeed 能否刷 NVIDIA 官方镜像](docs/faq/seeed-device-use-nvidia-official-image.md) | Wiki |
| [Super GMSL / Arducam](docs/faq/recomputer-super-j401-gmsl-arducam-imx219.md) | Wiki |
| [Robotics CAN 唤醒](docs/faq/recomputer-robotics-j401-can-wakeup.md) | Wiki |
| [Classic J401 HDMI 无信号](docs/faq/recomputer-j401-hdmi-no-signal.md) | [Wiki](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/) |
| [GPIO sysfs 缺失](docs/faq/jetpack-6-gpio-sysfs-missing.md) | [GitHub](https://github.com/NVIDIA/jetson-gpio/issues/114) |
| [AGX Orin 64GB 规格书](docs/faq/agx-orin-64gb-developer-kit-datasheet.md) | NVIDIA |
| [Orin Nano 无 SD 镜像 (JP7.2)](docs/faq/orin-nano-jetpack-7-2-no-sd-card-image.md) | NVIDIA |
| [J4012 PREEMPT_RT 内核 (R36.4.3)](docs/faq/j4012-preempt-rt-kernel-seeed-bsp-r3643.md) | Wiki + NVIDIA + GitHub |

### Seeed 设备（seeed_device）

| 条目 | 备注 |
|------|------|
| [Classic J401 刷机](docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md) | 不含 Super |
| [Super 刷机要点](docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md) | mfi `--flash-only` |
| [Linux_for_Tegra BSP](docs/seeed_device/recomputer/seeed-linux-for-tegra-jetpack-6-2-bsp.md) | |
| [Industrial](docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md) | Jetson J201/J301/J401 |
| [Industrial R20xx TPM 选配](docs/seeed_device/recomputer-industrial-r20xx/recomputer-industrial-r20xx-tpm-option.md) | R2045-12 等 CM5 系列 |
| [reServer Industrial](docs/seeed_device/reserver/reserver-industrial-getting-started.md) | |
| [Robotics J401](docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md) | |
| [Robotics J501](docs/seeed_device/recomputer-robotics/robotics-j501-jetpack-6-2-1.md) | |

### NVIDIA 官方套件（official_kit）

| 条目 |
|------|
| [JP 6.2.2 发布](docs/official_kit/common/jetpack-6-2-2-l4t-r36-5-release.md) |
| [JP 7.2 发布](docs/official_kit/common/jetpack-7-2-l4t-r39-2-release.md) |
| [Orin Nano JP7.2 ISO](docs/official_kit/jetson-orin-nano-devkit/jetpack-7-2-iso-install.md) |
| [AGX Orin JP7.2 更新](docs/official_kit/jetson-agx-orin-devkit/jetpack-7-2-iso-update.md) |
| [GPIO pinmux](docs/official_kit/common/jetpack-6-gpio-pinmux.md) |

### 跨平台通用（common）

| 条目 |
|------|
| [BSP 后装 SDK](docs/common/install-jetpack-components-after-bsp.md) |

## 待确认（staging）

| 条目 | 来源 |
|------|------|
| [Seeed J401/J501 是否支持 JP7.2](docs/staging/seeed-j401-jetpack-7-2-support.md) | [Forum](https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471) |
| [apt upgrade 与 BSP 冲突](docs/staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md) | [issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41) |
| [reServer J4012 PoE](docs/staging/reserver-industrial-j4012-poe-jetpack-6.md) | [Forum](https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727) |
| [reServer J4012 PoE/GPIO 记录](docs/staging/reserver-industrial-j4012-jetpack-6-gpio-poe.md) | 同上 |
| [Jetson RTC 电池寿命与更换](docs/staging/jetson-rtc-battery-lifespan-replacement.md) | NVIDIA PMIC_BBAT 12–50 µA；CR1220 约 1–5 月 |

## 结案日志

[`cases/`](cases/)
