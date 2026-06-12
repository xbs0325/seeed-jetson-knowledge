# 常见误区速查

> 由对话沉淀；技术事实条目见 `docs/faq/`。

## 电商标题

- ❌ 把「**官方核心模组 开发套件**」当成 **NVIDIA 官方 Developer Kit**
- ✅ 多数是 **NVIDIA 模组 + Seeed 载板套件**（如 reComputer Super J4012）

## 刷机包

- ❌ Seeed reComputer 客户使用 NVIDIA 官方 `jetson-orin-nano-devkit` 或第三方微雪教程
- ❌ Seeed Classic J401 与 Super J4012 **混用**刷机包 / 板级名（`recomputer-orin-j401` vs Super `mfi`）
- ✅ 先确认 **Classic / Super / Industrial** 再选 Wiki 与 mfi 包

## 设备名参数

- `--external-device nvme0n1p1`：外置 NVMe 分区名
- `recomputer-orin-j401`（Classic）/ `recomputer-orin-super-j401`（Super）/ `jetson-orin-nano-devkit-super`（NVIDIA DevKit）：**板级名不可混用**
- `internal` / `external`：启动链模式，不是产品型号
