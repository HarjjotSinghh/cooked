# Contributing

## What this repo is

One skill. Portable. Funny name, hard constraint.

If your PR makes `/cooked` dump a longer backlog, invent chores, or start fixing code mid-report — it will be closed.

## How to contribute

1. Edit `skills/cooked/SKILL.md` first.
2. Mirror any rule changes into `adapters/*`.
3. If you change the report shape, update `examples/`.
4. Keep the README install table accurate if you add an adapter.

## Local check

```bash
# frontmatter name matches folder
head -5 skills/cooked/SKILL.md

# tree should look like this
find skills adapters examples -type f | sort
```

Optional, if you have the reference validator:

```bash
npx skills-ref validate ./skills/cooked
```

## Ideas that fit

- Better boundary detection for monorepos / dirty trees
- Clearer Gemini / OpenCode adapter notes
- Real (anonymized) before/after examples from production runs

## Ideas that do not fit

- Auto-fix mode
- Generic "best practices" checklists
- Second skills that dilute the brand

## License

By contributing, you agree your changes are MIT-licensed, same as the repo.
