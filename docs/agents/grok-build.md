# Grok Build

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a grok -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.grok/skills/cooked/SKILL.md` |
| Project | `.grok/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.grok/skills
cp -R skills/cooked ~/.grok/skills/cooked
```

## Invoke

```text
/cooked
```

Or: `cooked`, `did I cook`, `am I cooked`.

## Notes

Grok Build uses the standard Agent Skills layout under `.grok/skills/`. No adapter required.
