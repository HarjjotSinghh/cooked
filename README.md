# cooked

> Did you cook, are you still cooking, or are you cooked?

A [Matt Pocock](https://github.com/mattpocock/skills)-style skill for coding agents. Run it **after** a feature is "done" — not before.

It reads the diff and the original ask, then returns a branded verdict plus what's *actually* unfinished: silently dropped requirements, code that was written but never wired up, contracts that drifted, tests that don't cover the new paths, and ship blockers.

Every item cites a `file:line` or a command it ran. Anything it can't cite, it doesn't say.

It ends with **one** next action, not a backlog.

```text
/cooked
```

## Why not just ask "what's next?"

Because you'll get: *add more tests, improve error handling, consider adding monitoring.* Ten items that could have been written before the agent opened your repo.

This skill bans that list by name and forces evidence for every claim. The constraint *is* the product — same reason [`grill-me`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) works.

## Verdicts

| Verdict | Meaning |
|---|---|
| **You cooked.** | Done, verified, ship-clear — or genuinely nothing left. |
| **Still cooking.** | Incomplete, unverified, unwired, or not live yet. |
| **You're cooked.** | Material bugs, failed criteria, regressions, or production risk. |

The double meaning is intentional. Ambiguity ships.

## Install

Portable [Agent Skills](https://agentskills.io/specification) layout — one `SKILL.md`, many agents.

```bash
# all supported agents, globally
npx skills add HarjjotSinghh/cooked --skill cooked -g

# or pick agents
npx skills add HarjjotSinghh/cooked --skill cooked -a claude-code -a codex -a opencode -a cursor
```

Then say `cooked`, `/cooked`, `did I cook`, or `am I cooked` when you're done with something.

### Manual install

| Agent | Path |
|---|---|
| Claude Code (skill) | `.claude/skills/cooked/SKILL.md` or `~/.claude/skills/cooked/SKILL.md` |
| Claude Code (command) | `.claude/commands/cooked.md` ← copy from `adapters/cooked.claude-command.md` |
| Codex (skill) | `~/.codex/skills/cooked/SKILL.md` |
| Codex (prompt fallback) | `~/.codex/prompts/cooked.md` ← copy from `adapters/cooked.codex.md` |
| OpenCode | `.opencode/command/cooked.md` ← copy from `adapters/command.md` |
| Gemini CLI | `~/.gemini/commands/cooked.toml` ← copy from `adapters/cooked.toml`, then `/commands reload` |
| Cursor / Copilot / others | drop `skills/cooked/` into the agent's skills directory |

### From this repo

```bash
git clone https://github.com/HarjjotSinghh/cooked.git
cp -R cooked/skills/cooked ~/.claude/skills/cooked   # Claude Code example
```

## The design in one line

Read-only · evidence-or-silence · max 3 per bucket · one next action · branded verdict.

### Six sweeps

1. **Broken promises** — TODOs, stubs, "not implemented", temp hardcodes in *this* diff  
2. **Dead wiring** — new exports/routes/handlers with zero call sites  
3. **Contract drift** — type/schema/API/DB changes with unupdated consumers  
4. **Verification gaps** — real typecheck/lint/test/build failures; untested new paths  
5. **Ship mechanics** — env, migrations, flags, lockfile, secrets  
6. **Spec delta** — every original requirement: done / partial / **silently dropped**

### Next-move ladder

`Finish → Prove → Ship → Observe → Advance → Stop`

Earliest applicable wins. Optional polish never outranks unfinished scope.

## Example

**Slop answer** (ask any agent "what's next?" cold):

```text
1. Add more unit tests
2. Improve error handling
3. Consider adding monitoring
4. Update the documentation
5. Refactor for readability
```

**`/cooked` answer** (evidence only):

```text
## Verdict
**Still cooking.**
Billing webhook is registered but never called from the checkout success path.

## Scope
12 files since origin/main · against issue #88

## Findings
### BLOCKING
1. `handleStripeWebhook` exported, zero call sites — `src/billing/webhook.ts:14`
   Checkout success never hits the webhook route; paid users stay "pending".

### Spec delta
| Requirement | Status |
|---|---|
| Process Stripe webhook on success | silently dropped |
| Show paid status in UI | partial |

## Don't start yet
Don't start the admin dashboard redesign — the money path is still open.

## → Next
Wire `handleStripeWebhook` into the checkout success handler · Finish
Done when a successful test payment flips the user to `paid` in the DB.
```

That contrast *is* the pitch. Screenshot both. Ship the post.

## Repo layout

```text
cooked/
├── skills/cooked/SKILL.md     # canonical skill (Agent Skills spec)
├── adapters/                  # slash-command ports for non-skill agents
│   ├── command.md             # generic / OpenCode
│   ├── cooked.claude-command.md
│   ├── cooked.codex.md
│   └── cooked.toml            # Gemini CLI
├── examples/                  # sample before/after outputs
├── LICENSE
└── README.md
```

## Pairs well with

- [`grill-me`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) — before you build. This is the bookend after.
- Code review skills — check *how* the code is written. This checks *what's missing*.

## Spec compliance

Follows the open [Agent Skills specification](https://agentskills.io/specification):

- `name` matches parent folder (`cooked`)
- `description` includes when-to-use triggers
- Portable `SKILL.md` body; adapters only for agents that don't load skills yet

## Contributing

PRs welcome. Keep the skill short. If a change makes the agent dump a backlog or invent chores, reject it.

## License

[MIT](./LICENSE)
