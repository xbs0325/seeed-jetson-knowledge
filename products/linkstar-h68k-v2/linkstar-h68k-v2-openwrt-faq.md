---
product: LinkStar-H68K-1432 V2
platform: Seeed Studio Wiki
tags:
  - linkstar
  - h68k-v2
  - openwrt
  - router
  - ethernet
  - docker
  - troubleshooting
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/h68kv2_datasheet/
---

# LinkStar-H68K-1432 V2 OpenWrt、接口与系统安装 FAQ

## 适用场景

适合电商客服解答 LinkStar-H68K-1432 V2 路由器的接口、默认系统、后台登录、OpenWrt/Armbian 安装和网络口用途问题。

## FAQ

### 问题：LinkStar-H68K-1432 V2 的核心规格是什么？

简洁答案：采用 Rockchip RK3568 四核 Cortex-A55 平台，配备 4 个以太网口（双 2.5G + 双 1G）、Wi-Fi 6、较高容量存储和媒体播放能力。官方商品页 SKU 为 102110958，推荐室内使用。

相关链接：

- https://wiki.seeedstudio.com/h68kv2_datasheet/
- https://www.seeedstudio.com/LinkStar-H68K-1432-V2-p-5886.html

### 问题：收货后可以直接使用 OpenWrt 吗？

简洁答案：可以。官方 Wiki 说明 LinkStar-H68K-V2 预装 OpenWrt，收到后可直接上电使用。OpenWrt R22.11.18 版本说明中包含 Docker 支持。

相关链接：

- https://wiki.seeedstudio.com/h68kv2_datasheet/
- https://wiki.seeedstudio.com/H68KV2_install_system/

### 问题：默认后台地址、账号和密码是什么？

简洁答案：将电脑网线接到 ETH1/ETH2/ETH3 任一 LAN 口，在浏览器访问 `192.168.100.1`。默认账号为 `root`，默认密码为 `password`。ETH0 是 WAN 口，不建议用于首次进入后台。

相关链接：

- https://wiki.seeedstudio.com/h68kv2_datasheet/

### 问题：各网口如何区分？

简洁答案：官方快速开始中将 ETH0 作为 WAN 口，ETH1/ETH2/ETH3 作为 LAN 口。硬件概览中 ETH0/ETH1 为 1G 以太网，ETH2/ETH3 支持 2.5G/1G 以太网。

相关链接：

- https://wiki.seeedstudio.com/h68kv2_datasheet/

### 问题：支持哪些系统？如何安装？

简洁答案：LinkStar-H68K-V2 支持 OpenWrt、Armbian 等系统。TF 卡方式因读写速度和稳定性限制，官方文档仅用于 OpenWrt；刷入 eMMC 可用于 LinkStar-V2 当前支持的系统。刷机常用 balenaEtcher、USB-C 数据线、TF 卡/读卡器或 eMMC 刷写工具。

相关链接：

- https://wiki.seeedstudio.com/H68KV2_install_system/

### 问题：无法进入 OpenWrt 后台时怎么排查？

简洁答案：确认电脑连接的是 ETH1/ETH2/ETH3 LAN 口而不是 ETH0；确认设备已通过支持 CC 线 PD 快充的 Type-C 电源适配器供电；电脑网卡可设置为自动获取 IP，再访问 `192.168.100.1`。

相关链接：

- https://wiki.seeedstudio.com/h68kv2_datasheet/

