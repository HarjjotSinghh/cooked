# Cline

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a cline -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.agents/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.agents/skills
cp -R skills/cooked ~/.agents/skills/cooked
```

## Invoke

In Cline chat: `cooked`, `/cooked`, or `what's left on this feature?`

## Shared layout

Cline shares the universal `.agents/skills/` layout with Dexto, Kimi Code CLI, Loaf, Warp, Zed, and others. One project install can serve several of them:

```bash
npx skills add HarjjotSinghh/cooked --skill cooked \
  -a cline -a warp -a zed -a kimi-code-cli -y
```

## Docs

- [Cline skills](https://docs.cline.bot/features/skills)
