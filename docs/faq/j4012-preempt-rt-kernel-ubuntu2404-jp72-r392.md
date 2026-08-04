---
product: reComputer Industrial J4012 / Seeed Jetson Orin boards on JetPack 7.2
vendor: seeed
platform: seeed_device
jetpack: "7.2"
l4t: "39.2"
tags:
  - preempt-rt
  - real-time-kernel
  - ubuntu-24.04
  - jetpack-7.2
  - bsp
  - j4012
  - industrial
date: 2026-08-04
source_links:
  - https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
  - https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/
  - https://wiki.seeedstudio.com/flash_preempt_rt_kernel_on_recomputer_jetson_jetpack_6_2_1/
  - https://wiki.seeedstudio.com/jetpack_7_2_resource_hub/
  - https://github.com/Seeed-Studio/Linux_for_Tegra/tree/r39.2.0
  - https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/Kernel/RealTimeKernel.html
  - https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/Kernel/KernelCustomization.html
  - https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/AT/JetsonLinuxToolchain.html
status: active
---

# Ubuntu 24.04 / JetPack 7.2：Industrial J4012 启用 PREEMPT_RT（Seeed BSP R39.2）

## 适用范围

- 客户要从 **Ubuntu 22.04 / JetPack 6.x（如 R36.4.3）** 升级到 **Ubuntu 24.04**，并在 **reComputer Industrial J4012** 上启用 PREEMPT_RT。
- Ubuntu 24.04 on Jetson 对应 **JetPack 7.2 / Jetson Linux R39.2**（内核 6.8），不是在 JP6 上单独换 rootfs。
- 同样思路可延伸到其他使用 Seeed `Linux_for_Tegra` **`r39.2.0`** 的 Orin 产品，但刷机 board conf 必须按产品选择。

## 结论摘要

