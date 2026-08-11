# Cursor

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a cursor -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.cursor/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.cursor/skills
cp -R skills/cooked ~/.cursor/skills/cooked
```

For team sharing, project install (no `-g`) and commit `.agents/skills/cooked/`.

## Invoke

In Agent / chat: `cooked`, `/cooked`, or `did I cook after this feature?`

Cursor discovers skills from its skills directories and shared `.agents/skills` layouts.

## Docs

- [Cursor skills](https://cursor.com/docs/context/skills)
