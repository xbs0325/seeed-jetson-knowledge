---
product: Jetson Orin series GPIO
vendor: nvidia
platform: official_kit
jetpack: "6.x"
l4t: "36.x"
tags:
  - gpio
  - pinmux
  - jetson-gpio
  - bct
  - troubleshooting
date: 2026-06-10
source_url: https://github.com/NVIDIA/jetson-gpio/issues/114
status: active
---

# JetPack 6 GPIO：输出不生效与 pinmux/BCT 关系

## 适用范围

- NVIDIA Jetson Orin 系列官方平台的 GPIO/pinmux 排查。
- 适用平台类型：`official_kit`。
- Seeed 载板可能有自己的 pinmux、设备树和 GPIO 映射；Seeed 设备需优先查看对应 Seeed Wiki/BSP。

## 现象

部分用户在 JetPack 6.x 上使用 Jetson.GPIO 或用户态 GPIO 工具时，输入可用但输出不生效，或旧的 `/sys/class/gpio` 方式不可用。

## 官方/上游说明

- JetPack 6 使用 upstream kernel GPIO driver，而不是 JetPack 5 的 downstream kernel driver。
- upstream GPIO driver 不支持像旧版本那样动态把某些引脚切成 GPIO 模式。
- 若要把某个引脚作为 GPIO 使用，需要在 pinmux/BCT 中配置该引脚，并重新刷入对应配置。
- NVIDIA 文档要求使用 Orin pinmux spreadsheet 生成 `pinmux.dtsi` 与 `gpio.dtsi`：
  - `pinmux.dtsi` 复制到 `Linux_for_Tegra/bootloader/generic/BCT/`
  - `gpio.dtsi` 复制到 `Linux_for_Tegra/bootloader/`
- 使用 GPIO 时，还需确认对应 pinmux register 的 `E_IO_HV`/3.3V tolerance 设置，以及 Pin Direction 是否满足用户态输入/输出需求。
- JetPack 6 中 GPIO sysfs 已废弃，推荐使用 upstream GPIO 工具（如 libgpiod/gpioset/gpioget/gpioinfo）。

## 售后提示

如果客户使用 Seeed reComputer/reServer/Robotics：

1. 不要直接让客户套 NVIDIA 官方开发套件 pinmux 文件。
2. 先确认 Seeed 型号、JetPack/L4T 版本、使用的 Seeed 镜像/BSP、载板硬件接口。
3. 如果 Seeed 未明确给出该引脚在当前镜像中的支持状态，应标记为 `unknown` 或升级给人工复核。

## 相关链接

- NVIDIA Jetson.GPIO issue #114：<https://github.com/NVIDIA/jetson-gpio/issues/114>
- NVIDIA Jetson Linux Developer Guide pinmux changes：<https://docs.nvidia.com/jetson/archives/r36.3/DeveloperGuide/HR/JetsonModuleAdaptationAndBringUp/JetsonAgxOrinSeries.html?highlight=pin%20direction#pinmux-changes>
