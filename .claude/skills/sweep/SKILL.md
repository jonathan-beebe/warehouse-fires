---
name: sweep
description: Scans multiple sources to discover new warehouse and industrial fire incidents not yet documented in the research index.
---

Surface fire leads not yet in `./fires/`. Output a leads report only — do not create incident files (that is `/research-item`'s job).

---

## Step 1 — Load known incidents

Run `Glob("fires/*.md")` to get all documented incident filenames. Filenames encode date + location — no need to read INDEX.md.

---

## Step 2 — Search in parallel (2 agents)

Take into account any user research they passed in: $0

**Agent 1 — News & trade press.** WebSearch for:
- `warehouse fire 2026 site:apnews.com OR site:reuters.com`
- `"distribution center fire" 2026`
- `"industrial fire" arson 2026`
- Industrial Fire World, Insurance Journal, FireRescue1

Return: date, city/state, facility name, 1-sentence summary, URL.

**Agent 2 — Social media & official sources.** Search:
- Reddit: r/antiwork, r/news, r/labor + local subs — keyword `warehouse fire`
- X/Twitter: `warehouse fire`, `arson warehouse 2026`
- ATF press releases, U.S. Attorney announcements, state fire marshal pages (CA, OH, NY, NC, NJ, GA, IL)

Return: same fields. Flag roundup posts — extract each fire listed as a separate lead.

---

## Step 3 — Deduplicate and classify

Cross-reference agent results against filenames from Step 1. Drop anything already documented.

Classify each remaining lead:
- **Confirmed new** — credible news source, not in fires/
- **Unconfirmed** — social media only, no news found
- **Needs disambiguation** — possible match with known fire, date/location unclear

---

## Step 4 — Output leads report

```
## Sweep — [Date]
New: N | Unconfirmed: N | Skipped (known): N

### New Leads
1. [Date] — [City, ST]: [Facility] — [1 sentence]. [URL] | Labor angle: Y/N/Unknown

### Unconfirmed (social media only)
- [Date/approx] — [Location]: [Description]. [URL]

### Notes
[Roundup posts with more leads, clusters, notable patterns — or "nothing notable".]
```

Tesla/Musk retail facility fires: include only as a footnote, clearly labeled as a separate phenomenon from warehouse labor fires.
