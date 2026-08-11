# Amp / Replit / Universal

These agents share the **universal** skills layout (`.agents/skills/`).

## Install

```bash
# Amp
npx skills add HarjjotSinghh/cooked --skill cooked -a amp -g -y

# Replit
npx skills add HarjjotSinghh/cooked --skill cooked -a replit -g -y

# Explicit universal id
npx skills add HarjjotSinghh/cooked --skill cooked -a universal -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.config/agents/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.config/agents/skills
cp -R skills/cooked ~/.config/agents/skills/cooked
```

## Invoke

`cooked` / `/cooked` / natural language triggers in the skill description.

## Docs

- [Amp skills](https://ampcode.com/manual#agent-skills)
- [Replit skills](https://docs.replit.com/replitai/skills)
