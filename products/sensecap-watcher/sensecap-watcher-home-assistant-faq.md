---
product: SenseCAP Watcher
platform: Seeed Studio Wiki
tags:
  - sensecap
  - watcher
  - home-assistant
  - sensecraft
  - wifi
  - troubleshooting
date: 2026-06-10
source_url: https://wiki.seeedstudio.com/integrate_watcher_to_ha/
---

# SenseCAP Watcher 配网、SenseCraft 与 Home Assistant FAQ

## 适用场景

适合解答买家关于 SenseCAP Watcher 首次绑定、2.4GHz Wi-Fi、Home Assistant 集成、本地 HTTP 推送和恢复出厂设置的问题。

## FAQ

### 问题：Watcher 支持 5GHz Wi-Fi 吗？

简洁答案：不支持。官方 SenseCraft APP 文档说明 Watcher 只支持 2.4GHz Wi-Fi，不支持 5GHz。配网失败时应让买家确认路由器已开启 2.4GHz SSID，手机蓝牙权限也已开启。

相关链接：

- https://wiki.seeedstudio.com/sensecap_app_introduction/
### 问题：首次绑定 Watcher 需要什么步骤？

简洁答案：在 Watcher 上通过滚轮进入绑定二维码界面，用 SenseCraft APP 扫码添加设备；绑定过程需要手机蓝牙权限，随后选择 2.4GHz Wi-Fi 并输入密码完成联网。

相关链接：

- https://github.com/Seeed-Studio/OSHW-SenseCAP-Watcher
- https://wiki.seeedstudio.com/sensecap_app_introduction/

### 问题：如何接入 Home Assistant？

简洁答案：先在 Home Assistant 安装 HACS，再通过 HACS 添加 SenseCraft 集成仓库 `https://github.com/Seeed-Solution/SenseCraft-HomeAssistant.git`。之后在 Settings > Devices & Services 中添加 SenseCraft 集成，选择局域网 host/id 添加 Watcher，并输入设备 EUI。

相关链接：

- https://wiki.seeedstudio.com/integrate_watcher_to_ha/
- https://github.com/Seeed-Solution/SenseCraft-HomeAssistant.git

### 问题：Home Assistant 中为什么显示“无数据”？

简洁答案：添加设备后如果任务没有运行，或没有在任务 Detail Config 中启用 HTTP Push Notification，Home Assistant 会没有数据。需要在任务中勾选 HTTP Push Notification，并将 HTTP URL 填为 Home Assistant 主机 IP 加端口 8887，例如 `http://192.168.1.151:8887`。

相关链接：

- https://wiki.seeedstudio.com/integrate_watcher_to_ha/

### 问题：想完全本地推送，不经过 SenseCraft 云端，应该怎么设置？

简洁答案：在 Watcher 的 HTTP Message Block 中配置本地 HTTP URL/Token，并勾选 HTTP Push Notification；不要勾选 APP Push Notification，否则通知仍会经过 SenseCraft 再推送到 APP。

相关链接：

- https://wiki.seeedstudio.com/sensecap_app_introduction/

### 问题：恢复出厂后为什么 APP 里还要删除设备？

简洁答案：官方文档提示 Restore Device Setting 会清除设备本地设置；恢复后需要在 APP 中手动删除对应设备，再重新添加。反过来，如果 APP 中删除设备后要重新绑定，也需要在设备侧执行 Factory Reset。

相关链接：

- https://wiki.seeedstudio.com/sensecap_app_introduction/
