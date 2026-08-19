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
  - channel-customer
date: 2026-08-13
source_type: customer_logs
source_links:
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
status: need_review
review_target: docs/faq
review_reason: "Channel account Coram.ai; multiple critical topology/symptom points still unconfirmed. No root-cause or RMA conclusion until checklist below is closed."
next_action: "Send careful clarification questions; do not assert hardware failure, driver failure, or RMA until topology + single-port + PoE + power/camera facts are confirmed."
---

# reComputer Industrial J4012：Coram.ai 双网口 / PoE（渠道客户 · 待确认）

## 适用范围

- 渠道/经销商链路客户 **Coram.ai**（经 Nana Zhou / Distributor Techsupport）
- 订单 **DZ2605060002**，SKU **100049279** reComputer Industrial J4012，约 50 台；反馈至少 5 台类似
- **渠道口径**：未关闭下方确认清单前，不对外下根因结论、不承诺 RMA/换货

## 产品事实（可对外复述的规格，与本票症状无关）

- **LAN1（最左侧）**：普通数据网口 + **PoE PSE 802.3af（约 15W）**
- **LAN2**：普通数据网口（LAN7430），**无 PoE**
- 官方 Industrial 镜像下两口数据面都应可用；无「只能用一个口」的产品限制

## 客户已提供日志（仅 1 台测试机）

| 项 | 结果 |
| --- | --- |
| 镜像 | Seeed `mfi_recomputer-industrial-orin-nx-16g-j201-6.1-36.4.0-2024-12-05.tar.gz`，R36.4.0 |
| 内核 | `5.15.148-tegra` |
| 板级 | `recomputer-industrial-orin-j201` |
| `lspci` | LAN7430 `[1055:7430]` + Realtek `[10ec:8168]` |
| `lsmod \| grep lan743` | 无输出 |
| `ip -br link` | `enP1p1s0`、`enP8p1s0` 均为 `UP` + `LOWER_UP` |
| `dmesg` | **未提供** |

## 必须确认清单（关闭前不下根因）

### A. 拓扑与「掉线」含义（最优先）

- [ ] LAN1（PoE 口）实际接的是什么？（交换机/路由器 / 相机 / 其他）
- [ ] LAN2（普通口）实际接的是什么？
- [ ] 「disconnect LAN PSE → device goes offline」具体指：
  - [ ] 远程连不上这台 J4012（SSH / 管理平台 / ping 设备）
  - [ ] 还是相机画面/推流断了
  - [ ] 或两者都有
- [ ] 是否有独立上位机/跳板机？还是云端/局域网直接管 J4012？
- [ ] 两口是否接到**同一网段/同一交换机**，还是不同网络？

### B. 物理口 ↔ 系统网卡映射

- [ ] 最左侧 LAN1 对应 `enP1p1s0` 还是 `enP8p1s0`？（需客户标注或拔插观察）
- [ ] 「有灯的口 / 无灯的口」分别对应哪个 `enP*`

### C. LAN2「无灯但有 IP」

- [ ] `ethtool` 的 link detected / speed / duplex（两口）
- [ ] 无灯时是绿灯和黄灯都不亮，还是只有某一灯不亮
- [ ] 对端是 100M 还是 1000M（Wiki：绿灯仅 1000M）
- [ ] 补发：`dmesg | grep -iE 'lan743|ethernet|eth'`

### D. 「拔 LAN1 掉线」是否等于 LAN2 不能用

- [ ] `ip addr`、`ip route`（看默认路由在哪张网卡）
- [ ] **只接 LAN2、不接 LAN1** 时：能否 ping 网关 / 能否远程登录
- [ ] **只接 LAN1、不接 LAN2** 时：管理连通性是否正常
- [ ] NetworkManager / 静态 IP / 是否人为把默认路由绑在 LAN1

### E. PoE 相机不上电

- [ ] 相机型号、是否明确 **IEEE 802.3af**、标称功耗是否 **≤15W**
- [ ] 相机是否曾在其他标准 PoE 交换机上正常上电
- [ ] J4012 供电：是否原装约 19V 适配器，还是客户自备电源（电压/功率）
- [ ] 相机是否插在**最左侧 LAN1**（唯一 PSE 口）
- [ ] 插相机时：口上是否有 link 灯；`ip -br link` 该口状态
- [ ] 是否误把 reServer 的 PoE GPIO 步骤用在本机（本产品 Wiki **无**该步骤）

### F. 批量范围（渠道订单敏感）

- [ ] 「至少 5 台」的准确数量、序列号/资产编号
- [ ] 5 台是否**同一症状组合**（无灯 + 拔 LAN1 掉线 + PoE 不上电），还是各台不同
- [ ] 其余约 45 台是否正常；同批次 / 同镜像 / 同接线方式？
- [ ] 出厂预装系统是否被重刷；若重刷，是否均为该 mfi 包

## 已可谨慎陈述（仍避免引申）

- 该测试机日志显示为 **Seeed Industrial 镜像与板级标识**，与「刷成 NVIDIA DevKit 导致 LAN7430 完全缺失」的典型形态**不一致**。
- 软件上两张网卡接口均存在且为 `LOWER_UP`；**不能**再主推「驱动完全没加载」作为唯一解释（`lsmod` 无 `lan743` 仍要用 `ethtool -i` / dmesg 再核）。

## 禁止外发（渠道）

- 未完成 A–E 前：不说「硬件故障」「PoE 坏了」「LAN2 坏了」「一定是配置问题」
- 不承诺 RMA / 批量换货 / 到场
- 不把 **reServer** PoE `gpioset` 方案发给本产品客户
- 不把 staging 推断写成已确认事实
