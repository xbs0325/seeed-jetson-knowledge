---
product: reComputer J4012 / reComputer Industrial J4012 / reServer Industrial J4012
vendor: seeed
platform: seeed_device
jetpack: "6.2"
l4t: "36.4.3"
tags:
  - preempt-rt
  - real-time-kernel
  - bsp
  - kernel-build
  - j4012
date: 2026-06-22
source_links:
  - https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/
  - https://docs.nvidia.com/jetson/archives/r36.4.4/DeveloperGuide/SD/Kernel/KernelCustomization.html
  - https://docs.nvidia.com/jetson/archives/r36.4.4/DeveloperGuide/SD/Kernel/RealTimeKernel.html
  - https://github.com/Seeed-Studio/Linux_for_Tegra/tree/r36.4.3
  - https://forums.developer.nvidia.com/t/are-rt-kernel-package-provided-for-orin-5-1-r36-4-7-miivii-board/357429/2
  - https://forum.seeedstudio.com/t/how-to-install-a-real-time-kernel-for-the-a603-board/293292
status: active
---

# J4012（L4T R36.4.3）启用 PREEMPT_RT 内核：Seeed BSP 构建要点

## 适用范围

- Seeed J4012 系列（Orin NX 16GB），JetPack 6.2 / L4T R36.4.3。
- 含 reComputer J4012、reComputer Industrial J4012、reServer Industrial J4012、reComputer Super J4012 等使用 Seeed `Linux_for_Tegra` BSP 的设备。
- **不适用**：直接安装 NVIDIA 官方 `nvidia-l4t-rt-kernel` APT 包到 Seeed 载板（见下文说明）。

## 结论摘要

| 问题 | 答案 |
|------|------|
| BSP 源版本/tag | GitHub `Seeed-Studio/Linux_for_Tegra` 分支 **`r36.4.3`**；NVIDIA 源同步 tag **`jetson_36.4.3`** |
| PREEMPT_RT 是否已内置 | **否**。需通过 `./generic_rt_build.sh "enable"` 或 Seeed `./nvbuild.sh -r` 启用 |
| 是否可用 NVIDIA RT APT 包 | **不推荐**。NVIDIA 官方 RT deb 面向 DevKit；Seeed 载板需基于 Seeed BSP 自行编译 |
| 推荐部署方式 | **从 Seeed BSP 编译 RT 内核后，经 host 刷机（`l4t_initrd_flash.sh`）部署** |
| J4012 专用 RT 指南 | **当前无 Seeed 官方 J4012 专用 RT 文档**；按 Seeed BSP 构建 Wiki + NVIDIA Kernel Customization RT 章节操作 |

## 为何不用 NVIDIA 官方 RT APT 包

