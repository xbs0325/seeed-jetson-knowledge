---
product: Jetson Orin Nano / reComputer J401 / Super / Robotics
vendor: seeed
platform: seeed_device
tags:
  - faq
  - accessory
  - ssd
  - nvme
  - orin-nano
date: 2026-08-14
source_url: https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
source_links:
  - https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
  - https://wiki.seeedstudio.com/recomputer_j401b_interfaces_usage/
  - https://wiki.seeedstudio.com/recomputer_jetson_super_hardware_interfaces_usage/
  - https://wiki.seeedstudio.com/recomputer_jetson_robotics_j401_getting_started/
  - https://developer.nvidia.com/embedded/learn/jetson-orin-nano-devkit-user-guide/hardware_spec.html
  - https://www.seeedstudio.com/M-2-2280-SSD-128GB-p-5332.html
  - https://www.seeedstudio.com/NVMe-M-2-2280-SSD-256GB-p-5333.html
  - https://www.seeedstudio.com/NVMe-M-2-2280-SSD-512GB-p-5334.html
  - https://www.seeedstudio.com/NVMe-M-2-2280-SSD-1TB-p-5767.html
  - https://www.seeedstudio.com/NVMe-M-2-2280-SSD-2TB-p-6265.html
status: active
---

* 问题
  * Orin Nano / Seeed reComputer（J401 / Super / Robotics 等）更换 SSD 时，应选用什么规格？Bazaar 对应型号是什么？
* 适用产品
  * Seeed reComputer Classic J401、J401B、Super、Robotics J401 等带 **M.2 Key M 2280** 的 Orin Nano/NX 载板产品
  * NVIDIA Jetson Orin Nano Developer Kit（参考：M.2 Key-M 2280 PCIe 3.0 x4；另有 Key-M 2230 PCIe 3.0 x2）
* 适用平台类型：seeed_device / official_kit
* 简洁答案
  * 请选用 **M.2 Key M、NVMe（PCIe）协议、2280 尺寸** 的固态硬盘；接口为 **PCIe Gen3 x4** 量级。
  * **不要**选用 M.2 SATA SSD（即使外形能插入 Key M，协议也不匹配）。
  * Seeed Wiki 官方列出的验证容量：128GB / 256GB / 512GB / 1TB / 2TB（NVMe M.2 PCIe Gen3x4 2280）。
* 推荐（Bazaar）

  | 容量 | SKU | 链接 |
  |------|-----|------|
  | 128GB | 112990226 | https://www.seeedstudio.com/M-2-2280-SSD-128GB-p-5332.html |
  | 256GB | 112990246 | https://www.seeedstudio.com/NVMe-M-2-2280-SSD-256GB-p-5333.html |
  | 512GB | 112990247 | https://www.seeedstudio.com/NVMe-M-2-2280-SSD-512GB-p-5334.html |
  | 1TB | 112990267 | https://www.seeedstudio.com/NVMe-M-2-2280-SSD-1TB-p-5767.html |
  | 2TB | 114993467 | https://www.seeedstudio.com/NVMe-M-2-2280-SSD-2TB-p-6265.html |

* 注意事项
  * 更换 SSD 后需重新刷写系统（SSD 上的系统不会自动恢复）。
  * 若客户买的是 **NVIDIA 官方 Orin Nano DevKit**，主槽为 2280；另有 2230 Key-M 槽，尺寸不同，勿混用。
  * PCIe Gen4 NVMe 通常可向下兼容，但速度会受限于 Gen3；优先选 Gen3x4 / 已验证型号更稳妥。
  * 库存与价格以 Bazaar 页面为准；本条目不承诺库存。
* 相关链接
  * [J401 Interfaces — Supported SSD](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/)
  * [NVIDIA Orin Nano DevKit Hardware Layout](https://developer.nvidia.com/embedded/learn/jetson-orin-nano-devkit-user-guide/hardware_spec.html)
