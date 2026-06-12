---
product: reServer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "6.x"
l4t: "36.x"
tags:
  - reserver-industrial
  - gpio
  - poe
  - libgpiod
  - troubleshooting
date: 2026-06-10
source_url: https://forum.seeedstudio.com/t/reserver-industrial-j4012-with-jetpack-6-jetson-orin-nx-16gb-missing-gpio/279727
status: need_review
---

# reServer Industrial J4012：JetPack 6 PoE/GPIO 排查记录

## 适用范围

- Seeed reServer Industrial J4012，用户自行升级到 JetPack 6 的场景。
- 适用平台类型：`seeed_device`。
- 状态为 `need_review`：来源为 Seeed 论坛问答，建议售后使用前结合最新 Wiki/BSP 再确认。

## 问题背景

有用户反馈 reServer Industrial J4012 升级到 JetPack 6 后：

- `/sys/class/gpio` 不存在或不可按旧方式使用。
- 与 PoE 以太网口、4G/5G 模块相关的 GPIO 映射缺失或行为变化。
- 4 个 PoE 口可能因 GPIO 未拉起而无法供电。

## Seeed 论坛给出的处理建议

Seeed 回复中给出 JetPack 6 下启用 PoE 的 libgpiod 命令示例：

```bash
sudo apt update
sudo apt install gpiod
gpioset gpiochip2 15=1
```

排查 GPIO：

```bash
gpiodetect
gpioinfo
sudo cat /sys/kernel/debug/gpio
```

## 注意事项

- JetPack 6/L4T 36 使用 upstream GPIO 工具链，旧 sysfs GPIO 方式不应作为默认建议。
- `gpioset gpiochip2 15=1` 是论坛上下文中的 reServer Industrial J4012 PoE 示例，不应推广到其他 Seeed 设备。
- 如客户使用非 Seeed 官方 JetPack 6 镜像，需核对设备树、overlay、BSP 和 PoE 控制 GPIO 是否匹配。
- 对生产环境客户，建议回到 Seeed 官方发布的稳定镜像，或等待 Seeed 针对该设备发布明确 JetPack 6/7 BSP。
