---
product: reComputer Industrial J4012 / J4011 / J3011 / J3010
vendor: seeed
platform: seeed_device
jetpack: "5.1.x / 6.x / 7.2"
l4t: "35.x / 36.x / 39.x"
tags:
  - faq
  - recomputer-industrial
  - ethernet
  - poe
  - lan7430
  - bsp
date: 2026-08-13
source_links:
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J20_Hardware_Interfaces_Usage/
status: active
---

* 问题
  * reComputer Industrial 两个 RJ45 分别做什么？一边不亮/不通时怎么先核对 BSP？PoE 怎么理解？
* 适用产品
  * Seeed reComputer Industrial J4012 / J4011 / J3011 / J3010（以及同载板的 J201 系列接口说明）
* 适用平台类型：seeed_device
* 简洁答案
  * **LAN1（最左侧）**：直连 Jetson 侧 GbE，并带 **PoE PSE 802.3af（最高约 15W）**，可给 PoE IP 相机供电。
  * **LAN2**：经板载 **LAN7430** PCIe 网卡，一般作上行接交换机/路由器。
  * 官方 Industrial 镜像下两口都应能用；**没有「只能用其中一个口上网」的产品限制**。
  * 指示灯：Wiki 写明 **绿灯仅在 1000M 链路点亮**；黄灯表示活动。100/10M 时可能几乎看不到绿灯，不要单凭「没灯」断定口坏了。
  * 排查时先确认是否在跑匹配的 Seeed Industrial 镜像（见下方命令）；`nv_boot_control.conf` 中应出现 `recomputer-industrial-orin-j201`（JP6 常见）一类 Industrial 板级标识，而不是纯 DevKit 配置。
* 注意事项
  * **不要把 reServer Industrial 的 PoE GPIO 开启步骤**（如 `gpioset gpiochip2 15=1`）套用到 reComputer Industrial；那是 reServer 四路 PoE 的控制方式。
  * reComputer Industrial 的 PoE 为硬件 PSE；相机须兼容 **802.3af 且功耗 ≤15W**，并使用足够容量的 **12–24V** 供电（标配约 19V 适配器）。供电不足时整机可能仍能开机，但 PSE 可能无法给相机上电。
  * `lsmod | grep lan743` 无输出不一定等于驱动缺失：接口可能已由内建/`lan743x` 等驱动拉起。应结合 `lspci`、`ip -br link`、`ethtool -i <iface>`、`dmesg` 一起看。
  * 两口都拿到 IP 但拔掉 LAN1 就掉线，常见是 **默认路由只在 LAN1**（网络/NM 配置问题），不一定是 LAN2 硬件坏。需查 `ip route`，并单独只接 LAN2 做连通性测试。
* 建议核对命令

```bash
cat /etc/nv_tegra_release
uname -r
cat /etc/nv_boot_control.conf
lspci -nn | grep -i eth
lsmod | grep -iE 'lan743|r816'
ip -br link
ip route
ethtool enP1p1s0
ethtool enP8p1s0
# 将接口名换成本机实际名称
dmesg | grep -iE 'lan743|ethernet|eth|r816|nvethernet'
```

* 相关链接
  * [reComputer Industrial Getting Started](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/)
  * [Industrial J40/J30 Hardware Interfaces — Gigabit Ethernet](https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/)
  * [Industrial J20 Hardware Interfaces](https://wiki.seeedstudio.com/reComputer_Industrial_J20_Hardware_Interfaces_Usage/)
