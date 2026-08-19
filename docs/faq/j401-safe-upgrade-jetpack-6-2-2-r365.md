---
product: Seeed J401 全系（Classic / Mini / Super / Industrial / reServer J401）
vendor: seeed
platform: seeed_device
jetpack: "6.2 / 6.2.1 / 6.2.2"
l4t: "36.4.x / 36.5.0"
tags:
  - faq
  - apt
  - bsp
  - ota
  - j401
  - upgrade
date: 2026-08-12
source_links:
  - https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0
  - https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41
  - https://github.com/Seeed-Projects/Seeed-Jetson-DevelopTool
  - https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471
  - https://developer.nvidia.com/embedded/jetpack-sdk-622
status: active
---

# J401 全系：JetPack 6.2 → 6.2.2（L4T R36.5）安全升级

## 适用范围

- Seeed **J401 全系**载板/整机：Classic、Mini、Super、Industrial、reServer J401 等使用 Seeed 定制 BSP 的 Jetson Orin 设备。
- 升级路径：**L4T R36.x（低于 R36.5）→ L4T R36.5.0 / JetPack 6.2.2**，同属 R36 大版本内小版本升级。
- **不适用**：
  - NVIDIA 官方 Developer Kit 裸机（应走 NVIDIA 官方 APT 流程）。
  - 跨大版本（如 R35 → R36、JP6 → JP7）：应完整刷机或走 DevelopTool 中已列出的跨版本 OTA 路径，**不是**本文路径。
  - 已在 R36.5.0 的设备重复升级、或降级。

## 事实

