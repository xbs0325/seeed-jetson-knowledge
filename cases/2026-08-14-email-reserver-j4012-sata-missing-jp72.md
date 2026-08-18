---
date: 2026-08-14
channel: zoho
reply_to: user_internal
product: reServer Industrial J4012 (Orin NX 16GB)
issue_type: flashing
resolved: partial
confidence: confirmed
final_customer_reply: false
---

# 英文邮件：reServer Industrial J4012 JP7.2 后双 SATA 不可见

## 问题摘要

客户 Ahmed El Shrief（订单 4000502783，SKU J4012，reServer Jetson Industrial）安装 2× WD RED Pro SATA 4TB，用 Seeed-Jetson-DevelopTool 升到 JetPack 7.2 后：`lsblk` 仅 NVMe，`lspci` 无 SATA 控制器。

## 客户最新证据

| 命令 | 输出要点 |
|------|----------|
| `/proc/device-tree/model` | `NVIDIA Jetson Orin NX Engineering Reference Developer Kit Super` |
| `/etc/nv_tegra_release` | R39 / REVISION 2.1（JP7.2 / L4T 39.2 族） |
| `uname -a` | `6.8.12-1021-tegra` |
| `lspci … sata/ahci…` | 空 |

客户称使用 Seeed-Jetson-DevTools 刷机；刷机前 SSD 未装，之后再装盘。尚未明确答复「升级前 SATA 是否可用」。

## 核对资料

- Wiki：[reServer Industrial Getting Started](https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/) — JP7.2 包 `mfi_reserver-industrial-orin-nx-16g-7.2.0-39.2.0-…`
- Wiki：[SATA Connectors](https://wiki.seeedstudio.com/reserver_industrial_hardware_interface_usage/#sata-connectors)
- Wiki：[Flash and OTA JP7.2](https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/) — 必须选确切载板镜像
- DevelopTool `l4t_data.json`：`j4012reserver` + `39.2.0` 与 `orin-nano-devkit-super` + `39.2` 并存
- NVIDIA：该 model 字符串对应 Orin NX + p3768 Engineering Reference / DevKit Super 配置

## 结论（内部）

- **事实**：当前设备树型号是 NVIDIA DevKit Super（p3768），不是 reServer Industrial 载板 BSP。
- **推断**：错误板级镜像导致载板 PCIe-to-SATA 未进入设备树，故 `lspci` 无控制器、`lsblk` 无 sda/sdb。
- **建议**：用 Wiki / DevelopTool 的 **reServer Industrial J4012** JP7.2 包完整重刷；重刷前备份数据。勿再选 DevKit Super 或其它相近型号。
- **禁止**：在未重刷正确镜像前断言硬盘损坏或承诺保修结论。

## 知识库更新

- [x] `docs/faq/reserver-industrial-sata-missing-wrong-devkit-image.md`（active）
- [x] `INDEX.md`

## 来源

- 客户邮件线程（2026-08-12 ～ 2026-08-13）
- 上述 Wiki / DevelopTool / NVIDIA 文档

## PR

- draft（本分支）
