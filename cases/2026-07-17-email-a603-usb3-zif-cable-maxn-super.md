---
date: 2026-07-17
channel: email
product: A603 Carrier Board + Jetson Orin NX 16GB
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户 Philip（Referer: seeedstudio.com）询问：

1. A603 + Orin NX 16GB，希望用板上 **3 路原生 USB3** 接 3 台 USB3 相机，避免 USB hub；找不到 **20P FFC ZIF → USB 3 Micro-B**（或 Type-A / 主板 20-pin 等标准口）的合适线材/适配器，请推荐。
2. A603 供电系统是否支持 Orin 模组的 **SUPER / MAXN** 模式。

内部问题：现有资料能否查到。

## 答复要点

### 现有资料结论（一句话）

**部分能查到**：USB 口形态与 W11 引脚、供电额定值有公开规格；**推荐成品转接线 SKU 与 SUPER/MAXN 官方支持声明查不到**，需产品/硬件确认。

### 问题 1（USB 线材）

- A603 实际是：**2× USB3 Type-A + 1× USB3 0.5mm 20P ZIF (W11) + 1× USB2 Micro-AB**，共 3 路 USB3。
- Datasheet 有 W11 引脚定义（5V / USB2 D± / USB3 SSTX·SSRX）。
- 公开商详/Wiki/**未**提供官方推荐的 FFC→USB Micro-B/Type-A 线材 SKU；包装清单未见该线。
- 不能把 PC 主板 20-pin USB3 header 线当作兼容配件推荐。

### 问题 2（SUPER / MAXN）

- 规格：**9–20V @ 7A**；常见适配器 **19V/4.74A (~90W)**。
- Datasheet DC 口另有 **(3A)** 注释，与 7A 冲突，未澄清。
- NVIDIA Orin NX SUPER/40W/MAXN SUPER 需 JP6.2+ 等条件；**Seeed 未明文写 A603 支持 SUPER/MAXN**。
- 可从功率余量**推断**通常够模组侧，但不能当官方确认；需计入相机与散热。

### 客服动作建议

1. 先回客户：接口说明 + Datasheet 链接 + 暂无官方成品转接线、可按 pinout 定制。
2. SUPER/MAXN：按规格说明输入能力与推荐电源，标明需散热与正确 JetPack；避免「保证支持」措辞，直到内部确认。
3. 转产品/硬件确认：是否有 W11 转接线配件、SUPER/MAXN 正式口径、7A vs 3A。

## 知识库更新

- [x] `docs/staging/a603-usb3-zif-cable-and-maxn-super-power.md`（待确认）
- [ ] 确认后移入 `docs/seeed_device/` 并更新 `INDEX.md` active 区

## 来源

- https://wiki.seeedstudio.com/reComputer_A603_Flash_System/
- https://www.seeedstudio.com/A603-Carrier-Board-for-Jetson-Orin-NX-Nano-p-5635.html
- https://files.seeedstudio.com/products/NVIDIA/A603-Carrier-Board-for-Jetsson-Orin-NX-Nano-Datasheet.pdf
- https://developer.nvidia.com/blog/nvidia-jetpack-6-2-brings-super-mode-to-nvidia-jetson-orin-nano-and-jetson-orin-nx-modules/
- https://forum.seeedstudio.com/t/jetson-a603-current-draw/294442

## PR

- draft：本分支
