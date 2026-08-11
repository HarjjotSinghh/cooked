---
description: Did you cook, still cooking, or are you cooked? Evidence-only audit of finished work — one verdict, ranked findings, one next action.
---

The work described above (or in `$ARGUMENTS`, if given) is done. Run **cooked**.

You are read-only. Do not edit code, do not fix what you find, do not start the next task.

**The one rule: every item you report must cite something you read** — a `file:line`, a command you ran and its output, a line from the diff, or a line from the issue/spec. If you cannot cite it, it does not go in the list.

### Verdicts (pick exactly one)

- **You cooked.** — outcome met, verified, ship-clear — or genuinely nothing left.
- **Still cooking.** — incomplete, unverified, unwired, not live, or open ship blockers.
- **You're cooked.** — material bugs, failed criteria, regressions, or production risk.

### Steps

1. **Boundary.** Find the diff (uncommitted → merge-base with default branch → last tag → last few commits) and the intent (linked issue, PR body, spec file, ticket in commit messages, or this conversation). State both in one line before continuing.

2. **Sweep, all six.**
   - Broken promises: TODO/FIXME/HACK added by this diff, stubs, "not implemented", temp hardcodes, commented-out blocks.
   - Dead wiring: every new export/route/handler/component/env var/migration — grep for a second usage site. Zero call sites means written but never plugged in.
   - Contract drift: changed type/schema/API shape/DB column/config key — grep every consumer, including other packages, generated clients, `.env.example`, fixtures, docs.
   - Verification gaps: actually run typecheck, lint, tests, build. Report real failures. Note skipped/`.only` tests and new code paths with no test at all.
   - Ship mechanics: env var missing from `.env.example` or deploy config, migration with no rollback, flag defaulting on, dep missing from lockfile, committed secret.
   - Spec delta: walk the original ask line by line, mark each requirement done / partial / **silently dropped**. Silently dropped is the most valuable finding here.

3. **Rank** into BLOCKING (broken in prod now) / WILL BITE (breaks within a week) / LOOSE END (cheap now, annoying later) / NOT DOING (out of scope, say why). Max 3 per bucket; if there are more, show the top 3 and say how many you cut.

4. **Next move** — earliest applicable: Finish → Prove → Ship → Observe → Advance → Stop. Exactly one concrete action with a crisp completion condition.

5. **Report** as:

```
## Verdict
**You cooked.** | **Still cooking.** | **You're cooked.**
<one evidence-based sentence>

## Scope
...

## Findings
### BLOCKING / WILL BITE / LOOSE ENDS / NOT DOING
...

### Spec delta
...

## Don't start yet
...

## → Next
...
```

If everything is genuinely clean: `**You cooked.** Nothing blocking. Tests green. Spec fully covered. Ship it — or stop and move on.`

**Banned unless cited:** "add more tests", "improve error handling", "add monitoring", "consider caching", "update the docs", "add rate limiting", "handle edge cases", "improve accessibility", "refactor for readability", "add types". If your finding could have been written before you opened the repo, delete it.

Then offer — do not perform — to grill the top item, file the rest as issues, or fix `→ Next`. Wait for the answer.
