# LOST contribution-graph streak

This repo automatically commits on specific days between **2026-07-05** and
**2026-12-26** so that your GitHub contribution graph spells **LOST**.

## How it works
- `on_dates.json` lists the exact 53 calendar dates that need a commit.
- `.github/workflows/lost-streak.yml` runs every day at 12:00 UTC via GitHub
  Actions, checks if today is in that list, and if so makes one commit and
  pushes it — fully automatic, no manual steps after setup.

## One-time setup

1. Create a **new public repo** on GitHub (private repos only show up on your
   graph if you've enabled "Include private contributions" in your profile
   settings — public is simpler).
2. Push the contents of this folder to that repo's default branch (e.g. `main`).
3. Go to the repo's **Settings → Secrets and variables → Actions → Variables**
   and add two repository variables so the commits are attributed to *you*
   (otherwise they'll be attributed to `github-actions[bot]` and won't count
   on your graph):
   - `GIT_USER_NAME` → your GitHub username
   - `GIT_USER_EMAIL` → an email that is **verified on your GitHub account**.
     The easiest safe choice is your GitHub-provided "noreply" email, which
     you can find at:
     Settings → Emails → "Keep my email address private" → it shows something like
     `123456+username@users.noreply.github.com`
4. Make sure Actions are enabled for the repo (Settings → Actions → General →
   "Allow all actions").
5. That's it — leave it alone. Each day the workflow checks itself and commits
   only when needed.

## Testing it early
Go to the **Actions** tab → select the "LOST contribution streak" workflow →
"Run workflow" to trigger it manually and confirm it runs without errors
(it just won't commit unless today happens to be a pixel day).

## Notes
- GitHub determines which day a commit counts toward using UTC, so the
  12:00 UTC run time is a safe middle-of-the-day buffer.
- If a run ever fails (e.g. GitHub Actions outage) and misses a day, just
  re-run it manually from the Actions tab — it will still commit for "today"
  if today is a pixel day, though a strictly missed day in the past can't be
  recovered since real time has moved on.
- The grid: 25 weeks (columns), Sun→Sat (rows), 1 blank column padding on
  each side, letters L-O-S-T each 5 columns wide with 1-column gaps between.
