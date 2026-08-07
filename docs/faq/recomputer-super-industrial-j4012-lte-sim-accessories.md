---
product: reComputer Super J4012 / reComputer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "5.1.3 / 6.2"
tags:
  - recomputer-super
  - recomputer-industrial
  - lte
  - sim
  - accessory
  - mini-pcie
date: 2026-07-15
source_links:
  - https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
  - https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/
  - https://www.seeedstudio.com/reComputer-Super-J4012-p-6443.html
  - https://www.seeedstudio.com/reComputer-Super-Bundle.html
  - https://www.seeedstudio.com/reComputer-Industrial-J4012-p-5684.html
  - https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_super_user_manual.pdf
status: active
---

# reComputer Super / Industrial J4012：LTE 与 SIM 配件

## 适用范围

- reComputer Super J4012（Orin NX 16GB，SKU **114110314**）
- reComputer Industrial J4012（Orin NX 16GB，SKU **110110191**）
- 客户需求常见组合：2×1GbE、Orin NX 16GB、LTE + Nano SIM

## 事实

### 两款均满足「双千兆 + Orin NX 16GB」

| 项目 | Super J4012 | Industrial J4012 |
| --- | --- | --- |
| 模组 | Orin NX 16GB | Orin NX 16GB |
| 以太网 | 2× RJ45 GbE | 2× RJ45 GbE（其中 1× PoE PSE 802.3af） |
| LTE 接口 | **1× mini-PCIe**（官方标注 for LTE 4G module） | **1× mini-PCIe**（4G/LoRaWAN）或 **1× M.2 Key B**（4G/5G） |
| SIM | 机内有 **SIM card slot**（与 mini-PCIe LTE 配套使用） | **1× Nano SIM** 卡槽 |
| LTE 模组是否标配 | **否**，需另购 | **否**，需另购 |

### Super 可以用 LTE

客户常误以为 Super「没有 SIM/LTE 选项」。公开规格与 Wiki 说明：

1. 载板提供 **mini-PCIe for LTE 4G module**。
2. 商详 / Catalog / Super User Manual / Hardware Wiki 均涉及 **SIM card slot**；Hardware Wiki 给出插卡与取卡（push in to eject）步骤。
3. LTE 模组与天线为选配，需安装后才能上网。

Wiki 规格表网络项未单独列出 “SIM” 一行，但 Hardware Wiki 与配件清单明确存在机内 SIM 槽与 LTE 安装流程。

### Super 所需 LTE 配件（官方配件表 / Bundle 页）

至少需要：

1. **LTE Cat 4 EC25 mini-PCIe 模组**（按地区选型），例如：
   - EC25-AFXGA — North American — SKU **113991134**
   - EC25-EUXGR — EMEA / Thai — SKU **113991135**
   - EC25-AUXGR — Australia — SKU **113991174**
   - EC25-EFA — Thai — SKU **113991214**
   - EC25-EMGA — Malaysia — SKU **113991234**
   - EC25-JFA — Japan — SKU **113991296**
2. **4G Antenna Kit** — SKU **110061502**
3. 可选：**GPS Antenna Kit for EC25** — SKU **110061521**

订购入口示例：

- Super + 配件：https://www.seeedstudio.com/reComputer-Super-Bundle.html
- Super 单品：https://www.seeedstudio.com/reComputer-Super-J4012-p-6443.html
- 北美 EC25：https://www.seeedstudio.com/LTE-Cat-4-EC25-AFXGA-mini-PCIe-p-5668.html
- 4G 天线：https://www.seeedstudio.com/4G-Antenna-Kit-for-reTerminal-DM-p-5713.html

安装与拨验：开后盖 → 装 mini-PCIe LTE → 插 SIM → 接天线（可走机壳 **4× Antenna Hole**）→ `minicom -D /dev/ttyUSB2` 用 AT 命令验证（见 Super Hardware Wiki）。

电源（Wiki Power Guidelines）：Orin NX 整机建议 **19V 4.74A（5525）** 官方适配器及对应电源线。

### Industrial 所需 LTE 配件

Industrial 标配机内 **Nano SIM**；蜂窝为 Module optional。

**方案 A — 4G via mini-PCIe（Wiki 已测 EC25EUXGA / EC20CEHCLG）：**

1. 选地区匹配的 **EC25 / EC20 mini-PCIe** 模组（商详 Also Add 常列 EC25-EUX 等）。
2. **4G 天线**（模组 MAIN 口，IPEX）。
3. **Nano SIM** 插入 J15（金面朝下）。
4. **J8 跳线**：把 **SIM_MUX_SEL 与 GND** 短接（仅 4G via Mini PCIe 时需要）。

**方案 B — 4G/5G via M.2 Key B（Wiki 已测 SIM8202G-M2 5G）：**

1. M.2 Key B 模组 + 天线（IPEX4 等按模组要求）。
2. 同一 Nano SIM 卡槽。
3. **断开** J8 上 SIM_MUX_SEL–GND 跳线（把 SIM 切到 M.2）。
4. **注意**：Mini PCIe 与 M.2 Key B **不可同时使用**。

Industrial 接口 Wiki：https://wiki.seeedstudio.com/reComputer_Industrial_J40_J30_Hardware_Interfaces_Usage/

## 推断

- 客户更偏好 Super Mode（MAXN）时，可在 **Super J4012 + EC25 mini-PCIe + 4G Antenna Kit + 运营商 Nano SIM** 方案上做评测样机；公开资料支持该路径。
- 若还需工业接口（PoE PSE、DI/DO、RS232/485、无风扇宽温等），应选 Industrial，并用同一类 EC25 配件启用 LTE。

## 建议（客服对内）

1. 先确认客户部署地区，再推荐对应 EC25 频段 SKU。
2. Super 选型时明确说明：**SIM 槽与 mini-PCIe 已有，LTE 模组/天线另购，不是「不能上 LTE」**。
3. 「立刻订 1 套评测」属商务/库存，转销售或店铺客服，不承诺交期与价格。

## 禁止

- 不要说 Super「不支持 SIM/LTE」。
- 不要默认某地区 EC25 可全球通用。
- 不要承诺第三方未验证的 LTE/5G 模组兼容性。
- 不要混用 Robotics（M.2 Key B for 5G）与 Super（仅 mini-PCIe LTE）的说明。
