# AGENTS.md

This repository is a single portable agent skill: **`cooked`**.

## Layout

- `skills/cooked/SKILL.md` — canonical skill (Agent Skills spec). Edit this first.
- `adapters/` — slash-command ports. Keep them in sync with the skill's core rules when the skill changes.
- `docs/` — install + per-agent guides. Update paths when the skills CLI agent matrix changes.
- `examples/` — sample outputs for docs and launch posts. Not loaded by agents.

## Rules for changing the skill

1. Stay read-only. The skill must never instruct the agent to edit, commit, push, or deploy.
2. Evidence-or-silence stays non-negotiable. No new section that invites uncited advice.
3. Max 3 items per ranking bucket.
4. Exactly one `→ Next` action.
5. Keep `SKILL.md` under ~500 lines / ~5k tokens (spec progressive-disclosure guidance).
6. `name` in frontmatter must stay `cooked` and match the folder name.
7. After editing `SKILL.md`, mirror material rule changes into every file under `adapters/`.

## Do not

- Turn this into a general codebase audit skill.
- Add a "recommended improvements" section without citations.
- Split into multiple skills unless a real second product emerges.
