---
date: 2026-07-14
channel: zoho
product: Mini AI Computer T506S (SKU 114110167, Jetson Xavier NX 8GB)
resolved: partial
confidence: need_review
---

## 问题摘要

英文客户拥有 Mini AI Computer T506S（Xavier NX 8GB）。原文存在歧义：

1. `upgrade options for its carrier board` → 更偏向 **载板升级/更换方案**
2. `Does this carrier board support … Orin NX or Orin Nano` → 也在问 **现有 T506S 载板能否插新模组**

结合内部关注点「是否还有支持 Xavier 的载板在售」，主答应以 **换/升级载板（或整机）** 为准；本机换 Orin 模组仅作附带澄清。

客户对新路径的接口诉求：Ethernet、PoE、USB、NVMe、CAN、RS-232、RS-485、GPIO、HDMI、Wi-Fi、Bluetooth；并要最新 JetPack、BSP、刷机镜像、设备树、安装说明。

## 答复要点

### 解读与口径

- 不是中文翻译错误；英文两句把「换载板」和「现有载板是否支持新模组」叠在一起了。
- **主答**：能给哪些 Seeed 载板/整机替换路线，且尽量满足接口列表；Xavier 载板是否仍在售。
- **附带**：明确 T506S 现有载板 **不建议/不承诺** 直插 Orin NX/Nano。

### 技术结论

| 路径 | 结论 |
| --- | --- |
| 本机 T506S 载板插 Orin | **不支持对外承诺**（NVIDIA 非 pin 兼容；公开资料仅 Xavier） |
| 保留 Xavier 换 Seeed 载板 | **有** Xavier 载板入口：**J202**；整机还有 J2021 / Industrial J2012 / T506S。接口会缩水，**J202 远不等于 T506S 的 5×PoE 工业口** |
| 要 Orin + 尽量贴近 T506S 接口 | 优先评估 **reServer Industrial**（5×GbE / 4×PoE、COM RS232/422/485、CAN、HDMI、USB、NVMe；无线可选） |
| T506S 本身最新 JetPack / BSP | 出厂 JP4.6；公开 Wiki **缺 T506S 刷机页**；不可承诺 JP5.1.6 DevKit 流程保全接口 |
| Wi-Fi | T506S 为可选贴装；换到 J202/reServer 后走对应 M.2 / miniPCIe 配件，SKU 需销售确认 |

## 知识库更新

- [x] 修正本 case 与 staging：主叙事改为「升级/更换载板」
- [x] `docs/faq/seeed-xavier-nx-carrier-boards-availability.md`（仍适用）
- [x] `INDEX.md`

## 来源

- https://www.seeedstudio.com/Mini-AI-Computer-T506S-with-Jetson-Xavier-NX-8GB-p-5507.html
- https://wiki.seeedstudio.com/reServer_Industrial_Getting_Started/
- https://wiki.seeedstudio.com/reComputer_J2021_J202_Flash_Jetpack/
- https://www.seeedstudio.com/reComputer-J202-Carrier-Board-for-Jetson-Xavier-NX-p-5397.html
- https://developer.nvidia.com/embedded/jetpack-archive
- https://forums.developer.nvidia.com/t/can-i-connect-jetson-orin-nx-16-board-to-xavier-nx-carrier-board/241776/4

## PR

- cursor/t506s-xavier-carrier-support-923a
