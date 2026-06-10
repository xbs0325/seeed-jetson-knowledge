---
product: Seeed Studio XIAO ESP32C6
platform: Seeed Studio Wiki
tags:
  - xiao
  - esp32c6
  - specs
  - pinout
  - arduino
  - matter
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/
---

# Seeed Studio XIAO ESP32C6 规格、引脚与入门 FAQ

## 适用场景

适合淘宝/天猫客服解答买家关于 XIAO ESP32C6 的无线能力、供电、引脚、Arduino 入门和外设连接问题。

## FAQ

### 问题：XIAO ESP32C6 支持哪些无线协议？

简洁答案：支持 2.4GHz Wi-Fi 6、Bluetooth 5.x LE、Zigbee、Thread / IEEE 802.15.4，适合 Matter 智能家居项目和低功耗 IoT 设备。

相关链接：

- https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/
- https://circuitpython.org/board/seeed_xiao_esp32c6/

### 问题：这块板子的核心规格是什么？

简洁答案：ESP32-C6 SoC，双 32-bit RISC-V 处理器；高性能核心最高 160MHz，低功耗核心最高 20MHz；片上 512KB SRAM 和 4MB Flash。尺寸为 XIAO 系列的小尺寸板型，适合空间受限项目。

相关链接：

- https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/
### 问题：Type-C 和电池供电分别是多少电压？

简洁答案：Type-C 输入为 5V；电池输入为 3.7V。3V3 引脚是板载稳压输出，官方引脚说明中标注可输出约 700mA。外部电源接 5V 引脚时应按官方说明加入二极管隔离，避免反灌。

相关链接：

- https://wiki.seeedstudio.com/xiao_pin_multiplexing_esp32c6/

### 问题：常用 UART、I2C、SPI 引脚怎么接？

简洁答案：UART 常用 D6(TX)、D7(RX)；I2C 常用 D4(SDA)、D5(SCL)；SPI 常用 D8(SCK)、D9(MISO)、D10(MOSI)，片选 CS 可按项目选择普通 GPIO，例如 D3。

相关链接：

- https://wiki.seeedstudio.com/xiao_pin_multiplexing_esp32c6/

### 问题：Arduino IDE 如何选择开发板？

简洁答案：按官方入门文档安装 Arduino IDE 和 ESP32 板卡支持包后，添加/选择 XIAO ESP32C6 对应板卡，再运行 Blink 示例验证上传。若上传失败，优先检查 Type-C 数据线是否支持数据传输，并尝试按 BOOT/RESET 进入下载模式。

相关链接：

- https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/
