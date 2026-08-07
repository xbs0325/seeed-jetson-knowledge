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

> 说明：权威副本在 `.agent/skills/`。Claude Code 发现路径已用 symlink：`.claude/skills/seeed-jetson-support` → `../../.agent/skills/seeed-jetson-support`。若还需 Cursor 自动发现，可同样 symlink 到 `.agents/skills/` 或 `.cursor/skills/`。