1. NVIDIA Developer Forums 明确：RT kernel deb packages are for **developer kit**；custom board 需手动编译（[NVIDIA Forum](https://forums.developer.nvidia.com/t/are-rt-kernel-package-provided-for-orin-5-1-r36-4-7-miivii-board/357429/2)）。
2. Seeed 设备使用定制 BSP（板级 DTB、额外驱动、`apply_binaries.sh` 等）。直接 `apt install nvidia-l4t-rt-kernel` 会替换为 NVIDIA DevKit 内核/模块，可能导致 Seeed 载板外设（网口、GPIO、PoE 等）异常。
3. 参见本仓库 [apt upgrade 与 BSP 冲突](docs/staging/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md) 记录。

## 构建环境

- Host：Ubuntu 20.04 或 22.04 x86_64 PC。
- 参考：[Seeed BSP 构建 Wiki](https://wiki.seeedstudio.com/how_to_build_the_source_code_project_for_seeed_jetson_bsp/)（以 R36.4.3 为例）。

## 步骤概览

### 1. 下载 NVIDIA BSP 与 rootfs

```bash
wget https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v4.3/release/Jetson_Linux_r36.4.3_aarch64.tbz2
wget https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v4.3/release/Tegra_Linux_Sample-Root-Filesystem_r36.4.3_aarch64.tbz2
tar xf Jetson_Linux_r36.4.3_aarch64.tbz2
sudo tar xpf Tegra_Linux_Sample-Root-Filesystem_r36.4.3_aarch64.tbz2 -C Linux_for_Tegra/rootfs/
```

### 2. 同步 NVIDIA 内核源

```bash
cd Linux_for_Tegra/source/
./source_sync.sh -t jetson_36.4.3
```

### 3. 覆盖 Seeed BSP 定制内容

```bash
cd ../..
git clone https://github.com/Seeed-Studio/Linux_for_Tegra.git -b r36.4.3 --depth=1 github/Linux_for_Tegra
cp -r github/Linux_for_Tegra/* Linux_for_Tegra/
cd Linux_for_Tegra
sudo ./apply_binaries.sh
```

**必须在编译 RT 内核之前完成 `apply_binaries.sh`。**

### 4. 安装依赖与交叉编译工具链

```bash
sudo apt-get update
sudo apt-get install -y build-essential flex bison libssl-dev bc zstd sshpass abootimg nfs-kernel-server libxml2-utils qemu-user-static git-lfs

wget https://developer.nvidia.com/downloads/embedded/l4t/r36_release_v3.0/toolchain/aarch64--glibc--stable-2022.08-1.tar.bz2
mkdir -p l4t-gcc
tar xf aarch64--glibc--stable-2022.08-1.tar.bz2 -C ./l4t-gcc
export ARCH=arm64
export CROSS_COMPILE=$(realpath .)/l4t-gcc/aarch64--glibc--stable-2022.08-1/bin/aarch64-buildroot-linux-gnu-
```

### 5. 编译 RT 内核、OOT 模块与 DTB

Seeed `source/nvbuild.sh` 支持 **`-r`** 启用 RT（内部调用 `./generic_rt_build.sh "enable"`，并自动设置 `IGNORE_PREEMPT_RT_PRESENCE=1` 编译 OOT 模块）：

```bash
cd source
./nvbuild.sh -r
./do_copy.sh
export INSTALL_MOD_PATH=$(realpath ../rootfs/)
./nvbuild.sh -r -i
cd ..
sudo ./tools/l4t_update_initrd.sh
```

等价于 NVIDIA 文档中的手动步骤（[Kernel Customization — RT](https://docs.nvidia.com/jetson/archives/r36.4.4/DeveloperGuide/SD/Kernel/KernelCustomization.html)）：

- `./generic_rt_build.sh "enable"`
- `make -C kernel` / `make install -C kernel`
- `export IGNORE_PREEMPT_RT_PRESENCE=1` 后 `make modules` / `make dtbs`

### 6. 刷机部署（推荐）

根据具体产品选择 **device name**（见 Wiki 列表）：

| 产品形态 | flash device name |
|----------|-------------------|
| reComputer J4012（Classic） | `recomputer-orin-j401` |
| reComputer Industrial J4012 | `recomputer-industrial-orin-j201` |
| reServer Industrial J4012 | `reserver-industrial-orin-j401` |
| reComputer Super J4012 | `recomputer-orin-super-j401` |

NVMe 示例（Classic J401）：

```bash
sudo ./tools/kernel_flash/l4t_initrd_flash.sh \
  --external-device nvme0n1p1 \
  -c tools/kernel_flash/flash_l4t_t234_nvme.xml \
  -p "-c bootloader/generic/cfg/flash_t234_qspi.xml" \
  --showlogs --network usb0 recomputer-orin-j401 internal
```

Industrial / reServer 其他刷机方式见对应 Getting Started Wiki。

### 7. 验证 RT 内核

刷机并重启后：

```bash
uname -a
# 期望内核版本字符串含 -rt，例如 5.15.xxx-rtYY-tegra

cat /sys/kernel/debug/preempt_rt/ 2>/dev/null || zgrep CONFIG_PREEMPT_RT /proc/config.gz
```

## 部署方式说明

### 推荐：Host 侧编译 + 刷机

- Seeed Wiki 与社区验证路径均为：在 host 构建完整 BSP 镜像后刷入设备。
- 可保留用户数据需自行评估；生产环境建议完整备份后刷机。

### 不推荐：NVIDIA RT APT OTA

- `deb https://repo.download.nvidia.com/jetson/rt-kernel r36.4 main` + `nvidia-l4t-rt-kernel` 面向 NVIDIA DevKit，**不适用于 Seeed J4012 载板**。

### 在运行系统上直接替换内核（未官方验证）

- 理论上可将编译产物（`Image`、DTB、`rootfs/lib/modules/`）复制到运行系统并更新 initrd，但 **Seeed 未提供 J4012 官方 in-place RT 升级文档**。
- 风险：模块版本不匹配、Seeed DTB 被覆盖、boot 分区/extlinux 配置错误导致无法启动。
- 若客户强需求 in-place，应明确告知为**自行承担风险**，并建议先备份镜像（`l4t_backup_restore.sh`）。

## 注意事项

1. **RT 内核为 Developer-Preview 质量**（NVIDIA 文档说明，Orin NX 在支持列表内）。
2. **UEFI runtime services** 可能增加延迟；RT 应用运行时不建议使用（NVIDIA RealTimeKernel 文档）。
3. 刷机/升级后 **避免无保护地 `sudo apt upgrade`**，以免 NVIDIA 官方内核包覆盖 Seeed 定制内核（参见 issue #41）。
4. 社区参考：[Seeed Forum — A603 RT kernel（JP 6.2 / R36.4.3）](https://forum.seeedstudio.com/t/how-to-install-a-real-time-kernel-for-the-a603-board/293292)（流程类似，device name 与 DTB 不同）。

## reComputer Industrial J4012 补充说明

- 典型运行环境：Ubuntu 22.04，内核 `5.15.148-tegra`（L4T R36.4.3 / JetPack 6.2）与本文档版本一致。
- Industrial J4012 刷机 device name：**`recomputer-industrial-orin-j201`**（与 J4011 等同配置文件前缀）。
- Industrial 刷机入口 Wiki：https://wiki.seeedstudio.com/reComputer_Industrial_Getting_Started/
- PoE、DI/DO、RS485、CAN 等工业接口依赖 Seeed DTB；必须使用 Seeed BSP 构建的 RT 内核，不可改用 NVIDIA DevKit RT APT 包。

## 售后需向客户确认

- 存储介质（eMMC / NVMe / SD）以调整刷机参数。
- 是否必须保留当前系统内用户数据（决定刷机 vs 备份策略）。
