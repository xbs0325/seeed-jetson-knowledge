---
date: 2026-08-14
channel: zoho
reply_to: user_internal
product: Jetson Orin Nano (SSD replacement)
issue_type: accessory
confidence: confirmed
final_customer_reply: false
resolved: yes
---

## 问题摘要

英文客户此前购买 2 台 Orin Nano，SSD 损坏，询问更换时应买哪种 SSD；内部要求给出推荐型号及 Bazaar 链接。

## 客户原文要点

Hi We bought 2 Orin Nano before and the SSD spoil, can i just to confirm if i want to buy SSD to replace what kind of SSD will be supported?

## 答复要点

- 规格：**M.2 Key M + NVMe (PCIe) + 2280**；非 M.2 SATA。
- Seeed Wiki（J401 / Super / Robotics 等）列出 128GB–2TB NVMe M.2 PCIe Gen3x4 2280。
- Bazaar 对应：128GB `112990226`、256GB `112990246`、512GB `112990247`、1TB `112990267`、2TB `114993467`。
- 建议优先推荐 **512GB**（或按原机容量）；换盘后需重刷系统。
- 若实际为 NVIDIA 官方 DevKit，主槽仍为 2280 Key-M NVMe（另有 2230 槽）。

## 知识库更新

- [x] `docs/faq/orin-nano-nvme-ssd-compatibility.md`（active）
- [x] `INDEX.md` 已更新

## 来源

- https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
- https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
- https://developer.nvidia.com/embedded/learn/jetson-orin-nano-devkit-user-guide/hardware_spec.html
- https://www.seeedstudio.com/NVMe-M-2-2280-SSD-512GB-p-5334.html（及同系列其它容量页）

## PR

- draft PR（本分支）
