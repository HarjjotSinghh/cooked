# Share assets

Craft-level OG cards (1200×630 @2x), matched to brand quality from reinstate / moonshift / portfolio.

## Canonical (use this everywhere)

| File | Role |
|---|---|
| **`og-card.png`** | Default share image — README hero, release asset, social posts |
| `og-v3-framed.png` | Same art as `og-card.png` (source-of-truth render name) |

```text
https://raw.githubusercontent.com/HarjjotSinghh/cooked/main/assets/og-card.png
```

Where it is wired:

- README hero
- GitHub Release `v1.1.0` asset
- Launch posts ([`examples/launch-post.md`](../examples/launch-post.md))
- Distribution checklist ([`docs/distribution.md`](../docs/distribution.md))

**Still manual once:** GitHub → Settings → Social preview → upload `og-card.png`.

## Variants (archives)

| File | Direction (reference DNA) | Headline |
|---|---|---|
| `og-v1-product.png` | Reinstate — brand + illustration | **Post-work audit for coding agents** |
| `og-v2-marketing.png` | Moonshift — hero + product mock | **Feature shipped. Actually done?** |
| `og-v3-framed.png` | Portfolio — hatch + corner card | **Prove the work is actually done.** ← default |
| `og-v4-verdicts.png` | Dark editorial product | **What is left after “done”?** |

Source HTML: `og-src/v{1-4}.html` (render via Playwright).

Default stack: Manrope + Inter (portfolio-25 OG), monoline icons, two-line desc.
