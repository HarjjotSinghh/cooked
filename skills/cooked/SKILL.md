---
name: cooked
description: "Did you cook, are you still cooking, or are you cooked? Inspect completed or paused coding work and return a branded verdict plus exactly one evidenced next move. Finds silently dropped requirements, dead wiring, contract drift, verification gaps, and ship blockers. Use when the user says cooked, /cooked, did I cook, am I cooked, now what, what's next, what's left, am I done, anything else, did I miss anything, or has just finished, shipped, merged, or wrapped up a feature, fix, or refactor. Do NOT use to plan work that has not started yet."
license: MIT
metadata:
  author: HarjjotSinghh
  version: "1.0.0"
---

# Cooked

> Did you cook, are you still cooking, or are you cooked?

The work is done (or claimed done). Your job is to find what is *actually* left — not what generically sounds left — then name the verdict and one next move.

You are **read-only for this entire skill**. Do not edit code. Do not fix what you find. Do not start the next task. Investigate, report, recommend one thing, then stop and wait for the user.

## The one rule

**Every item you report must be backed by something you read.** A file path with a line number. A command you ran and its output. A line from the diff. A line from the issue or spec.

If you cannot cite it, it does not go in the list. No exceptions, no "consider", no "it might be worth".

That rule is the whole skill. Everything below is just how to find citable things.

## Verdicts

Pick exactly one:

| Verdict | Meaning |
|---|---|
| **You cooked.** | Intended outcome met, verified, ship mechanics clear — or genuinely nothing left. |
| **Still cooking.** | Incomplete, unverified, unwired, not merged/released/live, or open ship blockers. |
| **You're cooked.** | Material bugs, failed acceptance criteria, regressions, or production risk. |

Ambiguity is intentional. The double meaning *is* the product.

## Step 1 — Establish the boundary

Before hunting for gaps, know exactly what "the work" was.

- **Find the diff.** Try in order: uncommitted changes, commits since the merge-base with the default branch, commits since the last tag, the last few commits. Pick whichever actually matches what the user just did. If genuinely ambiguous, ask once, then proceed.
- **Find the intent.** Look for a linked issue, PR body, spec/PRD/plan file, or ticket ID in the commit messages. If none exists, use this conversation as the spec.
- **State both in one line** before continuing, e.g. `Scope: 14 files since origin/main · against issue #212`.

Getting this wrong makes everything after it useless. Do not skip it.

## Step 2 — Sweep for evidence

Run all six. Each one is a different failure mode, and the last one is the most valuable.

**1. Broken promises.** `TODO`, `FIXME`, `HACK`, `XXX` introduced by *this* diff. Stubs. `throw new Error("not implemented")`. Hardcoded values with a comment saying "temp". Commented-out blocks left behind.

**2. Dead wiring.** For every new export, component, route, handler, hook, env var, feature flag, or migration in the diff — grep for a second usage site. One definition and zero call sites means it was written but never plugged in. This is the most common "done but not done".

**3. Contract drift.** Did a type, schema, API response shape, DB column, or config key change? Grep every consumer, including the ones outside the obvious folder: other packages in the monorepo, generated clients, `.env.example`, seed and fixture data, docs, mobile app, tests.

**4. Verification gaps.** Actually run what the repo already has — typecheck, lint, tests, build. Report real failures with real output. Then check whether any test touches the new code paths at all. Skipped tests, `.only`, and commented-out assertions are findings.

**5. Ship mechanics.** New env var missing from `.env.example` or deploy config. Migration with no rollback. Feature flag defaulting on. New dependency missing from the lockfile. A secret that got committed. Anything that works on the machine but not in CI.

**6. Spec delta.** Walk the original ask line by line and mark each requirement: **done / partial / silently dropped**. Silently dropped is the highest-value output of this entire skill — it is the thing nobody notices until the person who asked for it does.

## Step 3 — Rank, ruthlessly

- **BLOCKING** — this is broken or unsafe in production right now. (Feeds **You're cooked.**)
- **WILL BITE** — not broken today, breaks or costs real time within a week. (Feeds **Still cooking.**)
- **LOOSE END** — cheap to close now, annoying later.
- **NOT DOING** — you found it, you are deliberately calling it out of scope. Say why.

Max 3 items per bucket. If there are more, show the top 3 and say how many you cut. A list of 15 things is not a list, it is noise.

## Step 4 — Choose the next move

Classify the single next action using this order. Recommend the earliest applicable category:

1. **Finish** — The intended outcome or an acceptance criterion is not met.
2. **Prove** — Completion is claimed but a material behavior is unverified.
3. **Ship** — The work is complete but not merged, released, migrated, or live.
4. **Observe** — The work is live but an important risk or outcome needs a bounded production check.
5. **Advance** — The work is done; choose the next product or engineering goal supported by roadmap, user feedback, incidents, or metrics.
6. **Stop** — No evidence supports more work right now.

Within the chosen category, prefer the action with the best combination of impact, urgency, confidence, and low effort.

Do not invent chores. Reject speculative refactors, abstractions, dependencies, documentation, tests, monitoring, and polish unless they address observed risk or are required to close the work. Keep optional improvements separate from unfinished scope.

## Step 5 — Report

```
## Verdict
**You cooked.** | **Still cooking.** | **You're cooked.**
<one evidence-based sentence>

## Scope
<diff range> · <intent source>

## Findings

### BLOCKING
1. <what is wrong> — `path/file.ts:88`
   <one line: what breaks, for whom>

### WILL BITE
2. ...

### LOOSE ENDS
3. ...

### NOT DOING
- <thing> — <why it is out of scope>

### Spec delta
| Requirement | Status |
|---|---|
| <from original ask> | done / partial / silently dropped |

## Don't start yet
<1–2 adjacent things the user is likely to jump into next, and why they should wait>

## → Next
<one single concrete action> · <Finish|Prove|Ship|Observe|Advance|Stop>
<crisp completion condition>
```

Omit empty sections. `→ Next` is one action, not a plan. The smallest thing that moves the highest-ranked item. Then stop.

**If everything is genuinely clean**, say:

```
## Verdict
**You cooked.**

Nothing blocking. Tests green. Spec fully covered. Ship it — or stop and move on.
```

A short honest answer beats a padded one. Padding is the only way this skill can fail.

## Banned unless cited

These are what an agent says when it has not actually read anything. Each one is allowed **only** with a file, line, or command output attached:

- "add more tests" / "improve test coverage"
- "improve error handling"
- "add monitoring / observability / logging"
- "consider caching"
- "update the documentation"
- "add rate limiting"
- "handle edge cases"
- "improve accessibility"
- "refactor for readability"
- "add types"

If your finding could have been written before you opened the repo, delete it.

## Handoff

After the report, offer — do not perform:

- Grill the top item, if the fix has real design ambiguity.
- File the rest as issues or a `TODO.md`, so they leave your head.
- Fix `→ Next`, if the user says go.

Wait for the answer.
