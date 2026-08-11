---
product: Seeed Jetson devices / Jetson developer kits using a Linux host as gateway
vendor: seeed
platform: common
jetpack: common
tags:
  - ethernet
  - network-sharing
  - ubuntu-24.04
  - networkmanager
  - nat
  - wifi
  - j4012
date: 2026-08-11
source_links:
  - https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/
  - https://documentation.ubuntu.com/core/explanation/system-snaps/network-manager/how-to-guides/configure-shared-connections/
  - https://forums.developer.nvidia.com/t/unable-to-connect-to-internet-in-jetson-nano-using-ethernet-protocol-host-device-as-internet-gateway/77666
status: active
---

# Ubuntu 24.04 主机通过网线给 Jetson 共享网络：优先用 NetworkManager 共享，不要做 bridge

## 适用范围

- 客户的 **Ubuntu 24.04 PC** 已通过 **Wi-Fi** 上网。
- 客户希望把这台 PC 的网络通过 **以太网口** 共享给 Jetson（例如 reComputer J4012）。
- Jetson 与主机为点对点网线连接，或通过一个简单交换网络连接。

## 结论摘要

| 问题 | 结论 |
|------|------|
| Ubuntu 24.04 上“Shared to other computers”是什么？ | 是 **NetworkManager 的共享/NAT 模式**，不是二层 bridge。 |
| Jetson 侧 IP 应该怎么设？ | **优先保持 Automatic (DHCP)**。不要先手动固定到无关网段。 |
| Host 侧共享成功后，Jetson 常见会拿到什么？ | Jetson 会从 host 侧 DHCP 获得一个私网地址；host 同时充当 **gateway + DNS/NAT**。 |
| 如果 Jetson 能拿到 IP 但不能上网，先查什么？ | **host 防火墙 / 转发规则**、Jetson 默认路由、DNS。 |
| 是否推荐把 Wi-Fi 和有线口做 bridge？ | **不推荐作为首选**。多数客户场景应先用 NetworkManager 共享模式。 |

## 事实

- reComputer J4012 载板官方资料明确包含 **1x Gigabit Ethernet**，并将其作为标准网络接口之一。
- Seeed J401 载板 Wiki 中，无线扩展的官方建议路径主要是 **M.2 Key E Wi‑Fi/Bluetooth 模块**；对于 USB Wi‑Fi 芯片驱动问题，不宜承诺官方专用补丁。
- Canonical 的 NetworkManager 文档说明：`ipv4.method shared` 会在共享接口上启动 DHCP，并启用转发与 masquerading（NAT）。
- NVIDIA 社区案例中，Jetson 通过 host 做网关时，若链路可 ping 通 host 但不能访问外网，重点通常落在 **host 转发/NAT** 或 **Jetson 默认路由/DNS**，而不是 Jetson 以太网口本身。

## 推断

- 客户在 host 上已尝试 “Shared to other computers” 但 Jetson 仍不能上网，**更像是 host 侧共享未完全生效**（例如防火墙拦截、共享连接没有真正起效），而不是 J4012 网口不支持。
- 客户提到尝试手动设 `192.168.1.100`、link-local only 等做法，说明现场可能混用了 **共享/NAT**、**静态地址** 与 **链路本地** 配置，容易导致默认网关和 DNS 不一致。

## 建议（给客户的低风险步骤）

### 1. 先把主机侧恢复到最简共享模式

在 Ubuntu 24.04 host 上：

1. 确认 **Wi‑Fi 已正常上网**。
2. 打开有线连接设置，把 **IPv4 Method** 设为 **Shared to other computers**。
3. 不要把同一个有线连接同时再手动填静态 gateway / DNS。
4. 断开并重新连接网线，或重新启用该有线连接。

如果客户愿意走命令行，可给出等价思路（接口名需按实际替换）：

```bash
nmcli connection add type ethernet con-name jetson-share ifname <host-ethernet-iface> ipv4.method shared ipv6.method ignore
nmcli connection up jetson-share
```

### 2. Jetson 侧先保持自动获取，不要先手动写死

在 Jetson 上：

- 有线连接 **IPv4 = Automatic (DHCP)**。
- 不要先设 `192.168.1.100` 之类固定地址，除非已经确认 host 共享出来的网段就是该网段。
- 不要使用 **Link-local only** 作为上网方案；它通常只能形成本地链路，不能直接提供 Internet。

### 3. 先做三步最小验证

在 Jetson 上执行：

```bash
ip addr
ip route
ping -c 4 8.8.8.8
```

判断方式：

- **拿不到 DHCP 地址**：优先看 host 侧共享是否真的启动。
- **能 ping host，但不能 ping 8.8.8.8**：优先看 host 防火墙 / NAT / IP forwarding。
- **能 ping 8.8.8.8，但域名不通**：优先看 DNS。

### 4. 若共享模式已开但仍不通，重点检查 host 防火墙

Ubuntu 上若开启了 UFW 或其他防火墙，可能出现：

- Jetson 能获得本地 IP；
- Jetson 与 host 可以互 ping / SSH；
- 但 Jetson 无法访问公网。

此时应让客户重点核对 **host 防火墙是否拦截转发/NAT**，而不是继续在 Jetson 上反复改静态 IP。

## 可直接给客户的排查信息请求

如果还需要客户补充日志，优先只要这几项：

1. Ubuntu host 上：

```bash
nmcli connection show
ip addr
ip route
sudo ufw status
```

2. Jetson 上：

```bash
ip addr
ip route
ping -c 4 <host-ethernet-ip>
ping -c 4 8.8.8.8
```

## 客户可发口径（英文思路）

- Host Wi‑Fi to Jetson Ethernet on Ubuntu 24.04 should normally use **NetworkManager sharing/NAT**, not a bridge.
- On the Jetson side, please leave IPv4 on **Automatic (DHCP)** first.
- If the Jetson gets a local IP but still cannot reach the Internet, the next checks should be the **host firewall**, **default route**, and **DNS**, rather than more manual IP changes on the Jetson.

## 禁止 / 风险提示

- **不要**对客户承诺 Seeed 提供 RTL8188EU 的官方 Jetson 驱动补丁。
- **不要**把“Shared to other computers”解释成 bridge。
- **不要**在未确认 host 网段前，建议客户把 Jetson 手动固定到任意 `192.168.x.x`。
- **不要**把 `link-local only` 当作稳定外网接入方案。
