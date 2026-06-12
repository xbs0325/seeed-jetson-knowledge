# 记忆层说明

本目录存放**长期记忆**：对话中形成的偏好、约定、处理习惯、已确认的流程决策。

与另外两层区分：

| 层级 | 路径 | 写什么 |
| --- | --- | --- |
| 指令 | `AGENTS.md`、`instructions/` | 角色、流程、禁令（相对稳定） |
| **记忆** | `memory/` | 用户偏好、渠道约定、回复习惯、已确认的处理决策 |
| 知识库 | `docs/`、`INDEX.md` | Jetson 技术事实、FAQ、案例 |

## 文件放置规则

| 内容类型 | 写入位置 |
| --- | --- |
| 用户偏好、回复风格、渠道约定 | `memory/preferences.md` |
| 某类问题的处理习惯、内部约定 | `memory/workflow-notes.md` |
| 某客户/渠道的已确认处理记录（非公开技术事实） | `memory/channel-notes.md` |
| 常见误区、易错点速查 | `memory/common-mistakes.md` |

## 更新原则

- 对话中出现**应长期保留**的约定时，Agent 应写入本目录对应文件，并通过 PR 合并。
- 已核对的技术事实 → 写 `docs/`，不写 `memory/`。
- 不确定的内容 → `docs/unknown_review/`，不写入记忆层。
