# 知识库清洗审计 — 2026-06-12

> 自动化收集已建议暂停。本文档标出当前知识库中**可能影响技术支持准确性**的问题，并说明新的分区规则。

## 一、当前统计

| 分区 | 文件数 | 说明 |
|------|--------|------|
| `docs/faq/` | 9 | 客服 FAQ |
| `docs/seeed_device/` | 8 | Seeed 设备资料 |
| `docs/official_kit/` | 5 | NVIDIA 官方套件 |
| `docs/common/` | 1 | 通用 |
| `docs/unknown_review/` | 1 | 待复核技术条目 |
| `status: active` | 20 | 客服可优先引用 |
| `status: need_review` | 4 | **不应作为最终结论** |

---

## 二、高优先级问题（建议尽快处理）

### 1. `need_review` 条目出现在 INDEX 的 FAQ 主列表里

以下条目 `status: need_review`，但 INDEX「FAQ」区块未区分，客服 Agent 可能当 `active` 引用：

| 文件 | 问题 |
|------|------|
| `docs/faq/seeed-jetpack-6-apt-upgrade-l4t-kernel-conflict.md` | 来源 GitHub issue，建议 hold 方案需按型号复核 |
| `docs/faq/reserver-industrial-j4012-poe-jetpack-6.md` | 来源论坛帖，PoE 行为未官方确认 |
| `docs/seeed_device/reserver/reserver-industrial-j4012-jetpack-6-gpio-poe.md` | 与上条同论坛源，内容部分重复 |

**已做：** INDEX 拆为「已确认」与「待复核」两区。  
**建议：** PoE/GPIO 两条合并或明确分工；复核后改 `active` 或移到 `community_questions/`。

### 2. Classic J401 与 Super J401 刷机路径混用风险

| 文件 | 风险 |
|------|------|
| `docs/seeed_device/recomputer/recomputer-j401-flash-jetpack.md` | 标题含 J4012，但流程是 **Classic J401**（`recomputer-orin-j401` / 旧 flash 命令），**不含 Super** |
| `docs/seeed_device/recomputer/recomputer-super-jetpack-6-2.md` | Super 正确路径（mfi + `--flash-only`），但未写自编译板级名 `recomputer-orin-super-j401` |
| `docs/seeed_device/recomputer/seeed-linux-for-tegra-jetpack-6-2-bsp.md` | README 列举支持硬件**未列 Super**，易误导「源码 BSP 不含 Super」 |

**实际规则：**

- **Classic** → Wiki `reComputer_J4012_Flash_Jetpack` / `recomputer-orin-j401`
- **Super** → Wiki `recomputer_jetson_super_getting_started` / mfi 或 `recomputer-orin-super-j401`

**建议：** Classic 刷机文档标题注明「不含 Super」；Super 文档补充自编译板级名（已列入本次 inbox 草稿）。

### 3. 产品型号在 INDEX 中过度合并

`recomputer-j401-flash-jetpack.md` 索引为 J3010/J3011/J4011/**J4012**，但：

- **J4012** 可能是 Classic 或 **Super**（不同 SKU/外壳）
- 淘宝标题「Orin NX 16G Super」几乎总是 **Super J4012**，不应默认链到 Classic 刷机 Wiki

**建议：** 客服先辨 Classic / Super / Industrial / Robotics，再选文档（见 `memory/workflow-notes.md`）。

### 4. `unknown_review` 与「开放问题」职责重叠

| 路径 | 应有内容 |
|------|----------|
| `docs/unknown_review/` | 有部分结论、仍需人工核实的**技术事实** |
| `docs/community_questions/`（新建） | 社交媒体等渠道的**开放问题**，尚无可靠答案，需跟踪是否被解决 |

`seeed-j401-jetpack-7-2-support.md` 适合留在 `unknown_review`（有背景、无定论）。  
纯用户提问、无人回复的帖应进 `community_questions/`。

---

## 三、中优先级问题

### 5. 来源链接不完整

规范要求每条保留可审核链接。当前缺口：

| 文件 | 缺口 |
|------|------|
| 多数 `seeed_device/` 条目 | 仅有 `source_url`（Wiki），无「最后核对日期」 |
| `docs/faq/taobao-title-official-module-vs-nvidia-devkit.md` | 来自对话沉淀，除 Wiki 外无淘宝样例链接（可接受，已在 memory 层） |

**已做：** 新建 `docs/_templates/entry-frontmatter.md` 统一要求 `source_url` + 可选 `source_links[]`。

### 6. DAILY_SUMMARY 与知识库状态不同步

`DAILY_SUMMARY.md` 历史条目把部分 `need_review` 写在「今日新增」里，未强调不可当最终答案。  
**建议：** 收集自动化暂停期间，DAILY_SUMMARY 仅由人工或新 collector 更新；客服不以 DAILY_SUMMARY 为事实依据，以 `INDEX.md` + `status: active` 为准。

### 7. 论坛来源条目置信度

| 文件 | 来源类型 | 注意 |
|------|----------|------|
| `reserver-industrial-j4012-*` | Seeed Forum | 用户实测，非 Seeed 官方声明 |
| `jetpack-6-gpio-pinmux.md` | GitHub issue | NVIDIA 生态问题，非 Seeed 专属 |
| `seeed-jetpack-6-apt-upgrade-*` | GitHub issue | Seeed 维护者回复，仍标 need_review |

---

## 四、低优先级 / 结构优化

- `docs/faq/agx-orin-64gb-developer-kit-datasheet.md`：官方套件 FAQ，与 Seeed 电商问法常混用，已有淘宝标题 FAQ 互补，可保留。
- `docs/official_kit/` JetPack 7.2 条目：对 Seeed 客户需强调「官方 DevKit only」，已有 `seeed-device-use-nvidia-official-image.md`。
- 记忆层 `memory/common-mistakes.md` 与 `docs/faq/taobao-title-*` 有重叠：合理（memory=习惯，docs=可引用事实）。

---

## 五、新分区规则（本次落地）

```
docs/
├── faq/                    # status:active — 客服主库（已人工确认）
├── seeed_device/           # status:active — 设备资料
├── official_kit/           # status:active
├── common/                 # status:active
├── inbox/                  # status:need_review — 收集到的 Q&A 草稿（有答案）
├── community_questions/    # 仅问题 — 社交媒体开放问题，跟踪 resolution
├── unknown_review/         # 有部分结论待复核的技术条目
└── _templates/             # 条目模板
```

**客服 Agent（技术支持）：**

- 优先读 `status: active` 的 `docs/faq`、`docs/seeed_device`、`docs/official_kit`、`docs/common`
- `inbox`、`community_questions`、`unknown_review` 仅作参考，须标注「待复核 / 开放问题」
- **不**自动把收集内容写入 `faq/` 或改 `memory/`

**收集 Agent（暂停后可按新指令重启）：**

- 社交媒体产品问题 → 总结到 `community_questions/`（仅问题）或 `inbox/`（有可靠 Q&A）
- 每条必须含 `source_url` 或 `source_links`
- 只开 draft PR，不 merge

---

## 六、建议人工下一步

1. 复核 4 条 `need_review`，决定晋升 `active` 或降级到 `community_questions`
2. 拆分/标注 Classic vs Super 刷机文档
3. 从近期工单把 Super 刷机板级名、apt/浏览器 FAQ 复核后晋升（见 `docs/inbox/` 草稿）
4. 自动化保持关闭，直到 `instructions/automation-collector.md` 配置完成
