# Claude Code

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a claude-code -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.claude/skills/cooked/SKILL.md` |
| Project | `.claude/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.claude/skills
cp -R skills/cooked ~/.claude/skills/cooked
```

### Optional: slash command adapter

If you want a dedicated `/cooked` command file (in addition to the skill):

```bash
mkdir -p ~/.claude/commands
cp adapters/cooked.claude-command.md ~/.claude/commands/cooked.md
```

## Invoke

```text
/cooked
```

Natural language also works once the skill is installed: `did I cook?`, `am I cooked?`, `now what`.

## Use without installing

```bash
npx skills use HarjjotSinghh/cooked@cooked | claude
```

## Docs

- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Agent Skills spec](https://agentskills.io/specification)
