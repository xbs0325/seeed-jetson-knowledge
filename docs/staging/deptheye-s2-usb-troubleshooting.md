---
status: staging
product: DepthEye S2
sku: "101990866"
topic: usb-enumeration-failure
confidence: need_review
---

# DepthEye S2 (101990866) — USB 无法识别 / Device Descriptor Request Failed

## 产品概要

| 项目 | 说明 |
|------|------|
| SKU | 101990866 |
| 名称 | DepthEye S2 VGA ToF Camera (Sony IMX556PLR) |
| 数据接口 | USB 3.1 Gen1 / Type-C |
| 供电 | **12V DC，峰值 1A / 平均 0.5A**（需外接适配器） |
| 盒内附件 | DepthEye S2 ×1、Type-C 数据线 ×1、电源线 ×1（**不含 12V 适配器**） |
| SDK / 工具 | [libDepthEye](https://github.com/pointcloudAI/libDepthEye)、[DepthEyeViewer](http://www.pointcloud.ai/doc/DepthEyeViewer_1.3.2_210807.exe.zip) |

## 典型现象

Windows Device Manager 出现：

- `Unknown USB Device (Device Descriptor Request Failed)` / `알 수 없는 USB 장치(장치 설명자 요청 실패)`
- 弹窗：USB device malfunctioned and Windows does not recognize it

表示主机在 USB **枚举**阶段未能读取有效 Device Descriptor，**早于** SDK/驱动安装阶段。

## 官方硬件连接要求

[libDepthEye README — Hardware Install](https://github.com/pointcloudAI/libDepthEye#0-hardware-install)：

> Please add one usb hub with Independent power supply. Then insert the double head USB cable together on the USB hub and connect the usb hub to your PC.

要点：

1. 连接 **12V 电源**（经盒内电源线）与 **USB 3.x 数据线**（盒内 Type-C 线）。
2. 推荐使用**带独立供电的 USB Hub**，再将 Hub 接至 PC。
3. Linux 需额外运行 udev 规则；**Windows 无单独 USB 驱动**，枚举成功后才安装/运行 DepthEyeViewer。

## 排查步骤（建议顺序）

### 1. 确认 12V 电源（最常见遗漏）

- 盒内**只有电源线，没有 12V 适配器**。
- 使用 **12V DC、≥1A**、极性与 barrel 接口匹配的 regulated 电源。
- 请客户提供适配器型号、输出电压/电流标签照片。

### 2. 连接与端口

- 先接 12V 电源，再接 USB（或同时连接）。
- 优先使用 PC **主板后置 USB 3.0/3.1** 口；避免仅测前面板口。
- 使用盒内原装 Type-C 线，确认非「仅充电」线。
- Hub 测试：Hub 独立电源已接通，Hub 上游线接 PC USB 3.0。

### 3. Windows 清理

1. 拔掉设备 → Device Manager → View → Show hidden devices。
2. 删除所有 Unknown USB Device / 带黄色叹号的 USB 条目。
3. Universal Serial Bus controllers → 卸载 USB Root Hub / xHCI Host Controller → 重启（Windows 会重装）。
4. 重新按步骤 1–2 连接。

### 4. 软件验证（枚举成功后）

- 下载 [libDepthEye](https://github.com/pointcloudAI/libDepthEye) 或 [DepthEyeViewer](http://www.pointcloud.ai/doc/DepthEyeViewer_1.3.2_210807.exe.zip)。
- Windows 无需 libDepthEye 中的 Linux udev 步骤。

### 5. 是否硬件不良 / RMA 条件

在以下**全部满足**仍无法枚举时，倾向硬件问题：

- 已确认 12V/1A 电源正确；
- 已测主板后置 USB 3.0 直连 + 带电源 Hub 两种方式；
- 已换 PC（建议第二台 Windows 或 Ubuntu）；
- 已使用盒内原装 USB 线。

## 置信度说明

| 结论 | 置信度 |
|------|--------|
| 产品型号与规格 | 已确认（商详 + 分销商页） |
| 盒内不含 12V 适配器 | 已确认（Core Electronics 等 Part List） |
| 当前个案为硬件不良 | **仍需人工确认**（缺 12V 适配器型号、第二 PC 测试结果） |

## 来源

- https://www.seeedstudio.com/DepthEye-S2-VGA-Resolution-ToF-Camera-p-5095.html
- https://core-electronics.com.au/deptheye-s2-h67-x-v51-vga-tof-camera-with-sony-imx556plr-depthsense.html
- https://github.com/pointcloudAI/libDepthEye
- https://learn.microsoft.com/en-us/answers/questions/5903639/unknown-usb-device-(device-descriptor-request-fail
