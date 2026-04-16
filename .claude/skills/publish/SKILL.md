---
name: publish
description: Turn the markdown into html files and publish to the web.
---

You are publishing the Warehouse Fires research site. Follow these steps exactly.

---

## Step 1 — Build the HTML

Run the build script:

```
./bin/build
```

This converts all markdown files in `./fires/` to HTML in `./web/`. Watch the output for errors. If the build fails, report the error and stop — do not proceed to commit or push.

---

## Step 2 — Stage all changes

Stage everything that changed — both the source markdown files and the built HTML output:

```
git add fires/ web/
```

---

## Step 3 — Summarize what changed

Run `git diff --cached --stat` to see what files are staged. If nothing is staged, report "Nothing to publish — working tree is clean" and stop.

---

## Step 4 — Commit

Write a concise commit message summarizing what changed. Follow these patterns:

- If only HTML was rebuilt (no markdown changes): `Rebuild site`
- If new incident files were added: `Add [N] new incident(s): [short names]`
- If existing files were updated: `Update [facility names / locations]`
- If a mix: `Add [X], update [Y]; rebuild site`

Format:

```
git commit -m "<message>

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>"
```

---

## Step 5 — Push to GitHub

```
git push origin main
```

If the push fails (e.g. remote is ahead), report the error and ask the user how to proceed. Do not force-push.

---

## Step 6 — Report

After a successful push, output:

```
Published to github.com/jonathan-beebe/warehouse-fires

Files built: N HTML pages
Commit: <short hash> — <message>
```
