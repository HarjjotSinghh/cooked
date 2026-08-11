# Gemini CLI

## Install (skills — preferred)

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -a gemini-cli -g -y
```

| Scope | Path |
|---|---|
| Global | `~/.gemini/skills/cooked/SKILL.md` |
| Project | `.agents/skills/cooked/SKILL.md` |

### Manual

```bash
mkdir -p ~/.gemini/skills
cp -R skills/cooked ~/.gemini/skills/cooked
```

## Optional: TOML slash command

If your Gemini CLI version uses custom commands (`.toml`) instead of or in addition to skills:

```bash
mkdir -p ~/.gemini/commands
cp adapters/cooked.toml ~/.gemini/commands/cooked.toml
```

Then in the CLI:

```text
/commands reload
/cooked
```

## Invoke

```text
/cooked
```

Or: `did I cook`, `am I cooked`, `now what`.

## Docs

- [Gemini CLI skills](https://geminicli.com/docs/cli/skills/)
