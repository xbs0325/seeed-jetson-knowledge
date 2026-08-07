---
channel: email
reply_to: customer
product: reComputer Industrial J4012 (Orin NX 16GB)
issue_type: compatibility
confidence: confirmed
final_customer_reply: true
related_case:
  - cases/2026-06-22-email-j4012-preempt-rt-r3643.md
  - cases/2026-06-26-email-j4012-rt-partuuid-boot-fail.md
date: 2026-08-04
---

# 英文邮件：Industrial J4012 升级 Ubuntu 24.04 后如何启用 PREEMPT_RT

## 客户问题

Akash Potti（Pace Robotics）此前在 **reComputer Industrial J4012** 上按 Seeed BSP R36.4.3 成功部署 PREEMPT_RT（Ubuntu 22.04）。现计划升级到 **Ubuntu 24.04**，要求提供与此前类似的 PREEMPT_RT 步骤与文档。

## 核对资料

- Industrial Getting Started：已含 **Jetpack7.2** 页签与 J4012 mfi 下载。
- Seeed JP7.2 Resource Hub / Flash and OTA：Ubuntu 24.04 = JetPack 7.2 / L4T 39.2 / kernel 6.8；JP6→JP7 需完整刷机。
- Seeed `Linux_for_Tegra` 分支 **`r39.2.0`**：含 Industrial、`nvbuild.sh -r`、`generic_rt_build.sh`；刷机 conf 为 **`recomputer-industrial-orin-j401`**。
- Seeed PREEMPT_RT Wiki：目前公开的是 **JetPack 6.2.1 / R36.4.4** 指南，**未找到 JP7.2 专用 RT 页**。
- NVIDIA R39.2 RealTimeKernel / Kernel Customization：支持 Orin NX 源码构建 RT；OTA deb 面向官方栈，不宜直接用于 Seeed 载板。

## 最终结论（内部）

1. Ubuntu 24.04 不是在 JP6 上打补丁，而是迁移到 **JetPack 7.2 / R39.2**。
2. 先刷 Seeed Industrial JP7.2 基线，再基于 **`r39.2.0` + `./nvbuild.sh -r`** 编译并刷入 RT。
3. 对外可说明：流程与此前类似，但版本/工具链/board conf 已变；尚无独立 JP7.2 RT Wiki，可参考 JP6.2.1 RT 指南结构 + r39.2.0 readme + NVIDIA R39 文档。
4. 不要推荐 NVIDIA RT APT；不要复用 R36.4.3 内核产物。

## 知识库更新

- [x] `docs/faq/j4012-preempt-rt-kernel-ubuntu2404-jp72-r392.md`（active）
- [x] 更新 `INDEX.md`
- [x] 更新 `docs/staging/seeed-j401-jetpack-7-2-support.md`（Industrial 已有 JP7.2 镜像）
- [x] 交叉链接既有 R36.4.3 RT FAQ

## 外发英文要点

- Ubuntu 24.04 → JetPack 7.2 / L4T R39.2；先刷 Industrial JP7.2 基线再编 RT。
- BSP：`r39.2.0` + `./nvbuild.sh -r`；board conf：`recomputer-industrial-orin-j401`。
- 参考 JP 6.2.1 RT Wiki 结构 + r39.2.0 readme + NVIDIA R39 文档；仍建议 host 编译 + 刷机，并务必更新 initrd。
