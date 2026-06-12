# Seeed Jetson 知识生态 — 三库三 Agent

> 本文件描述三个 GitHub 仓库如何分工。  
> **当前仓库 = 库 1（技术支持闭环）**，只服务客服 Agent 与你对话。

## 总览

```
┌─────────────────────────────────────────────────────────────────┐
│  你（产品/运营）                                                  │
│  · 与 Agent 1 对话处理工单                                        │
│  · 周审库 2 的反馈与开放问题                                       │
│  · 扫一眼库 3 日报                                               │
│  · merge 各库 draft PR                                           │
└────────────┬───────────────────────┬──────────────────────────┘
             │                       │
    对话触发 │                       │ 每日定时 Automation
             ▼                       ▼
┌────────────────────┐   ┌────────────────────┐   ┌────────────────────┐
│ 库 1 技术支持       │   │ 库 2 收集           │   │ 库 3 资讯           │
│ seeed-jetson-      │   │ seeed-jetson-      │   │ seeed-jetson-      │
│ knowledge (本库)   │   │ collect (新建)     │   │ news (新建)        │
├────────────────────┤   ├────────────────────┤   ├────────────────────┤
│ Agent 1 客服       │   │ Agent 2 收集       │   │ Agent 3 资讯       │
│ Cursor 对话        │   │ Cursor Automation  │   │ Cursor Automation  │
└────────────────────┘   └────────────────────┘   └────────────────────┘
```

## 库 1：技术支持闭环（本仓库）

**GitHub（当前）：** `xbs0325/seeed-jetson-knowledge`

**职责：** 答客户 + 结案沉淀 + 维护已确认知识库。

| 路径 | 用途 |
|------|------|
| `AGENTS.md`、`instructions/` | 客服运行指令 |
| `memory/` | 偏好、渠道、误区（短） |
| `docs/faq/`、`docs/seeed_device/`… | **`status: active` 已确认知识** |
| `docs/staging/` | 支持结案产生、**待你确认**再晋升 active |
| `cases/` | 每次支持的结案记录（闭环日志） |
| `INDEX.md` | 仅索引本库 active + staging |

**不做：** 社交媒体爬取、每日新闻、产品建议池（在库 2）。

**结案后写入：**

- 已确认 → `docs/faq/` 或更新已有条 + `cases/`
- 待确认 → `docs/staging/`
- 长期约定 → `memory/`
- 产品建议 / 无答案开放问题 → **在库 2 开 PR**（或记入 `cases/` 的 `export_to: collect` 字段，由你/Agent 2 同步）

---

## 库 2：收集与反馈（新建）

**建议仓库名：** `seeed-jetson-collect`

**职责：** 官方 FAQ 变更、Discord/论坛可信 Q&A、开放问题、用户建议。

| 路径 | 用途 |
|------|------|
| `AGENTS.md` | 收集 Agent 入口 |
| `instructions/collector.md` | 每日定时指令 |
| `inbox/` | 有 Q&A 的草稿（`need_review`） |
| `community_questions/` | 仅问题，跟踪是否已有解答 |
| `feedback/suggestions/` | 产品建议 |
| `feedback/issues/` | 问题聚类（体验/缺陷） |
| `DASHBOARD.md` | 给你的一页总览 |
| `INDEX.md` | 收集索引 |

**来源：** Seeed Wiki/Forum、Discord（需可验证）、Reddit 等。

**晋升到库 1：** 你核对 `source_url` 后，把条目复制/PR 到库 1 的 `docs/faq/` 并标 `active`。

**Automation：** 每天 1 次，draft PR only，不 merge。

---

## 库 3：前沿资讯（新建）

**建议仓库名：** `seeed-jetson-news`

**职责：** JetPack 发布、NVIDIA/Seeed 重大新闻，**不直接当客服答案**。

| 路径 | 用途 |
|------|------|
| `AGENTS.md` | 资讯 Agent 入口 |
| `instructions/news-digest.md` | 每日指令 |
| `daily/YYYY-MM-DD.md` | 日报 |
| `INDEX.md` | 按日期/主题索引 |

**Automation：** 每天 1 次，draft PR only。

**与库 1 关系：** 日报中「建议入库」项 → 你决定后由库 1 支持 Agent 或你手动写 FAQ。

---

## 数据流

```
客户问题 ──► Agent 1（库 1）──► 答复
                │
                └──► cases/ + docs/staging|faq/ + memory/
                              │
                              │ 你 merge PR
                              ▼
                         INDEX 更新

Discord/论坛 ──► Agent 2（库 2）──► inbox / community / feedback
                              │
                              │ 你周审晋升
                              ▼
                         库 1 docs/faq/

NVIDIA/Seeed 新闻 ──► Agent 3（库 3）──► daily/
                              │
                              │ 你扫一眼
                              ▼
                         可选 → 库 1 FAQ
```

## 仓库创建清单

- [ ] 新建 `seeed-jetson-collect`，从本仓库 `templates/collect-repo/` 复制骨架
- [ ] 新建 `seeed-jetson-news`，从 `templates/news-repo/` 复制骨架
- [ ] 库 1 去掉 `inbox/`、`community_questions/`、`automation-collector.md`（已在本 PR）
- [ ] Cursor：库 1 绑定对话 Agent；库 2、3 各绑每日 Automation
- [ ] 你周审：库 2 `DASHBOARD.md` + 库 1 `docs/staging/`

## Agent 1 与你沟通的内容

- 工单怎么答、结案写哪
- 库 2、3 的 Automation prompt 要不要改（指令在对应库，本 Agent 帮你起草）
- 库 2 里哪些 inbox 可以晋升到库 1
