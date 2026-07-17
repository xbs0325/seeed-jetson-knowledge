---
product: A603 Carrier Board (SKU 102110840) + Jetson Orin NX 16GB
vendor: seeed
platform: seeed_device
jetpack: "6.2+ for SUPER modes; board itself has JP5.1–7.2 BSP on Wiki"
l4t: ""
tags:
  - a603
  - usb
  - ffc
  - zif
  - power
  - maxn
  - super
date: 2026-07-17
source_links:
  - https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
  - https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
  - https://files.seeedstudio.com/products/NVIDIA/A603-Carrier-Board-for-Jetsson-Orin-NX-Nano-Datasheet.pdf
  - https://developer.nvidia.com/blog/nvidia-jetpack-6-2-brings-super-mode-to-nvidia-jetson-orin-nano-and-jetson-orin-nx-modules/
  - https://docs.nvidia.com/jetson/archives/r36.4.4/DeveloperGuide/SD/PlatformPowerAndPerformance/JetsonOrinNanoSeriesJetsonOrinNxSeriesAndJetsonAgxOrinSeries.html
  - https://forum.seeedstudio.com/t/jetson-a603-current-draw/294442
status: need_review
review_target: docs/seeed_device
review_reason: "公开资料无官方推荐的 20P ZIF→USB 转接线 SKU；SUPER/MAXN 无 A603 明文支持声明；规格书 DC 口 3A 与整板 7A 表述不一致，需产品/硬件确认"
next_action: "产品或硬件确认：1) 是否有推荐/在售的 W11 FFC→USB-A/Micro-B 转接线或适配板；2) A603 是否正式支持 Orin NX MAXN / MAXN SUPER / 40W，以及推荐电源与散热；确认后移入 docs/seeed_device 并更新 INDEX"
---

# A603：USB3 20P ZIF 线材与 MAXN/SUPER 供电（待确认）

## 适用范围

- Seeed **A603** Carrier Board（SKU **102110840**）+ Jetson Orin NX / Orin Nano 模组。
- 不适用：reComputer Classic J401 / Super / Robotics / Industrial 等其它载板（USB 口形态不同）。

## 事实

### USB 接口（公开规格一致）

A603 的 USB 为：

- **2× USB 3.0 Type-A**（集成 USB 2.0）
- **1× USB 3.0，0.5 mm pitch，20P ZIF**（Datasheet 标注 **W11**）
- **1× USB 2.0 Micro-AB**（刷机/设备口，非第三路 USB 3）

因此「3 路原生 USB 3」= 2× Type-A + 1× ZIF，**不是** 3 个 Type-A 口。

Datasheet 对 **W11（20PIN Multi-function Interface）** 给出信号定义（摘要）：

| Pin | Signal | Pin | Signal |
| --- | --- | --- | --- |
| 1–5 | 5V | 11–12 | USB3.0_SSTX_N / SSTX_P |
| 6 | GND | 13 | GND |
| 7–8 | USB2.0_DN / DP | 14–15 | USB3.0_SSRX_N / SSRX_P |
| 9 | GPIO_01 | 16 | GND |
| 10 | GND | 17 | GPIO_06 |
| | | 18 | GND |

（完整表以 [A603 Datasheet PDF](https://files.seeedstudio.com/products/NVIDIA/A603-Carrier-Board-for-Jetsson-Orin-NX-Nano-Datasheet.pdf) 为准。）

### 线材 / 配件

- 商详/分销包装清单常见为：**载板 + 19V/4.74A（5.5/2.5 mm）电源适配器**（电源线可能另购）。
- **公开渠道未找到** Seeed 官方 SKU 或 Wiki 推荐的「A603 W11 20P FFC → USB Micro-B / Type-A / 主板 20-pin header」成品线材。
- Wiki（刷机页）与 Jetson FAQ 未覆盖该转接线选型。
- PC 主板常见 **USB 3.0 20-pin IDC header** 线与本板 **0.5 mm FFC ZIF** 在机械与引脚定义上均不同，**不能当作同款配件直接推荐**。

### 供电规格

- 规格表：**+9V ~ +20V DC Input @ 7A**。
- 常见推荐适配器：**19V / 4.74A**（约 90W）。
- Datasheet **DC Interface (W4)** 注释另有 **DC +9V – +20V (3A)** 表述，与整板 **7A** 不一致，公开资料未解释。
- NVIDIA：Orin NX 在 JetPack 6.2+ 提供 **40W** 与 **MAXN SUPER** 等模式；MAXN/MAXN SUPER 为 uncapped/实验性功耗模式，受热设计与电源能力约束。
- Seeed 公开 Wiki/商详/**未**写明「A603 正式支持 SUPER / MAXN」。
- Forum 有用户询问 A603 7A 是否对应 MAXN，仅有非官方社区回复，**不能当结论**。

## 推断

- 若按 **19V×7A≈133W** 或随机 **~90W** 适配器粗算，对 Orin NX 模组 **40W / MAXN SUPER** 的模组侧功耗通常有余量；但还需计入载板、NVMe、**多路 USB3 相机** 与散热，且依赖 DC 口实际设计电流能力（3A 注释未澄清前不能对外承诺）。
- 第三路 USB3 相机需要按 Datasheet **W11 引脚** 定制 **0.5 mm 20P FFC → 客户相机接口（如 USB Micro-B / Type-A）** 线材或适配板；Seeed 侧目前只能提供引脚定义，不能点名现货 SKU。

## 建议

- 对客户：可说明 USB 口真实形态 + 提供 Datasheet / W11 引脚；说明 **暂无官方推荐成品转接线**，需按 pinout 定制或向销售/产品询配件。
- 对 SUPER/MAXN：可说明输入规格与推荐 90W 适配器，并强调需 **JP6.2+、正确刷机/外设驱动、主动散热**；**不能**写成「官方已确认 A603 支持 SUPER/MAXN」，除非产品/硬件书面确认。
- 内部：转产品或硬件确认转接线是否有在售/可定制，以及 7A vs 3A、SUPER/MAXN 支持口径。

## 禁止

- 禁止推荐「随便买一根 PC 主板 20-pin USB3 线」接 W11。
- 禁止断言 Seeed「有/没有」某款转接线库存，除非已核对商详配件区或内部配件清单（当前公开页未见）。
- 禁止对外承诺 A603「保证支持 MAXN SUPER / 40W 满载」而无产品确认。

## 相关链接

- [A603 Wiki 刷机](https://wiki.seeedstudio.com/reComputer_A603_Flash_System/)
- [A603 商详](https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html)
- [A603 Datasheet](https://files.seeedstudio.com/products/NVIDIA/A603-Carrier-Board-for-Jetsson-Orin-NX-Nano-Datasheet.pdf)
- [NVIDIA JetPack 6.2 Super Mode](https://developer.nvidia.com/blog/nvidia-jetpack-6-2-brings-super-mode-to-nvidia-jetson-orin-nano-and-jetson-orin-nx-modules/)
