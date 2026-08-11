# Docs

Install and use **`/cooked`** on any coding agent that supports [Agent Skills](https://agentskills.io).

## Start here

| Doc | When |
|---|---|
| [**One-command install**](./install.md) | You want `npx skills` and you're done |
| [**All agents matrix**](./all-agents.md) | You need the exact path for any of 70+ agents |
| [**Agent guides**](./agents/) | Your harness needs a special invoke or adapter |

## Major agents (deep guides)

| Agent | Guide | `--agent` | Invoke |
|---|---|---|---|
| [Claude Code](./agents/claude-code.md) | Install + `/cooked` slash command | `claude-code` | `/cooked` |
| [OpenAI Codex](./agents/codex.md) | Skills + `$cooked` / prompt fallback | `codex` | `$cooked` or `cooked` |
| [Cursor](./agents/cursor.md) | Project + global skills | `cursor` | `cooked` / Agent Skills |
| [OpenCode](./agents/opencode.md) | Skills + optional command adapter | `opencode` | `/cooked` |
| [Gemini CLI](./agents/gemini-cli.md) | Skills path + TOML command | `gemini-cli` | `/cooked` |
| [GitHub Copilot](./agents/github-copilot.md) | VS Code agent skills | `github-copilot` | skill mention / Agent |
| [Pi](./agents/pi.md) | coding-agent skills | `pi` | `/cooked` or skill name |
| [Grok Build](./agents/grok-build.md) | `.grok/skills` | `grok` | `/cooked` |
| [Windsurf](./agents/windsurf.md) | Codeium Windsurf skills | `windsurf` | skill name |
| [Cline](./agents/cline.md) | VS Code Cline + shared `.agents` | `cline` | skill name |
| [Continue](./agents/continue.md) | Continue.dev skills | `continue` | skill name |
| [Amp / Replit](./agents/amp.md) | Universal `.agents/skills` | `amp` / `replit` | skill name |
| [Goose](./agents/goose.md) | Block Goose skills | `goose` | skill name |
| [Roo Code](./agents/roo-code.md) | Roo Code skills | `roo` | skill name |
| [Antigravity](./agents/antigravity.md) | Google Antigravity | `antigravity` | skill name |
| [OpenClaw](./agents/openclaw.md) | OpenClaw skills root | `openclaw` | skill name |
| [OpenHands](./agents/openhands.md) | OpenHands skills | `openhands` | skill name |
| [Crush](./agents/crush.md) | Charm Crush | `crush` | skill name |
| [AiderDesk](./agents/aider-desk.md) | AiderDesk skills | `aider-desk` | skill name |
| [Junie](./agents/junie.md) | JetBrains Junie | `junie` | skill name |

Everything else → [all-agents.md](./all-agents.md).

## What "supported" means

1. **Canonical skill** — `skills/cooked/SKILL.md` follows the open Agent Skills spec.
2. **CLI install** — `npx skills add HarjjotSinghh/cooked --skill cooked` copies or symlinks into that agent's skill directory.
3. **Adapters** — only when an agent still wants a slash-command / TOML / prompt file instead of (or in addition to) skills. See [`../adapters/`](../adapters/).

If an agent loads `SKILL.md` from a skills folder, it is supported. No per-agent rewrite of the skill body.
