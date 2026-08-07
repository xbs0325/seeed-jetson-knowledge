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

> 说明：权威工作流仍以 `AGENTS.md` / `instructions/` 为准。Skill 放在 `.agent/skills/`，并在 `.claude/skills/` 放同名副本供 Claude Code 发现（非 symlink，便于在 GitHub 直接打开 `SKILL.md`）。若还需 Cursor 自动发现，可同步到 `.agents/skills/` 或 `.cursor/skills/`。
