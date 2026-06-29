# 知识库（技术支持）

`docs/` 按**问题归属**分目录，方便 Agent 和客服检索。条目 frontmatter 中的 `status: active` 表示已核对、可直接引用。

## 已确认（`status: active`）

| 目录 | 放什么 | 举例 |
|------|--------|------|
| `faq/` | 从工单沉淀的**问答型**条目，跨产品复用 | HDMI 无信号、能否刷官方镜像 |
| `seeed_device/` | Seeed 自有设备的产品文档 | J401 刷机、Industrial 入门 |
| `official_kit/` | NVIDIA 官方开发套件相关 | Orin Nano ISO 安装、JP 发布说明 |
| `common/` | 不绑定具体产品的跨平台技术 | BSP 匹配后补装 SDK 组件 |

`official_kit/common/` 是官方套件下的共性内容（如 JP 版本发布），与顶层 `common/` 不同：前者仍属 DevKit 语境，后者适用于所有已正确刷机的 Jetson。

## 待确认（`docs/staging/`）

结案或复核中的草稿，**勿当最终答案**。引用时须向客户说明尚未核实。

## 条目规范

见 [`_templates/entry-frontmatter.md`](_templates/entry-frontmatter.md)。
