---
channel: email
reply_to: customer
product: reComputer J4012 (Jetson Orin NX) + Ubuntu 24.04 host internet sharing
issue_type: compatibility
confidence: confirmed
final_customer_reply: true
date: 2026-08-11
---

# 英文邮件：RTL8188EU 不稳定后的临时联网方案（Ubuntu 24.04 host 通过 Ethernet 共享网络给 J4012）

## 客户问题

客户使用 **reComputer J4012**（JetPack 7.2 / Ubuntu 24.04 / kernel 6.8）搭配 **USB RTL8188EU** Wi‑Fi dongle，驱动来自社区仓库，连接不稳定。此前已建议：

- 该 USB Wi‑Fi 芯片不在 Seeed 官方验证范围内；
- 优先考虑 M.2 Key E Wi‑Fi 模块或直接使用 Ethernet。

客户随后尝试让一台 **Ubuntu 24.04 PC** 通过 **Wi‑Fi 上网**，再经 **LAN** 把网络共享给 Jetson，但未成功；已尝试：

- Host 有线 IPv4 设为 “Shared to other computers”
- Jetson 侧 DHCP 自动获取
- 手动静态 IP（如 `192.168.1.100`）
- Link-local only

## 核对资料

- Seeed Wiki：J401 载板具备 **1x Gigabit Ethernet**，无线扩展主要建议走 **M.2 Key E**。
- Canonical / NetworkManager 文档：`ipv4.method shared` 是 **共享/NAT** 模式，会启用 DHCP、forwarding 和 masquerading。
- NVIDIA 社区经验：当 Jetson 能与 host 通信但无法访问公网时，应优先排查 **host 转发/NAT、防火墙、默认路由、DNS**。

## 最终结论（内部）

1. 这类场景的标准做法不是 bridge，而是 **host 作为网关做 NAT 共享**。
2. Jetson 侧应先保持 **Automatic (DHCP)**；客户之前切换静态 IP / link-local only，容易把问题复杂化。
3. 如果 Jetson 能拿到局域网地址但无法访问 Internet，更大概率是 **Ubuntu host 的共享/NAT/防火墙未完全生效**，而不是 J4012 有线口异常。
4. 对外可建议客户先回到最简配置：host 有线口 `Shared to other computers`，Jetson 侧 DHCP 自动获取，然后分别验证 **本地地址 / 默认路由 / 8.8.8.8 / DNS**。

## 知识库更新

- [x] `docs/faq/jetson-ubuntu24-host-internet-sharing-over-ethernet.md`（active）
- [x] 更新 `INDEX.md`

## 外发英文要点

- Ubuntu host to Jetson over Ethernet should use **NetworkManager sharing/NAT**, not a bridge.
- Please leave Jetson Ethernet on **Automatic (DHCP)** first.
- If Jetson gets an IP but still cannot reach the Internet, check **host firewall**, **default route**, and **DNS**.
- If needed, ask the customer for `nmcli connection show`, `ip addr`, `ip route`, and `ufw status` on the host, plus `ip addr`, `ip route`, and ping results on the Jetson.
