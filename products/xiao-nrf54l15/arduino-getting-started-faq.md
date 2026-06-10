---
product: "Seeed Studio XIAO nRF54L15 / XIAO nRF54L15 Sense"
platform: "Seeed Studio Wiki"
tags:
  - XIAO
  - nRF54L15
  - Arduino
  - pinout
  - setup
  - ecommerce-support
date: 2026-06-10
source_url: "https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/"
---

# XIAO nRF54L15 Arduino 入门与常见问题 FAQ

## 适用范围

适用于 Seeed Studio XIAO nRF54L15 与 XIAO nRF54L15 Sense 的 Arduino 开发咨询，覆盖 Boards Manager 配置、GPIO/UART/I2C/SPI 接线、上传报错和买家常见兼容性问题。

## FAQ

### 问题：Arduino IDE 如何添加 XIAO nRF54L15 支持？

**简洁答案：** 在 Arduino IDE 的 File -> Preferences 中，将以下地址加入 Additional Boards Manager URLs，然后在 Boards Manager 中安装并选择 XIAO nRF54L15 / Sense：

```text
https://raw.githubusercontent.com/lolren/nrf54-arduino-core/main/package_nrf54l15clean_index.json
```

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - Getting Started](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

### 问题：买家第一次测试应该烧录什么程序？

**简洁答案：** 建议先烧录 Blink 例程验证开发板、USB 数据线、端口和板卡包均正常。若 LED 能按 500 ms 间隔闪烁，说明基础上传链路正常。

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - Upload the program](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

### 问题：数字引脚和模拟引脚在 Arduino 中怎么写？

**简洁答案：** 官方 Arduino 适配中 D0 到 D10 重新定义为 `PIN_D0` 到 `PIN_D10`；模拟输入 A0 到 A3 定义为 `PIN_A0` 到 `PIN_A3`。读取模拟电压时可使用 12-bit ADC，按 3.3V 参考电压换算。

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - Digital](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)
- [Arduino for Seeed Studio XIAO nRF54L15 - Analog](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

### 问题：UART 使用 D6/D7 时要注意什么？

**简洁答案：** D6/D7 对应 UART 的 TX/RX，可通过 `Serial1` 或 `Serial2` 使用。不要把 `PIN_SERIAL1_RX` 和 `PIN_SERIAL1_TX` 当作 USB `Serial` 使用，否则可能影响默认下载和调试通道，导致刷写失败或 SWD/CDC 异常。

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - UART](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

### 问题：I2C 接 OLED 或 Grove 扩展板时用哪些引脚？

**简洁答案：** XIAO nRF54L15 的 D4/D5 分别作为 SCL/SDA，在 Arduino 适配中对应 `PIN_WIRE_SCL` 和 `PIN_WIRE_SDA`。建议先用 Expansion Board Base for XIAO 的 OLED 示例验证 I2C 是否正常。

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - I2C](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

### 问题：Windows 上传时报没有 `py` 路径怎么办？

**简洁答案：** 按官方 FAQ，找到 Arduino15 包目录下的 `platform.txt`，将 `tools.python3.cmd.windows=py` 改为 `tools.python3.cmd.windows=python`，并将 `tools.python3.args.windows=-3` 改为空值。

**相关链接：**
- [Arduino for Seeed Studio XIAO nRF54L15 - FAQ](https://wiki.seeedstudio.com/xiao_nrf54l15_sense_arduino/)

## 电商客服提示

- 售前确认买家需要普通版还是 Sense 版，是否需要板载传感器。
- 售后上传失败优先确认 USB 线是否支持数据、板卡包 URL 是否添加、是否选对板型和端口。
- 接线类问题建议买家先用官方示例逐项验证 GPIO、UART、I2C、SPI，避免一次接入多个外设难以定位。
