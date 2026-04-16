---
name: research-item
description: Research a warehouse fire incident and write or update its file in ./fires/.
---

Research the following and write an incident report using the template in `./.claude/skills/research-item/template.md`.

$0

---

## Steps

**1 — Fetch input URLs**

Use this fallback chain — stop at the first that returns usable content:

1. `WebFetch <url>` — preferred; returns clean text with no local cost
2. `./bin/fetch-url --extract <url>` — local fallback using trafilatura; use when WebFetch fails or is blocked
3. `./bin/fetch-url --og <url>` — last resort; returns only title/description/url (~50 tokens); enough for triage if full content is unavailable
4. `./bin/fetch-url <url>` (raw HTML) — **Threads URLs only**; extract post text with:
   ```
   grep -o '"text":"[^"]*"' <saved-file> | head -20
   ```

Exit code 2 from `--extract` means trafilatura got no content (JS-rendered or paywalled) — fall back to `--og`.

- If the input is a roundup or list of fires, treat each item as a separate incident.
- If the input is a statistical claim, verify against `./fires/history.md` only.

**2 — Classify before researching**

| Input type | Action |
|---|---|
| Single incident | Research → create/update file |
| List/roundup | Split into individual incidents, research each |
| Statistical claim | Verify against history.md |
| Pre-2026-04-07 with no direct link | Skip |
| No news coverage found | INDEX entry only, no file |

**3 — Research (parallel for multiple incidents)**

Spawn one subagent per incident simultaneously. Each agent searches for: local news, fire marshal/ATF statements, court filings. Agent prompt should include only: facility name, city/state, date, and the specific question (arson? cause? charges?).

Do not conflate warehouse labor fires with anti-Musk Tesla facility attacks — they are categorically different. Note the distinction if a source groups them.

**4 — Write or update the file**

- New incident: create `./fires/YYYY-MM-DD-{city-state}-{short-description}.md`
- Existing incident: compare new findings, update only what changed
- Pre-cutoff / no coverage: skip file creation

**5 — Update INDEX**

Edit `./fires/INDEX.md`: add new rows in date order, update At-a-Glance counts, mark unconfirmed incidents as *(no file — no news coverage found)*.
