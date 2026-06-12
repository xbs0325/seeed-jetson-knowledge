# 工作流与内部约定

> 由对话沉淀；有变更时通过 PR 更新。

## 淘宝 / 天猫标题辨析（搜索优化导致的歧义）

店铺为提高搜索排名，标题常堆砌「官方」「开发套件」「Super」等词，**不能按字面理解成 NVIDIA 官方 Developer Kit**。

### 典型标题

例：`Jetson Orin NX 16G Super官方核心模组 开发套件 主板Ai人工智能`

### 正确理解

| 标题片段 | 实际含义 |
| --- | --- |
| **官方核心模组** | NVIDIA 正品 Jetson 模组（Orin NX 16GB 等） |
| **开发套件 / 主板** | **Seeed 载板 + 套件**（reComputer / Super 等），不是 NVIDIA 整机官方 DevKit |
| **Super** | 常指 reComputer **Super** 系列 + JetPack 6.2 **Super/MAXN** 模式 |

合起来：**官方（NVIDIA）模组 + Seeed 开发套件 = Seeed 产品**。

### 与真正「NVIDIA 官方套件」的区别

| 类型 | 含义 | 刷机 |
| --- | --- | --- |
| **NVIDIA 官方 Developer Kit** | NVIDIA 整机参考套件（如 Orin Nano Super DevKit、AGX Orin DevKit） | NVIDIA SDK Manager / 官方 User Guide |
| **Seeed「官方核心模组」套件** | Seeed 载板 + NVIDIA 模组 | **Seeed Wiki / mfi / Linux_for_Tegra** |
| **第三方载板套件**（微雪等） | 合作商载板 + NVIDIA 模组 | 载板商 Wiki + NVIDIA L4T（如 `jetson-orin-nano-devkit-super`） |

### 客服快速判断

1. 标题含「官方核心模组」+「开发套件」→ **先按 Seeed 产品核对**，不要直接给 NVIDIA 官方 DevKit 链接。
2. 「Orin NX 16G Super」→ 优先核对 **reComputer Super J4012**。
3. 仍不确定 → 要买家发：**店铺链接、商品 SKU、外壳铭牌、Recovery 时 `lsusb`**。
4. 只有明确为 **NVIDIA 原厂 Developer Kit 包装盒/型号** 时，才走 NVIDIA 官方刷机文档。

### 相关 Wiki（Seeed J401 / Super）

- reComputer Classic J401 刷机：https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/
- reComputer Super：https://wiki.seeedstudio.com/recomputer_jetson_super_getting_started/
- 按产品选镜像：https://wiki.seeedstudio.com/flash/jetpack_to_selected_product/
