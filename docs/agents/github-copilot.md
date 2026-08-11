# GitHub Copilot

## Install

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a github-copilot -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.copilot/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.copilot/skills
cp -R skills/cooked ~/.copilot/skills/cooked
```

Project-local (recommended for teams):

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a github-copilot -y
# commit .agents/skills/cooked
```

## Invoke

In Copilot Chat / coding agent: mention the skill or say `cooked` / `did I cook` after finishing a change.

Agent Skills are first-class in Copilot; the same `SKILL.md` works.

## Docs

- [About agent skills (GitHub)](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
