---
date: 2026-08-05
channel: zoho
reply_to: customer
product: reComputer Super J3011 / J4012 (board id recomputer-orin-super-j401)
issue_type: other
confidence: confirmed
final_customer_reply: true
resolved: yes
---

## 问题摘要

客户 Shahaf（mano-security.com，Order #7000016981）在两台 Seeed Jetson（Orin Nano 8GB / Orin NX 16GB）上执行 `sudo apt upgrade`，`nvidia-l4t-bootloader` 配置失败：

`ERROR. 3767-000-0000--1--recomputer-orin-super-j401- does not match any known boards.`

系统报告 Model 含 reComputer Classic Super，`COMPATIBLE_SPEC` / `TNSPEC` 板级名为 `recomputer-orin-super-j401`。询问官方支持的更新路径（5 问）。

## 核对资料

- Wiki FAQ Q8 / Q15：自定义载板不要 `apt upgrade`
- Wiki Q9：用 `apt install` 更新应用；系统级等 Seeed 完整 JetPack
- Linux_for_Tegra issue #41（closed）：维护者说明 apt upgrade 与自定义 BSP 冲突，并给出 hold 命令
- Forum 同题 + Seeed_Kevin 指向 FAQ
- 本仓库原 staging 条目与上述一致，已晋升 active FAQ

## 结论

经典问题，非单机故障。NVIDIA stock `nvidia-l4t-*` 不识别 Seeed 板级名。推荐：避免整包 apt upgrade；hold L4T 包；JetPack/BSP 用 Seeed Wiki mfi 重刷。客户设备按板级名按 **Super** 指引。

## 答复要点

见当轮外发英文邮件（回答 Q1–Q5 + hold + Super 刷机 Wiki）。

## 知识库更新

- [x] `docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md`（active，由 staging 晋升）
- [x] 删除 `docs/staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md`
- [x] 更新 `INDEX.md`
- [x] 更新 `docs/faq/seeed-jetson-install-browser-vs-apt-upgrade.md` 链接

## 来源

- https://wiki.seeedstudio.com/Jetson_FAQ/
- https://wiki.seeedstudio.com/upgrade_software_packages_for_jetson/
- https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
- https://forum.seeedstudio.com/t/recomputer-j401-orin-nx-sudo-apt-upgrade-or-package-installation-error-jetpack-6-1/289628
