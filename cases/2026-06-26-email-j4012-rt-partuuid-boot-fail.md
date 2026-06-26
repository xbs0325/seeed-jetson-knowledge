---
date: 2026-06-26
channel: email
product: reComputer Industrial J4012 (Orin NX 16GB)
customer: Akash Potti (Pace Robotics)
resolved: partial
confidence: confirmed
related_case: cases/2026-06-22-email-j4012-preempt-rt-r3643.md
---

## 问题摘要

客户按 Seeed BSP R36.4.3 指引成功编译 PREEMPT_RT 内核（`./nvbuild.sh -r`），并用 `l4t_initrd_flash.sh` 刷入 **reComputer Industrial J4012**，目标存储为 **NVMe SSD**。

刷机后无法启动，串口反复出现：

```
mount: /mnt: can't find PARTUUID=a7fd4784-59a4-4627-bf3a-00ec9a9e207c
ERROR: mounting PARTUUID=... as /mnt failed
/mnt is not a mountpoint
ttyTCU0: Press [ENTER] to start bash in XX seconds...
```

客户询问是否与刷机配置、PARTUUID 不匹配、NVMe 检测或 RT 内核额外步骤有关。

## 诊断结论（置信度：已确认）

该现象在 Jetson **自定义内核 + NVMe 根分区**场景下常见，**通常不是 RT 内核本身缺陷**，而是 **initrd 与新建内核/模块不一致**，导致早期启动阶段 **NVMe/PCIe 驱动无法加载**，initrd 内看不到 NVMe 分区，因而报「找不到 PARTUUID」。

次要可能：UEFI 仍从旧启动项引导；`l4t_update_initrd.sh` 未执行或失败（如缺少 `cpio`）；刷机参数与板型/存储不匹配。

## 答复要点

1. **优先排查**：客户是否完整执行 `sudo ./tools/l4t_update_initrd.sh`（在 `nvbuild.sh -r -i` 之后、刷机之前），且无报错。
2. **紧急 shell 诊断**：在 `Press [ENTER]` 提示处进入 bash，收集 `lsblk`、`blkid`、`cat /proc/cmdline`、`dmesg | grep -iE 'nvme|pcie'`。
3. **修复路径**：在 host 上重新 `nvbuild.sh -r` → `do_copy.sh` → `nvbuild.sh -r -i` → **`l4t_update_initrd.sh`** → **完整** `l4t_initrd_flash.sh`（Industrial：`recomputer-industrial-orin-j201`，`--external-device nvme0n1p1`）。
4. **恢复选项**：先用 Seeed JP 6.2 mfi 包 `--flash-only` 验证硬件与 NVMe 可启动，再重做 RT 构建刷机。
5. **待客户补充**：`l4t_update_initrd.sh` 完整输出；host 刷机日志末尾；紧急 shell 上述命令输出。

## 知识库更新

- [x] `docs/faq/j4012-preempt-rt-kernel-seeed-bsp-r3643.md` — 新增「刷机后 PARTUUID 挂载失败」排障节

## 来源

- https://docs.nvidia.com/jetson/archives/r36.4.4/DeveloperGuide/SD/Kernel/KernelCustomization.html
- https://forums.developer.nvidia.com/t/cant-find-partuuid-when-replacing-kernel-on-a-custom-board/288839
- https://forums.developer.nvidia.com/t/the-system-does-not-start-after-kernel-compilation-error-mounting-partuuid/354816
- https://forums.developer.nvidia.com/t/when-flashing-jetson-agx-orin-to-nvme-using-l4t-initrd-flash-sh-the-device-fails-to-boot-with-mounting-partuuid-xxx-as-mnt-fail-error/372074
- https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/
