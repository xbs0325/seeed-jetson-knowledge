---
date: 2026-08-11
channel: zoho
reply_to: user_internal
product: reComputer Robotics J401 (Jetson Orin NX)
issue_type: flashing
resolved: partial
confidence: need_review
final_customer_reply: false
customer: Karthikeyan Mahalingam / Nallaperumal Thanthondri
---

## 问题摘要

客户购买 **reComputer Robotics J401**（Orin NX，称预装 JetPack 6）。症状：

- 19V/4.7A 供电，PWR 绿灯亮；XT30 / 5525 两路都试过
- USB 2.0 Device/Debug 口 `lsusb` 有 Silicon Labs CP210x（`10c4:ea60`），`/dev/ttyUSB0` 存在
- minicom / picocom 115200：无启动日志、无登录提示；minicom 无法输入
- 无 HDMI 画面
- `lsusb` 无 NVIDIA APX/Recovery 设备
- 客户追问是否有更新

## 核对资料

- Wiki Robotics 规格：**显示为 Type-C Host DP 1.4，无原生 HDMI**；需 PD/DP→HDMI 或 DP 线
- Wiki：Debug 口需拨码到 **debug**；Recovery 需拨码到 **RESET/REC**，`lsusb` 应出现 `0955:7xxx`
- Debug Guide：115200、无流控；ModemManager 可能占用串口；无 boot 日志先核对 debug 口与拨码
- 本地：`docs/seeed_device/recomputer-robotics/robotics-j401-interfaces.md`

## 答复要点（内部）

1. **事实**：Robotics ≠ Classic；无 HDMI；CP210x 仅说明载板侧 Debug 桥与输入电源基本正常。
2. **推断**：当前更像「SoM 未出 bootloader / 未正确进 Recovery / 显示口接错」，尚不能下硬件损坏结论。
3. **建议**：先纠正显示口 → 确认 REC 拨码与串口 → 强制 Recovery 并回传 `lsusb` → 能进则按 Robotics mfi 重刷。
4. **禁止**：未做 Recovery 实测不断言 RMA；勿给 Classic HDMI / Classic 刷机包。

## 知识库更新

- [x] `docs/faq/recomputer-robotics-j401-display-dp-not-hdmi.md`（active）
- [x] `docs/faq/recomputer-robotics-j401-no-boot-no-serial.md`（active）
- [x] `INDEX.md`
- [ ] `docs/staging/...`
- [ ] `memory/...`

## 来源

- https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/
- https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
- https://wiki.seeedstudio.com/jetson_debug_guide/

## PR

- cursor/robotics-j401-no-boot-email-09e2
