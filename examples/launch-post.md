# Launch post — copy / paste

**Always attach the share card first:**

```text
assets/og-card.png
```

Raw: https://raw.githubusercontent.com/HarjjotSinghh/cooked/main/assets/og-card.png

---

## X / Twitter (primary)

Attach `og-card.png`, then:

```text
Ask any coding agent "what's next?" after a feature ships.

You get:
• add more tests
• improve error handling
• consider monitoring
• update the docs
• refactor for readability

Zero citations. Could've been written without opening the repo.

I built /cooked — a skill that refuses to invent chores.

Evidence or silence. Max 3 per bucket. One next action.
Verdict: You cooked. / Still cooking. / You're cooked.

npx skills add HarjjotSinghh/cooked --skill cooked -g

Then: /cooked

https://github.com/HarjjotSinghh/cooked
```

### Alt shorter

```text
"What's next?" → agent slop.
/cooked → file:line or silence.

Did you cook, still cooking, or are you cooked?

npx skills add HarjjotSinghh/cooked --skill cooked -g

https://github.com/HarjjotSinghh/cooked
```

## Reply / second post (attach screenshots)

Primary tweet already has `og-card.png`. For a thread reply:

Screenshot 1: the slop list from [before-after.md](./before-after.md) **Before** block.  
Screenshot 2: the **After** `/cooked` report from the same file.

```text
The whole product is this contrast.

Left: generic next steps.
Right: silently dropped requirement + dead wiring + one next move.

Bookend to grill-me: grill before you build, /cooked after you "finish."
```

## LinkedIn / longer

```text
I got tired of finishing a feature and asking the agent "what's next?" — only to get a backlog that could have been written without opening the repo.

So I shipped /cooked.

It's a portable agent skill (Claude Code, Codex, Cursor, OpenCode, Gemini CLI, and 70+ more) that:

• Is read-only — audit only, no mid-report "fixes"
• Requires a citation (file:line, command output, or spec line) for every finding
• Walks the original ask for silently dropped requirements
• Ends with exactly one next action — or "Stop. This work is done."

Install:
npx skills add HarjjotSinghh/cooked --skill cooked -g

Repo: https://github.com/HarjjotSinghh/cooked
```

## Show HN

**Title:** Show HN: /cooked – evidence-only "what's next" skill for coding agents

**Text:**

```text
After a feature is "done," agents love inventing chores: more tests, better error handling, monitoring, docs.

/cooked is a small Agent Skills skill that refuses that list. Every finding needs a file:line or command output. It ranks BLOCKING / WILL BITE / LOOSE ENDS, marks silently dropped requirements, and returns one next action — or "you cooked, stop."

Works via:
npx skills add HarjjotSinghh/cooked --skill cooked -g

Then /cooked in Claude Code, Codex, Cursor, etc.

https://github.com/HarjjotSinghh/cooked
```

## Reddit (r/ClaudeAI, r/cursor, r/ChatGPTCoding)

**Title:** /cooked – "did I cook or am I cooked?" skill after you finish a feature

**Body:** same as LinkedIn, plus install one-liner. Lead with the before/after blocks as fenced code.

## Discord (agent / skills servers)

```text
Shipped /cooked — post-feature audit skill.
Evidence or silence. One next move. Branded verdicts.

npx skills add HarjjotSinghh/cooked --skill cooked -g
https://github.com/HarjjotSinghh/cooked
```
