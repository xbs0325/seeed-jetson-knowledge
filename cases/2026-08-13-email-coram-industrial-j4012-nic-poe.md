---
date: 2026-08-13
channel: email
reply_to: user_internal
product: reComputer Industrial J4012 (SKU 100049279 / order DZ2605060002)
issue_type: other
confidence: needs_review
final_customer_reply: false
account: Coram.ai (via Nana Zhou / distributor techsupport)
---

# 英文邮件：Coram.ai Industrial J4012 双网口 / PoE 问题（内部建议轮）

## 历史对话背景

- 销售 Nana 转交：Coram 反馈 J4012 一批中至少 5 台「一个 RJ45 可用、另一个不可用」，询问端口用途限制。
- 首轮已说明：LAN1=PoE PSE，LAN2=LAN7430；官方镜像下两口都应用；常见错误原因是非匹配 BSP。
- 客户追问如何核对 BSP；已给出命令清单。
- Aron 回传测试机命令输出（**未含**原先要求的 `dmesg`）。

## 最新客户问题（摘要）

1. 两口都插线时只有 LAN PSE 有灯，另一口无灯，但两口都能获 IP。
2. 断开 LAN PSE 后设备掉线，期望应走另一口。
3. 相机接 LAN PSE 不上电，怀疑 PoE 失败。
4. 询问是否还需更多日志。

## 依据资料

- [Industrial Getting Started](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/)：2× RJ45，1× PoE PSE 802.3af。
- [J40/J30 Hardware Interfaces — Ethernet](https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/)：最左口 Jetson 侧 + PoE；另一口 LAN7430；**绿灯仅 1000M**。
- 知识库：`docs/seeed_device/recomputer-industrial/recomputer-industrial-getting-started.md`；reServer PoE GPIO 仅适用于 reServer（staging），**不可套用**。
- 客户日志：Seeed Industrial mfi R36.4.0 + `recomputer-industrial-orin-j201`；两路 `lspci` eth + 两接口 `LOWER_UP`。

## 内部结论

- **渠道客户**：未关闭确认清单前，不对外下根因、不承诺 RMA。
- **BSP（该测试机）**：日志与 Seeed Industrial 镜像/板级一致；**不能**再把「错 BSP」当主因，但也**不要**引申为整批硬件已定性。
- **根因**：拓扑、「掉线」含义、LAN2 单口可用性、PoE 相机/电源规格均未确认 → 见 staging 清单 A–F。
- 下步：先发核实问题；收齐后再判断是配置/接线、供电/相机规格，还是需销售协同硬件抽检。

## 知识库更新

- [x] `docs/faq/recomputer-industrial-dual-nic-poe-bsp-check.md`（active）
- [x] `docs/staging/recomputer-industrial-j4012-coram-nic-poe.md`（need_review，已加渠道确认清单）
- [x] `memory/preferences.md`（渠道客户须先确认关键不明点）
- [x] 更新 `INDEX.md`

## 外发

- 本轮仅内部建议；用户确认后，外发应以**核实问题为主**，少下结论。
