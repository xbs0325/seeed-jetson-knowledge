---
product: reComputer mini J4012 and Orin-based reComputers
vendor: seeed
platform: seeed_device
jetpack: "5.1.3 -> 6.2"
l4t: "35.5.0 -> 36.4.3"
tags:
  - ota
  - flashing
  - bsp
  - recomputer
  - maxn
date: 2026-06-11
source_url: https://wiki.seeedstudio.com/deploy_ota_on_recomputer/
status: active
---

# Seeed reComputer：JetPack 5.1.3 到 6.2 OTA 更新

## 适用范围

- Seeed Wiki 演示平台：reComputer mini J4012，JetPack 5.1.3 -> JetPack 6.2。
- Seeed 页面说明其他 Orin-based reComputers 可参考同一逻辑，但必须把 board name 替换为匹配自身载板的 `.conf` 名称。
- 适用平台类型：`seeed_device`。

## 关键结论

- Seeed 提供 reComputer mini 系列的 ready-to-use OTA payload：`ota_payload_package.tar.gz`，用于 JP5.1.3 -> JP6.2。
- 页面给出的 payload SHA256：`3da8fd97c450f4f7bd83390ab50f951dffd5ec1d43c39a1e6156b4806f7df7c6`。
- 设备端 OTA 前需安装 `efibootmgr` 和 `nvme-cli`，下载 NVIDIA OTA tools，并按需编辑 `ota_backup_files_list.txt` 保留用户文件。
- 升级完成后可用以下命令核对启动链、NVMe 和 L4T 版本：

```bash
nvbootctrl -t
sudo nvme list
cat /etc/nv_tegra_release
```

- Seeed 页面要求升级后应看到 `R36 (release), REVISION: 4.3`，对应 JetPack 6.2 / L4T 36.4.3。

## 自制 OTA 包要点

- Seeed 的可选流程使用 NVIDIA JetPack 6.2 packages 作为 target BSP，并叠加 Seeed `Linux_for_Tegra` r36.4.3 定制内容。
- Base BSP 使用 JetPack 5.1.3 / L4T 35.5.0，并叠加 Seeed r35.5.0 定制内容。
- 生成 OTA 包时，`target_board name` 必须使用匹配设备的 Seeed board name；示例为 `recomputer-orin-j40mini`。

## MAXN Super 注意事项

- Seeed Wiki 明确警告：reComputer mini 使用 Orin NX 16GB/8GB 模组时，不要启用 MAXN SUPER mode。
- 原因是 reComputer mini 散热能力不足，强行启用可能导致模块永久损坏。

## 售后提示

客户询问“能不能远程把 reComputer 从 JP5.1.3 升到 JP6.2”时，可说明 Seeed 已提供 reComputer mini J4012 的 OTA 示例和 payload；其他 Orin-based reComputer 需要核对具体型号、board name、当前系统版本和 Seeed 是否提供对应 payload，不要直接套用 NVIDIA 官方开发套件 OTA 流程。
