---
status: staging
product: Jetson AGX Thor / reComputer Robotics J601 / J501
topic: product-selection-usb-1gbe
confidence: need_review
---

# Jetson Thor 询价与 USB + 1GbE 选型（J601 / J501 / 官方 Dev Kit）

## 背景

客户（Ruhr-Universität Bochum）咨询 Jetson Thor，约束条件：

- **仅 USB 与 Ethernet 有需求**（GMSL/CAN 等不适用）
- 夹爪（gripper）需要 **1Gb Ethernet**，10GbE 等可能不被支持
- 询问报价、SDK Manager、是否有外壳（case）

## 产品对比（待 J601 最终规格确认）

| 产品 | 状态 | USB | 以太网 | 外壳/机箱 | 软件安装 |
|------|------|-----|--------|-----------|----------|
| [NVIDIA Jetson AGX Thor Developer Kit](https://www.seeedstudio.com/NVIDIA-Jetson-AGX-Thor-Developer-Kit-p-9965.html) (SKU **100060965**) | 现货 | 2× USB-A 3.2 + 2× USB-C 3.1 | 1× **5GbE** RJ45（多速率，含 1G 协商）+ QSFP28 | **含** 参考载板与外壳 | JetPack 7：**ISO 安装为主**；SDK Manager / L4T flash 为备选 |
| [reComputer Robotics J601](https://wiki.seeedstudio.com/ai_robotics_recomputer_robotics_j601_carrier_board_getting_started/) | **即将推出，规格未定** | 最多 4× USB 3.2 Type-A | 初步规划 **高速 RJ45（含 10GbE）**，**1GbE 未确认** | 载板与风扇**分开销售**，无完整机箱说明 | JetPack 7，刷机/BSP **TBD** |
| [reComputer Robotics J501](https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/) | 现货 | 3× USB 3.0 Type-A + USB-C | 1× 10GbE（支持 10/5/2.5/**1**/0.1G）+ **4× 1GbE** | 散热方案，非 Thor 级封闭机箱 | 预装 JetPack 6.2.1，Seeed BSP / initrd flash |
| [reComputer Robotics J501 Mini](https://wiki.seeedstudio.com/recomputer_j501_mini_getting_started/) | 现货 | 2× USB 3.2 Type-A + USB-C | 1× 10GbE + **1× 1GbE** | 紧凑载板 | JetPack 6.2.1，Seeed BSP |
| [reComputer Robotics J401](https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/) | 现货 | **6× USB 3.2** Type-A | **2× 1GbE** | 载板 | JetPack 6.2，Seeed BSP |

## 内部建议摘要

1. **报价**：技术支持不出报价 → 转 **order@seeed.io / 销售**，注明德国高校、数量、SKU、是否需要形式发票。
2. **Thor Dev Kit 官网限购**：商详标注 **Maximum purchase per account: 1pcs**；批量/高校采购需销售通道。
3. **1GbE 夹爪**：若夹爪**仅支持标准 1GbE**：
   - **J501 / J501 Mini** 有专用 1GbE 口，但为 **AGX Orin** 非 Thor。
   - **Thor Dev Kit** 的 5GbE 口通常可协商至 1G，**需客户与夹爪厂商确认**。
   - **J601** 目前 Wiki 仅提高速以太网，**不能承诺**有 1GbE 口；且 Zibo 邮件中的「4× 10GbE」与 Thomas 需求可能不匹配。
4. **SDK Manager**：
   - **官方 Thor Dev Kit**：NVIDIA 文档以 **Jetson ISO** 自助安装为主；SDK Manager 为需 Ubuntu Host 的替代方案。
   - **Seeed J501/J601 等**：使用 **Seeed 镜像 + BSP**，非 SDK Manager 刷官方 Dev Kit 镜像。
5. **Case/外壳**：
   - Thor Dev Kit：**含** NVIDIA 参考外壳。
   - J601：**仅载板**，无完整 case 说明。

## 置信度

| 项 | 级别 |
|----|------|
| Thor Dev Kit 接口与 ISO 安装 | 已确认（NVIDIA User Guide） |
| J501 1GbE + USB 规格 | 已确认（Seeed Wiki） |
| J601 最终以太网端口速率与 1GbE 支持 | **待确认**（Wiki 标注 preliminary draft） |
| 夹爪与 5GbE 口协商 1G 兼容性 | **需客户与夹爪厂商确认** |

## 来源

- https://www.seeedstudio.com/NVIDIA-Jetson-AGX-Thor-Developer-Kit-p-9965.html
- https://wiki.seeedstudio.com/ai_robotics_recomputer_robotics_j601_carrier_board_getting_started/
- https://wiki.seeedstudio.com/ai_robotics_recomputer_j501_robotics_getting_started/
- https://docs.nvidia.com/jetson/agx-thor-devkit/user-guide/latest/quick_start.html
- https://docs.nvidia.com/jetson/agx-thor-devkit/user-guide/0.1.0/hardware_layout.html
