# The Bozo League 🤡

Five idiots. One parlay. Permanent records.

A static site that reads the league's Google Sheet and renders standings, the
Bozo of the Week, the Bozo of the Year race, and the Hall of Shame. No backend,
no build step — one `index.html`.

## Deploy (GitHub Pages)

1. Create a repo (e.g. `bozo-league`) and upload `index.html` + this README.
2. Repo **Settings → Pages → Source: Deploy from a branch → main / (root)** → Save.
3. Site appears at `https://<username>.github.io/bozo-league/` in a minute or two.

## Wire up the Sheet

1. In Google Sheets: **Share → Anyone with the link → Viewer**.
2. Copy the Sheet ID from its URL (the long string between `/d/` and `/edit`).
3. In `index.html`, set `const SHEET_ID = "<that id>";`
4. Commit. The "DEMO DATA" chip flips to "LIVE".

Until `SHEET_ID` is set, the site renders built-in demo data.

## How it decides the Bozo banner

- Latest slate has ungraded picks → **TBD / sweat in progress**
- Graded, one loser, Bozo row logged → the Bozo, with SOLO badge
- Graded, multiple losers, no Bozo row yet → **IN COURT** (vote in progress)
- Graded, zero losses → **NOBODY / clean sweep**
- No picks at all → preseason mode

Data flows one way: Sheet → site. All stats are computed in the browser on
every page load. Edit the Sheet, refresh the page (Google caches published
sheet data for a few minutes).
