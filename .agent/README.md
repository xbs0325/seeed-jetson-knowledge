# `.agent`

本目录存放可复用的 Agent Skill（Cursor / 兼容工具可发现）。

| Skill | 路径 | 说明 |
|-------|------|------|
| `seeed-jetson-support` | [`skills/seeed-jetson-support/SKILL.md`](skills/seeed-jetson-support/SKILL.md) | Seeed Jetson 技术支持闭环摘要 |

完整指令仍以仓库根目录为准：

- [`AGENTS.md`](../AGENTS.md)
- [`instructions/`](../instructions/)
- [`INDEX.md`](../INDEX.md)
- [`memory/`](../memory/)

> 说明：Cursor 默认还会扫描 `.agents/skills/`、`.cursor/skills/`。本仓库按需求放在 `.agent/skills/`；若需自动发现，可将同名 skill 同步到上述目录，或以 symlink 指向此处。
