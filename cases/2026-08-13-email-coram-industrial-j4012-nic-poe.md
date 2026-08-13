---
date: 2026-08-13
channel: email
reply_to: customer
product: reComputer Industrial J4012 (SKU 100049279 / order DZ2605060002)
issue_type: other
confidence: needs_review
final_customer_reply: true
account: Coram.ai (via Nana Zhou / distributor techsupport)
---

# 英文邮件：Coram.ai Industrial J4012 双网口 / PoE 问题

## 历史对话背景

- 销售 Nana 转交：Coram 反馈 J4012 一批中至少 5 台网口异常。
- 已说明双口角色并索要 BSP 核对命令；Aron 回传日志（缺 dmesg）。
- 渠道客户：本轮外发以核实为主，不下根因、不承诺 RMA。

## 最终外发口径

- 感谢日志；该测试机镜像/板级标识与 Industrial 一致（谨慎陈述）。
- 复述规格：LAN1=PoE PSE，LAN2=普通口。
- 请客户确认拓扑、「goes offline」含义、单口测试、PoE/电源/相机、批量范围，并补 ethtool/ip route/dmesg。

## 知识库更新

- [x] FAQ / staging / memory / INDEX（见同 PR）
