# Distribution

How `/cooked` gets in front of people.

## Channels

| Channel | Status | Action |
|---|---|---|
| GitHub public repo | live | https://github.com/HarjjotSinghh/cooked |
| Release `v1.1.0` | live | https://github.com/HarjjotSinghh/cooked/releases/tag/v1.1.0 |
| `npx skills` install | live | `npx skills add HarjjotSinghh/cooked --skill cooked -g` |
| skills.sh listing | **live** | https://skills.sh/HarjjotSinghh/cooked |
| OG card (canonical) | live | [`assets/og-card.png`](../assets/og-card.png) (v3 framed) |
| Raw image URL | live | https://raw.githubusercontent.com/HarjjotSinghh/cooked/main/assets/og-card.png |
| README hero | live | same card embedded at top of README |
| Release asset | live | attached to [v1.1.0](https://github.com/HarjjotSinghh/cooked/releases/tag/v1.1.0) |
| X / Twitter | draft ready | paste from [launch-post.md](../examples/launch-post.md) + attach `og-card.png` |
| Reddit / Discord / HN | optional | same card + before/after contrast |

skills.sh has **no submit form**. Listing is triggered by installs of a public repo via `npx skills add`. Repo is already indexed.

## One-liner

> Ask any agent "what's next?" and you get slop. Run `/cooked` and you get evidence — or silence.

## Install copy (everywhere)

```bash
npx skills add HarjjotSinghh/cooked --skill cooked -g
```

Then: `/cooked`

## Share image

**Always attach / embed** the canonical card:

| Use | Path |
|---|---|
| Local file | `assets/og-card.png` |
| GitHub raw | https://raw.githubusercontent.com/HarjjotSinghh/cooked/main/assets/og-card.png |
| Source | `assets/og-src/v3.html` |

Set **GitHub repo → Settings → Social preview** to this PNG so link previews use it (API cannot set this; one manual click).

## Screenshot pair (optional second image)

Use the two code blocks in [before-after.md](../examples/before-after.md):

1. **Before** — cold "what's next?" (10 generic bullets, zero citations)
2. **After** — `/cooked` (file:line, silently dropped, one next move)

That contrast *is* the secondary post. Primary visual is always `og-card.png`.

## Launch checklist

1. [x] Public repo + MIT
2. [x] README install + docs for major agents
3. [x] GitHub topics + description + homepage
4. [x] GitHub Release `v1.1.0`
5. [x] Seed install across agents (skills.sh telemetry)
6. [x] skills.sh page live (https://skills.sh/HarjjotSinghh/cooked)
7. [x] Canonical OG card in README + release asset
8. [ ] GitHub Settings → Social preview = `assets/og-card.png` (manual)
9. [ ] Post launch copy on X (see launch-post.md) — attach `og-card.png`
10. [ ] Optional: HN Show / Reddit r/ClaudeAI / agent Discord
11. [ ] After ~24h: check install count on skills.sh

## Do not

- Spiral on more agent guides before the post is live
- Soften the before/after — the slop list is the villain
- Promise "works on every agent" without the install path — link `docs/all-agents.md`