| 问题 | 答案 |
|------|------|
| Ubuntu 24.04 对应哪一版？ | **JetPack 7.2 / L4T R39.2**（Ubuntu 24.04 rootfs + kernel 6.8） |
| Industrial J4012 是否有 JP7.2 官方镜像？ | **有**。[Industrial Getting Started](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/) 的 **Jetpack7.2** 页签提供 J4012 mfi 下载 |
| Seeed BSP 分支 | GitHub `Seeed-Studio/Linux_for_Tegra` 分支 **`r39.2.0`**；NVIDIA sync tag **`jetson_39.2`** |
| 有无 JP7.2 专用 PREEMPT_RT Wiki？ | **当前未找到**。可对照 [JP 6.2.1 RT Wiki](https://wiki.seeedstudio.com/flash_preempt_rt_kernel_on_recomputer_jetson_jetpack_6_2_1/) 流程，把版本换成 R39.2 + `r39.2.0`，并用 `./nvbuild.sh -r` |
| 能否沿用 R36.4.3 的 RT 产物？ | **不能**。必须用 R39.2 BSP / 内核 6.8 重新编译 |
| 能否用 NVIDIA RT APT 包？ | **不推荐**于 Seeed 载板。仍应按 Seeed BSP 源码编译 RT |
| Industrial 刷机 conf（R39.2） | **`recomputer-industrial-orin-j401`**（注意：JP6 时代多为 `recomputer-industrial-orin-j201`，R39.2 仓库已更名） |

## 事实

- JetPack 7.2 = Jetson Linux 39.2 + Ubuntu 24.04 + Linux 6.8（[JP7.2 Resource Hub](https://wiki.seeedstudio.com/jetpack_7_2_resource_hub/)、[Flash and OTA to JP7.2](https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/)）。
- Industrial Wiki 已列出 **Jetpack7.2** 刷机入口，并含 J4012 镜像下载与 SHA256。
- Seeed `Linux_for_Tegra` **`r39.2.0`** readme 说明基于 JP 7.2 / R39.2.0，并给出 NVIDIA 包下载、`source_sync.sh -t jetson_39.2`、覆盖 Seeed 源、`./nvbuild.sh` / `./do_copy.sh` / `l4t_update_initrd.sh` 流程。
- 同分支 `source/nvbuild.sh` 支持 **`-r`（Enable RT Kernel）**，内部调用 `generic_rt_build.sh enable`，并对 OOT 设置 `IGNORE_PREEMPT_RT_PRESENCE=1`。
- NVIDIA R39.2 文档：Orin NX/Nano 提供 Developer-Preview 级 RT；可用 OTA deb（面向官方栈）或按 Kernel Customization 源码构建（含 `./generic_rt_build.sh "enable"`）。
- JP6→JP7 迁移应 **完整刷机**，不要用跨大版本 `apt upgrade`（Seeed JP7.2 Flash/OTA Wiki）。

## 推断

- Seeed 尚未单独发布「JP7.2 PREEMPT_RT」页面，但 **BSP 脚本已具备与 JP6 相同的 `-r` 开关**，因此对 Industrial J4012 的推荐路径是：先升到 Seeed JP7.2 基线，再按 R39.2 + Seeed overlay 编译 RT 并刷入。
- 对外答复时应说明：步骤与此前 R36.4.3 类似，但 **包版本、工具链、board conf、内核树（`kernel-noble`）均已变更**，不能复制旧命令中的 r36.4.3 链接。

## 建议（给客户的路径）

### 1. 先升级到 Seeed JetPack 7.2（Ubuntu 24.04）基线

1. 备份数据。
2. 按 [Industrial Getting Started — Jetpack7.2](https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/) 刷入对应 **J4012** mfi 镜像；或按 [Flash and OTA to JP7.2](https://wiki.seeedstudio.com/flash_and_ota_jetpack_7.2/) / DevelopTool 选择该产品的 L4T 39.2 镜像。
3. 验证：

```bash
head -n 1 /etc/nv_tegra_release   # 期望 R39.2 族
cat /etc/os-release               # Ubuntu 24.04
uname -r                          # 6.8.x-tegra 线
```

### 2. 在 host 上基于 Seeed R39.2 BSP 编译 PREEMPT_RT

参考 [Seeed r39.2.0 readme](https://github.com/Seeed-Studio/Linux_for_Tegra/tree/r39.2.0) 与 [NVIDIA Kernel Customization (R39.2)](https://docs.nvidia.com/jetson/archives/r39.2/DeveloperGuide/SD/Kernel/KernelCustomization.html)；流程结构对齐 [JP 6.2.1 RT Wiki](https://wiki.seeedstudio.com/flash_preempt_rt_kernel_on_recomputer_jetson_jetpack_6_2_1/)。

```bash
# NVIDIA R39.2 包（链接以 NVIDIA 下载页为准）
wget https://developer.nvidia.com/downloads/embedded/l4t/r39_release_v2.0/release/Jetson_Linux_r39.2.0_aarch64.tbz2
wget https://developer.nvidia.com/downloads/embedded/l4t/r39_release_v2.0/release/Tegra_Linux_Sample-Root-Filesystem_r39.2.0_aarch64.tbz2
tar xf Jetson_Linux_r39.2.0_aarch64.tbz2
sudo tar xpf Tegra_Linux_Sample-Root-Filesystem_r39.2.0_aarch64.tbz2 -C Linux_for_Tegra/rootfs/

cd Linux_for_Tegra/source
./source_sync.sh -t jetson_39.2
cd ../..
git clone https://github.com/Seeed-Studio/Linux_for_Tegra.git -b r39.2.0 --depth=1 github/Linux_for_Tegra
cp -r github/Linux_for_Tegra/* Linux_for_Tegra/
cd Linux_for_Tegra
sudo ./apply_binaries.sh

# 工具链：按 NVIDIA R39.2 Jetson Linux Toolchain 页面下载并设置 CROSS_COMPILE
export ARCH=arm64
export CROSS_COMPILE=<toolchain-path>/bin/aarch64-none-linux-gnu-   # 或 Seeed CI/文档实际使用的前缀

cd source
./nvbuild.sh -r
./do_copy.sh
export INSTALL_MOD_PATH=$(realpath ../rootfs/)
./nvbuild.sh -r -i
cd ..
# 按 readme 复制 Seeed camera/GMSL DTBO 到 rootfs/boot（如需要）
sudo apt install -y cpio
sudo ./tools/l4t_update_initrd.sh
```

### 3. 刷入 Industrial J4012（NVMe）

```bash
sudo ./tools/kernel_flash/l4t_initrd_flash.sh \
  --external-device nvme0n1p1 \
  -c tools/kernel_flash/flash_l4t_t234_nvme.xml \
  -p "-c bootloader/generic/cfg/flash_t234_qspi.xml" \
  --showlogs --network usb0 \
  recomputer-industrial-orin-j401 internal
```

### 4. 验证 RT

```bash
uname -a
zcat /proc/config.gz | grep PREEMPT
# 期望含 -rt 与 CONFIG_PREEMPT_RT=y
```

## 禁止 / 风险提示

- **禁止**把 R36.4.3 的 Image / modules / initrd 直接搬到 Ubuntu 24.04。
- **禁止**对客户承诺「NVIDIA `nvidia-l4t-rt-kernel` APT 可安全用于 Seeed Industrial」（DevKit 导向；会覆盖 Seeed DTB/外设驱动）。
- **禁止**用跨大版本 `apt upgrade` 从 JP6 升到 JP7。
- Industrial 上勿默认建议启用 **MAXN SUPER**（Wiki 对 J4011/J4012 散热有明确警告，尤其 JP6.2 语境；JP7.2 仍应保守）。
- NVMe 刷 RT 后若出现 PARTUUID 挂载失败，优先核对 **`l4t_update_initrd.sh` 已成功**（见既有 R36.4.3 RT PARTUUID FAQ）。

## 售后需向客户确认

1. 是否已备份当前系统数据。
2. 目标是否明确为 **JetPack 7.2 / Ubuntu 24.04**（而非仅升级用户态）。
3. 刷机 host 系统版本（JP7.2 刷机可用 Ubuntu 20.04/22.04/24.04；若需 host 侧完整开发组件，Wiki 建议 20.04/22.04）。
4. 工业外设（PoE、DI/DO、RS485、CAN）在 JP7.2 + RT 下是否都需要验证。