- 在 Seeed 定制 BSP 设备上，**未做保护地执行 `sudo apt upgrade`** 可能拉取 NVIDIA 官方 L4T 包，覆盖 Seeed 定制内核/DTB/bootloader，导致无法启动或板级功能异常（[Linux_for_Tegra issue #41](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)）。
- Seeed 已于 **2026-05-26** 发布 [Linux_for_Tegra r36.5.0](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0)，提供：
  - `seeed-linux-bsp-upgrader_*.deb`：设备端 apt hook + 前台 wrapper；
  - `seeed-jetson-linux-r36.5.0-upgrade-bundle.tar.gz`：Seeed 定制 L4T 升级包。
- 正确流程是：**先安装 upgrader hook → 将 NVIDIA apt 源切到 r36.5 → 再 `sudo apt upgrade`**；hook 会拦截并改为安装 Seeed 定制包，而不是裸升官方 BSP。
- 2026-06 论坛仍有用户按「千万别 upgrade」理解 JP6.2→6.2.2，或误用 NVIDIA 官方 DevKit 的 `apt upgrade` 口径（[论坛帖](https://forum.seeedstudio.com/t/nvidia-has-officially-announced-jetpack-7-2-june-1-2026-any-plans-for-j401-agx-orin-32gb-support/295471)）。Seeed 设备**不是**「完全不能 upgrade」，而是**不能裸 upgrade**。
- [Seeed Jetson Developer Tool](https://github.com/Seeed-Projects/Seeed-Jetson-DevelopTool) 提供 **OTA Update** 引导式工作流（选产品 → SSH 连接 → 识别当前版本 → 匹配可用升级路径 → 执行并重启）。相比在各 J 系列 Flash/升级 Wiki 分散粘贴长命令，**更适合作为售后首推入口**。
- DevelopTool 客户端界面列出的 OTA 路径以运行时元数据为准；若某 J401 变体尚未显示 JP6.2→6.2.2 路径，可暂用手动 upgrader SOP（见下）。

## 推断

- 论坛「6.2.2 不知怎么做 / 只能禁止 upgrade」类反馈，主因是 **r36.5.0 upgrader 与 DevelopTool OTA 入口推广不足**，而非缺少技术方案。
- 不建议依赖「逐条 Wiki 全产品线手动命令」作为默认交付：覆盖面大、步骤多、易漏 bootloader 双 slot 同步，售后返工风险高。

## 建议

### 首选：Seeed Jetson Developer Tool → OTA Update

1. 在 PC 安装并打开 DevelopTool：`pip install seeed-jetson-developer` → `seeed-jetson-developer`。
2. 在 **Remote Connection** 通过 SSH 连接 Jetson（需网络可达）。
3. 打开 **OTA Update**，选择对应 J401 产品型号。
4. 工具识别当前 JetPack/L4T 后，若列表中有 **JP 6.2 / 6.2.1 → 6.2.2（R36.5）** 路径，按四步向导完成下载、校验、传输、执行与重启。
5. 升级完成后用 `cat /etc/nv_tegra_release`、`uname -r` 核对为 R36.5.0。

**售后话术要点**：不是「禁止 upgrade」，而是「请用 DevelopTool OTA 或 Seeed 官方安全升级流程，不要直接裸跑 `sudo apt upgrade`」。

### 备选：设备端手动安装 seeed-linux-bsp-upgrader（高级 / 无 GUI 环境）

适用于无法使用 DevelopTool、或客户端尚未列出对应 OTA 路径时。完整步骤以 [GitHub Release r36.5.0](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0) 为准，核心如下：

```bash
# 1) 下载并校验 upgrader deb
wget https://github.com/Seeed-Studio/Linux_for_Tegra/releases/download/r36.5.0/seeed-linux-bsp-upgrader_36.5.0-202605290010_all.deb
wget https://github.com/Seeed-Studio/Linux_for_Tegra/releases/download/r36.5.0/seeed-linux-bsp-upgrader_36.5.0-202605290010_all.deb.sha256
sha256sum -c seeed-linux-bsp-upgrader_36.5.0-202605290010_all.deb.sha256

# 2) 安装 hook
sudo dpkg -i seeed-linux-bsp-upgrader_36.5.0-202605290010_all.deb

# 3) 将 NVIDIA L4T apt 源指向 r36.5
sudo sed -i 's/r36\.[0-9]\+/r36.5/g' /etc/apt/sources.list.d/nvidia-l4t-apt-source.list

# 4) 刷新并触发 Seeed 安全升级（保持终端直到完成并重启）
sudo apt update
sudo apt upgrade
```

首次 reboot 后，Release 说明建议**再执行一次 Seeed 定制 bootloader deb 安装以同步双 slot**，然后二次 reboot 并验证（详见 Release 页 Verification 段）。

也可不装 hook、直接解压 `seeed-jetson-linux-r36.5.0-upgrade-bundle.tar.gz` 运行 bundle 内脚本（Release 中 “Manual upgrade without apt hook”），但仍需完成 bootloader slot 同步。

### 升级前确认

- 当前为 Seeed 官方 JP6.2 / 6.2.1 镜像（`cat /etc/nv_tegra_release` 显示 R36.4.x 等）。
- 磁盘空间充足；升级过程勿断电。
- 重要数据先备份。

## 禁止

- **禁止**在 Seeed J401 设备上直接照搬 NVIDIA 官方 DevKit 的 `apt dist-upgrade` / 裸 `sudo apt upgrade`（未安装 seeed-linux-bsp-upgrader 前）。
- **禁止**对论坛/客户只说「千万别 apt upgrade」而不给出 DevelopTool OTA 或 r36.5.0 upgrader 链接。
- **禁止**把 JP6→JP7 跨大版本升级与本文 JP6.2→6.2.2 小版本路径混用。
- **禁止**承诺所有 J401 变体在 DevelopTool 中已显示 OTA 路径；以客户端实际列表为准，未列出时走 Release 手动 SOP。

## 客服可复制回复

**英文邮件（简版）**

> For Seeed J401 carrier boards on JetPack 6.2 / 6.2.1, please do **not** run a plain `sudo apt upgrade` to reach JetPack 6.2.2 — that can overwrite Seeed’s customized BSP. The recommended path is the **OTA Update** workflow in **Seeed Jetson Developer Tool** (connect over SSH, select your J401 model, and follow the guided upgrade if JP 6.2 → 6.2.2 is listed). If the path is not shown in your client version, use Seeed’s **seeed-linux-bsp-upgrader** package from the [Linux_for_Tegra r36.5.0 release](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0), then run `apt upgrade` as documented there.

**中文（论坛/内部）**

> J401 升到 6.2.2 不是不能 upgrade，而是不能**裸** `sudo apt upgrade`。优先用 **Seeed Jetson Developer Tool** 里 **OTA Update** 引导升级；若没有对应路径，按 GitHub [r36.5.0 Release](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0) 先装 `seeed-linux-bsp-upgrader` 再 upgrade。

## 相关链接

- [Linux_for_Tegra r36.5.0 Release（upgrader + bundle）](https://github.com/Seeed-Studio/Linux_for_Tegra/releases/tag/r36.5.0)
- [Seeed Jetson Developer Tool](https://github.com/Seeed-Projects/Seeed-Jetson-DevelopTool)
- [Linux_for_Tegra issue #41（apt upgrade 冲突背景）](https://github.com/Seeed-Studio/Linux_for_Tegra/issues/41)
- [NVIDIA JetPack 6.2.2 页面（官方 DevKit 背景）](https://developer.nvidia.com/embedded/jetpack-sdk-622)
- [JP 6.2.2 官方发布要点（本仓库）](../official_kit/common/jetpack-6-2-2-l4t-r36-5-release.md)
- [装浏览器 vs apt upgrade（本仓库）](seeed-jetson-install-browser-vs-apt-upgrade.md)
