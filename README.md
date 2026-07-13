# claude-session-suite

> Spawn it. Keep it alive. Teleport it.

A **Claude Code plugin marketplace** covering the full lifecycle of a session —
three standalone tools that compose:

| Stage | Plugin | What it does | Repo |
|---|---|---|---|
| **Spawn** | `claude-remote` | Spawn Remote Control sessions in detached tmux panes, get the claude.ai/code URL | [claude-remote-launcher](https://github.com/superbereza/claude-remote-launcher) |
| **Keep alive** | `claude-session-keeper` | Sessions self-register; a systemd timer resurrects anything a reboot/OOM killed | [claude-session-keeper](https://github.com/superbereza/claude-session-keeper) |
| **Move** | `claude-session-teleport` | Teleport a live chat (and its project) to another machine — clone/migrate, tmux respawn, handoff briefing | [claude-session-teleport](https://github.com/superbereza/claude-session-teleport) |

> [!TIP]
> **Spawn works agent-side too.** A running Claude can spawn more Claudes —
> bud off fresh sessions in other folders mid-task, grab their claude.ai/code
> URLs, and keep working — all without leaving its own session.

## How they compose

A typical multi-machine setup: **spawn** working sessions on a server with
`claude-remote` (you — or a Claude that needs a helper), **register** the
important ones with `claude-keep add` so they survive reboots, and when work
needs to follow you — **teleport** the session to the laptop and back, history
intact.

## Use

```text
/plugin marketplace add superbereza/claude-session-suite

/plugin install claude-remote@claude-session-suite
/plugin install claude-session-keeper@claude-session-suite
/plugin install claude-session-teleport@claude-session-suite
```

Each plugin also works standalone and is **its own marketplace** — see the repos.
All three share one skill-repo standard: the same `skills/` directory is consumed
by Claude Code, Cursor, Codex and Gemini.
