# One-command install

## Recommended

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -g
```

Installs **cooked** globally for every coding agent the CLI detects on your machine.

## Pick agents

```bash
npx skills add HarjjotSinghh/cooked --skill cooked \
  -a claude-code -a codex -a cursor -a opencode -a gemini-cli \
  -a github-copilot -a pi -a grok -a windsurf -a cline -g
```

Install to **all** agents the CLI knows about (even if not detected):

```bash
npx skills add HarjjotSinghh/cooked --skill cooked --agent '*' -g -y
```

## Project-local (team share)

Omit `-g` so the skill lands in the project and can be committed:

```bash
cd your-app
npx skills add HarjjotSinghh/cooked --skill cooked -y
git add .claude .agents .cursor  # whatever paths your agents use
```

## Scope

| Scope | Flag | Where files go |
|---|---|---|
| Project | (default) | `./<agent-dir>/skills/cooked/` |
| Global | `-g` | `~/<agent-dir>/skills/cooked/` |

Exact paths per agent: [all-agents.md](./all-agents.md).

## Verify

```bash
npx skills list -g
npx skills list -g -a claude-code
```

You should see `cooked` listed for the agents you targeted.

## Update / remove

```bash
npx skills update cooked -g
npx skills remove cooked -g
```

## Use without installing

```bash
npx skills use HarjjotSinghh/cooked@cooked | claude
# or start an agent with the skill prompt:
npx skills use HarjjotSinghh/cooked --skill cooked --agent claude-code
```

## After install — run it

When the feature is "done":

```text
/cooked
```

Also works as natural language: `cooked`, `did I cook`, `am I cooked`, `now what`, `what's left`.

Agent-specific invoke notes live under [agents/](./agents/).
