# 知识库分区说明

## 客服技术支持（优先阅读）

| 路径 | `status` | 用途 |
|------|----------|------|
| `docs/faq/` | `active` | 已确认的常见问题 |
| `docs/seeed_device/` | `active` | Seeed 设备刷机、接口、BSP |
| `docs/official_kit/` | `active` | NVIDIA 官方开发套件 |
| `docs/common/` | `active` | 跨平台通用 |

索引入口：[`INDEX.md`](../INDEX.md)（仅列出 `active` 与明确标注的待复核项）

## 收集与观察（不可当最终技术结论）

| 路径 | 用途 |
|------|------|
| `docs/inbox/` | 有 **Question + Answer** 的收集草稿，`need_review`，人工晋升到 `faq/` |
| `docs/community_questions/` | **仅问题**、尚无可靠答案（社交媒体/论坛开放帖），跟踪是否已解决 |
| `docs/unknown_review/` | 有部分技术背景但仍需复核的条目 |

## 条目必填字段

见 [`_templates/entry-frontmatter.md`](_templates/entry-frontmatter.md)。  
**所有条目必须保留 `source_url` 或 `source_links`，供人工审核。**

## 晋升规则

`inbox/` 或 `community_questions/` → `docs/faq/`：

1. 人工核对来源链接与产品型号
2. 改 `status: active`
3. 更新 `INDEX.md`
4. 原文件可删除或在原处留 `promoted_to:` 链接
