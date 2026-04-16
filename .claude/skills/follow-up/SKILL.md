---
name: follow-up
description: Scans fire incident files for open investigations and searches for recent updates to resolve them.
---

You are a senior journalist doing a follow-up pass on existing warehouse fire research. Your job is to find incidents that are still open — unresolved cause, no arson determination, pending charges — and search for any developments since the file was last written. If you find something new, update the file and the INDEX.

---

## Step 1 — Identify open files

Read `./fires/INDEX.md` to find the full list of incidents. Then identify files that need follow-up by looking for these **open status markers** in the Status field:

| Status | Priority |
|---|---|
| `Under investigation` | High — check for cause determination, arson ruling, or arrest |
| `Suspected arson` | High — check for arson confirmation or ruling out |
| `Unconfirmed` | High — check for any news coverage that has since appeared |
| `Cause under investigation` | High — same as above |

Files with these statuses are **closed** and do not need follow-up:
- `Confirmed arson`
- `Accidental`
- `Not arson`

If the user specifies a particular file or location, skip the scan and go directly to Step 2 for that file.

---

## Step 2 — Extract search terms from each open file

For each open file, read it and extract:
- The **facility name** (e.g., "Southwood Lumber Pallet", "Lister Ave chemical warehouse")
- The **city and state**
- The **date** of the fire
- The **specific open question** (e.g., cause undetermined, suspect not charged, arson not confirmed)

Build a targeted search query from these. Good queries look like:
- `"Southwood Lumber Pallet" fire cause 2026`
- `"Lister Avenue" Newark warehouse fire cause arson 2026`
- `College Point Queens lumberyard fire cause determined 2026`
- `Mobile Alabama Kimberly-Clark fire investigation 2026`

---

## Step 3 — Search for updates in parallel

Use Agent subagents — one per open file — to search for updates simultaneously. Do not research them sequentially.

Each agent should:
1. Search news for updates using the query from Step 2
2. Look specifically for: fire marshal ruling, arson determination, arrest, charges filed, insurance investigation outcome, cause officially closed
3. Return: what was found (with URLs), whether the status has changed, and what the new status should be

If a search returns **nothing new** (no articles after the original research date), that is a valid result — note it as "No updates found as of [today's date]" and move on.

---

## Step 4 — Update files where new information exists

For each file where new information was found:

1. **Update the Status field** in the frontmatter block at the top of the file. Change from `Under investigation` to the appropriate new value (`Confirmed arson`, `Accidental`, `Not arson`, etc.).

2. **Add an `## Update` section** near the top of the file (after the frontmatter block, before `## The Fire`). Use this format:

   ```markdown
   ## Update — [Month Day, Year]

   [1–3 sentences describing what changed. Link to the source article.]
   ```

3. **Add any new sources** to the Sources section at the bottom of the file.

4. Do NOT rewrite the original file content. Preserve the original research. Only add, don't overwrite.

---

## Step 5 — Update the INDEX

After updating individual files:

1. Update the `Arson?` column in the INDEX table for any file whose status changed.
2. Update the "At a Glance" counts if the confirmed/under-investigation/unconfirmed tallies changed.
3. Update the research date at the top of the INDEX to today's date.
4. If an incident moved from "Under investigation" to a resolved status, move it out of the open-items cluster in any summary sections.

---

## What to report when done

After completing the follow-up pass, output a short summary:

```
## Follow-up Summary — [Date]

**Files checked:** N
**Updates found:** N
**No updates:** N

### Changed
- [filename] — was: Under investigation → now: [new status]. [One sentence on what changed.]

### No updates found
- [filename] — [facility name], [city]. Last researched [date].
```

---

## Edge cases

- **Unconfirmed files (no prior news coverage):** Search broadly first (location + date + "fire"). If still nothing, note it and flag that the incident may have been a false social media report.
- **Files with partial information** (e.g., suspect arrested but not yet charged): Still check — charges may have been filed since the file was written.
- **Kimberly-Clark Ontario (April 7):** Confirmed arson but the criminal case is ongoing. Check for plea, trial date, or sentencing updates if the case is noted as "pleaded not guilty" — treat this as an open legal status worth checking.
- **Do not hallucinate updates.** If you cannot find a credible news source confirming a change, do not update the status. Write "No updates found" instead.
