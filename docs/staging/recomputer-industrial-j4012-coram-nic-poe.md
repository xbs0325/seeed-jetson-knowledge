---
product: reComputer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "6.1"
l4t: "36.4.0"
tags:
  - recomputer-industrial
  - ethernet
  - poe
  - lan7430
  - coram
  - troubleshooting
date: 2026-08-13
source_type: customer_logs
source_links:
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
status: need_review
review_target: docs/faq
review_reason: "Coram.ai batch symptom (link LED / failover / PoE camera) still needs hardware or lab confirmation; BSP identity from logs is clear but root cause is not."
next_action: "Collect dmesg/ethtool/ip route + power/camera specs; if PoE fails on known-good 802.3af camera with official PSU, escalate hardware/RMA for affected units (order DZ2605060002)."
---

# reComputer Industrial J4012：Coram.ai 双网口 / PoE 症状（待确认）

## 适用范围

- 客户 Coram.ai，订单 **DZ2605060002**，SKU **100049279** reComputer Industrial J4012，批量约 50 台；反馈至少 5 台类似现象。
- 状态 `need_review`：公开 Wiki 可解释双口角色与 LED，但本批「无灯 / 无 failover / 相机不上电」根因未闭环。

## 客户已提供日志要点（测试机）

| 项 | 结果 |
| --- | --- |
| 镜像 | Seeed `mfi_recomputer-industrial-orin-nx-16g-j201-6.1-36.4.0-2024-12-05.tar.gz`，R36.4.0 |
| 内核 | `5.15.148-tegra` |
| 板级 | `TNSPEC` / `COMPATIBLE_SPEC` 含 `recomputer-industrial-orin-j201` |
| `lspci` | Microchip LAN7430 `[1055:7430]` + Realtek RTL8111/8168 `[10ec:8168]` |
| `lsmod \| grep lan743` | 无输出 |
| `ip -br link` | `enP1p1s0`、`enP8p1s0` 均为 `UP` + `LOWER_UP` |

## 客户描述症状

1. 两口都插网线时，**只有 LAN PSE 口有灯**，另一口无灯；但两口都能拿到 IP。
2. 拔掉 LAN PSE 后整机掉线，期望应能走另一口。
3. 相机直连 LAN PSE 取电时相机不亮，怀疑 **PoE PSE 失败**。

## 当前判断（非最终结论）

### 事实

- 该测试机 **不是**「刷成 DevKit / 缺少 Industrial 板级配置」的典型形态；镜像名与 `nv_boot_control.conf` 与 Seeed Industrial 一致。
- 软件上两路网卡均可见且 `LOWER_UP`，与早期「LAN7430 完全不出现」的错误 BSP 场景不同。
- Wiki：LAN1（最左）PoE PSE 802.3af 15W；LAN2 为 LAN7430；绿灯仅 1000M 点亮。

### 推断（需更多证据）

- 「无灯」可能是 **速率非千兆导致绿灯不亮**，或链路灯硬件异常；不能仅凭无灯判定该口无链路（与 `LOWER_UP`/已获 IP 矛盾，需 `ethtool` 核对）。
- 拔 PSE 掉线更像 **默认路由 / NetworkManager 策略只挂在 PSE 口**，需 `ip route` 与「只接 LAN2」单口测试。
- PoE 不上电：可能是相机非 802.3af / 超 15W、供电不足、或 **PSE 硬件异常**（批量 ≥5 台时需重视硬件抽检）。**不要**套用 reServer 的 `gpioset` PoE 开启命令。

### 建议继续向客户索取

1. 之前未回复的：`dmesg | grep -iE 'lan743|ethernet|eth'`
2. `ip route`；`ethtool <iface>`（两口）；`ethtool -i <iface>`
3. 物理口与 `enP*` 对应关系（哪边是最左侧 LAN1）
4. 供电：是否原装 19V；相机型号、是否标称 802.3af、功耗
5. 单口测试：只接非 PSE 口时能否上网；只接 PSE 口接已知好用的 802.3af 相机是否上电

### 禁止外发

- 在未确认前不要断言「一定是硬件坏了」或「一定是配置问题」。
- 不要把 reServer Industrial PoE GPIO 步骤当作本机解决方案发给客户。
