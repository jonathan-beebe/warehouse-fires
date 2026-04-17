# Warehouse Fires Research Project

## Purpose

We are building a **source of truth** for warehouse and industrial fires in the United States following the April 7, 2026 Kimberly-Clark Distribution Center arson in Ontario, California.

That fire — set by an NFI Industries warehouse worker who filmed himself and said *"All you had to do was pay us enough to live"* — was explicitly framed as a labor protest. It sparked national conversation and a wave of online noise conflating unrelated fires with deliberate acts of economic protest.

This project exists to **cut through that noise**: rigorously document what actually happened, what is confirmed, what is speculation, and what is still under investigation. Every incident gets its own file grounded in verifiable sources.

---

## Research Process

Only look for reports of fires occurring in the year 2026. We are not interested in historical fires earlier that, unless they have a direct link or special relevance to current events.

### Step 1 — Social Media Sweep

Start with social media to find what's circulating and to surface fire incidents that may not yet have major news coverage:

- **Threads** — search fire-related posts and accounts covering news/labor/protest topics
- **Reddit** — r/antiwork, r/news, local subreddits for cities with reported fires
- **X / Twitter** — keyword searches for warehouse fire, arson, worker protest

Social media posts are used to **identify leads**, not as primary evidence. They are cited with full URLs and note the platform, account handle, and approximate post date.

### Step 2 — News Aggregators and Ground News

Cross-reference social media leads against news aggregators to assess coverage breadth and source diversity:

- **Ground News** — check bias ratings and coverage spread across outlets
- **Google News** — surface recent articles
- **Substack / independent journalism** — useful for synthesis pieces

### Step 3 — Local News Investigation

Local news is the gold standard for incident-specific facts (exact address, fire department response details, cause determination, ownership, injuries). For each incident we seek:

- Local TV affiliates (ABC, NBC, CBS, Fox) in the relevant market
- Local newspapers and digital outlets
- Official press releases from fire departments, police departments, or county emergency management
- Wire services (AP, Reuters) when available

### Step 4 — Official Sources

For confirmed arson cases, supplement with:

- U.S. Attorney's Office / DOJ press releases
- ATF statements
- Court filings and charging documents
- Wikipedia (as a secondary aggregator, with original sources verified)

---

## File Conventions

### Location

All incident files live in `./fires/`.

### Naming

```
fires/YYYY-MM-DD-{city-state}-{short-description}.md
```

Use the date the fire started (not when it was reported or when arrests were made). If a date is uncertain or spans two calendar days, use the start date with a note.

### File Structure

Each incident file should include:

```markdown
# YYYY-MM-DD — City, State: Facility Name

**Status:** [Confirmed arson / Suspected arson / Under investigation / Accidental / Not arson]
**Labor/Wage Connection:** [Explicit / Indirect / None / Unknown]
**Date/Time:** [Date and time fire began]
**Location:** [Full street address if known, neighborhood, city, state]

## The Fire
[What burned, size, response, outcome]

## Cause
[What is known or confirmed about how the fire started]

## Ownership & Operations
[Who owns/operates the facility; relevant corporate context]

## Suspect / Arrests
[If applicable]

## Labor Connection
[Explicit discussion of any wage/labor/protest angle]

## Social Media Reaction
[If significant]

## Sources
[Full citations — see format below]
```

### Source Citation Format

**Every source must be cited twice: once as a full textual description, and once as a live hyperlink.** These are not optional — a citation without a live link is incomplete, and a link without a textual description is insufficient.

Always include:
- Full hyperlink with descriptive title (the link text should be human-readable, not a bare URL)
- Publication/outlet name
- Date of publication (not access date — but note if a source was live at time of research)

```markdown
- [Article Title — Outlet Name](https://url)
```

For research reports and official documents, include both the landing page and the direct PDF link where both exist:

```markdown
- [Report Title — Publisher (Author, Date)](https://direct-pdf-url). Landing page: [publisher.org/page](https://landing-page-url).
```

For social media:
```markdown
- [Threads @handle — post description](https://threads.com/...)
- [Reddit r/subreddit — post title](https://reddit.com/...)
```

**Access date for this research:** All sources in this repository were accessed on or around **April 14, 2026** unless otherwise noted in the file.

---

## Index

`./fires/INDEX.md` is the master cross-reference table. It lists every documented incident with:
- Date, location, facility
- Arson status and labor connection
- Link to the individual file
- Date discrepancies (when the user-reported date differs from confirmed news dates)

Update the INDEX whenever a new incident file is added or an existing file is materially updated.

---

## Ground Rules

- **Confirmed** means a law enforcement charge, official fire marshal determination, or court document says so.
- **Suspected** or **Under investigation** means fire marshals have not ruled and no charges have been filed.
- **Unconfirmed** means the incident was reported on social media but no news coverage was found.
- Never elevate social media speculation to the status of confirmed fact.
- When a date in social media or a user source conflicts with verified news reporting, note the discrepancy in the file and use the verified date.
- Always flag if a fire has no confirmed labor connection, even if it's part of a cluster generating online speculation.

---

## Current Scope

Fires documented as of April 14, 2026:

| Date | Location | Confirmed Arson + Labor Link? |
|---|---|---|
| 2026-01-05 | Joliet, IL (Amazon) | No |
| 2026-03-16 | Flushing, Queens, NY (residential) | Yes — job loss rage (4 killed) |
| **2026-04-07** | **Ontario, CA (Kimberly-Clark)** | **Yes — explicit wage protest** |
| 2026-04-08 | West Jefferson, OH (Amazon) | No — solar panels |
| 2026-04-08/09 | East Providence, RI (Aspen Aerogels) | No — ethanol vapors |
| 2026-04-09 | Newark, NJ (chemical warehouse) | Under investigation |
| 2026-04-10 | Lawrenceville, GA (GSL Transfer Station) | No — accidental |
| 2026-04-10/11 | College Point, Queens, NY (lumberyard) | Under investigation |
| 2026-04-11 | Bakersfield, CA (abandoned warehouse) | Under investigation |
| 2026-04-11/12 | Wayne County, OH (Southwood Lumber Pallet) | Under investigation |
| 2026-04-11 | Cahokia Heights, IL (Patterson Towing) | No — EV battery |
| 2026-04-13 | West Jefferson, NC (Amazon, alleged) | Unconfirmed |
