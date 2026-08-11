# OpenCode

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a opencode -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.config/opencode/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.config/opencode/skills
cp -R skills/cooked ~/.config/opencode/skills/cooked
```

### Optional: command adapter

Some OpenCode setups also load command files:

```bash
# path may be command/ or commands/ depending on version
mkdir -p .opencode/command
cp adapters/command.md .opencode/command/cooked.md
```

## Invoke

```text
/cooked
```

Or natural language: `cooked`, `what's left`, `am I done`.

## Docs

- [OpenCode skills](https://opencode.ai/docs/skills)
