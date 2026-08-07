---
date: 2026-07-15
channel: zoho
reply_to: user_internal
product: reComputer Super J4012 / reComputer Industrial J4012
issue_type: accessory
resolved: yes
confidence: confirmed
final_customer_reply: false
---

## 问题摘要

英文客户希望采购类似 reComputer Industrial J4012 或 Super J4012 的 Box PC，需求：2×1GbE、LTE Nano SIM、Orin NX 16GB；偏好 Super Mode，但认为 Super 似乎没有 SIM/LTE 选项，询问如何在 Super 上用 LTE、两款各需哪些配件，并希望立刻订 1 套做测试。

## 答复要点

- **已确认**：两款均有 Orin NX 16GB 与 2× GbE。
- **已确认**：Super J4012 提供 **mini-PCIe for LTE 4G** 与机内 **SIM card slot**；LTE 模组/天线为选配，不是「不能上 LTE」。
- **已确认**：Industrial J4012 标配 **Nano SIM**，可通过 mini-PCIe（EC25 等）或 M.2 Key B（如 SIM8202G-M2）上网；二者不可同用，且需按方案设置 J8 `SIM_MUX_SEL`。
- **配件建议（Super）**：地区匹配 EC25 mini-PCIe（如北美 113991134）+ 4G Antenna Kit **110061502**（可选 GPS 天线 110061521）；可从 Super Bundle 页一并选购。
- **配件建议（Industrial）**：同系 EC25 mini-PCIe + 天线 + Nano SIM；Wiki 已覆盖安装与拨号步骤。
- **需转交**：立即订购 1 套、价格、库存、交期 → 销售/店铺。

## 知识库更新

- [ ] 无（已有条目覆盖）
- [x] `docs/faq/recomputer-super-industrial-j4012-lte-sim-accessories.md`（active）
- [ ] `docs/staging/...`（待确认）
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
- https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
- https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
- https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
- https://www.seeedstudio.com/reComputer-Super-Bundle.html
- https://www.seeedstudio.com/reComputer-Industrial-J4012-p-5684.html
- https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_super_user_manual.pdf

## PR

- cursor/super-industrial-lte-sim-78c1
