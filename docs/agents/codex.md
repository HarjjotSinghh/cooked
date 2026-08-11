# OpenAI Codex

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a codex -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.codex/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.codex/skills
cp -R skills/cooked ~/.codex/skills/cooked
```

### Optional: prompt fallback

Older / custom-prompt setups:

```bash
mkdir -p ~/.codex/prompts
cp adapters/cooked.codex.md ~/.codex/prompts/cooked.md
```

Prefer skills. Codex has moved custom prompts toward skills.

## Invoke

```text
$cooked
```

Or: `cooked`, `/cooked`, `did I cook`, `am I cooked`.

Optional scope: `$cooked since origin/main`

## Docs

- [Codex skills](https://developers.openai.com/codex/skills/)
