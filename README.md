# SMK AdobeCC Progress Dashboard

A single-page dashboard that tracks Adobe Creative Cloud installation progress across three schools. Data is read live from a published Google Sheet, so updating the sheet updates the page — no redeploy needed.

**Live site:** https://silvertechsynergy.github.io/smk-adobecc/

## Schools tracked

| Button | Google Sheet tab |
|---|---|
| SMK Tengku Ibrahim | T.Ibrahim |
| SMK Tengku Mizan Zainal Abidin | T.Mizan |
| SMK Binjai | Binjai |

## How it works

1. Click a school button to load that tab from Google Sheets (CSV).
2. Each PC appears as a card with its 3-step progress dots.
3. Click a PC card for details: Remote ID and status of each step.

Progress is counted as `done` (also accepts `yes` / `true`). Anything else is treated as pending.

## Sheet format

Each tab needs these column headers in row 1:

| pc-id | remote-id | adobecc-installer | adobecc-installed | license-installed |
|---|---|---|---|---|
| PC-1 | 466 359 007 | done | pending | pending |

The number of PCs is read from the sheet, so adding or removing rows needs no code change.

## Updating the data

Edit the Google Sheet, then click **Refresh** on the page (or reload it).

The sheet must remain published: **File → Share → Publish to web**.

## Changing sheet links or school names

Open `index.html` and edit the config near the top of the `<script>` section:

```js
const SHEETS = {
  "T.Ibrahim": "https://docs.google.com/.../pub?gid=0&single=true&output=csv",
  ...
};
const DISPLAY_NAMES = {
  "T.Ibrahim": "SMK Tengku Ibrahim",
  ...
};
```

The key (e.g. `"T.Ibrahim"`) links the two objects together. To add a school, add an entry to both.

## Features

- Light / dark mode (remembers your choice)
- Live refresh with last-updated timestamp
- Responsive layout

### Design theme

The visual theme follows the RootSys design language:

- **Light:** warm cream "paper" surface (`#FAF7F1`) with warm brown text and an amber accent (`#C4954A`)
- **Dark:** deep teal night surface (`#0B1415`) with warm amber accent (`#E8B04E`)
- **Fonts:** Archivo for headings, Inter for body text
- **Shapes:** soft 12–16px radii, pill-shaped buttons and badges

## Files

| File | Purpose |
|---|---|
| `index.html` | The dashboard (HTML, CSS and JavaScript) |
| `sts.png` | Silver Tech Synergy logo |
| `favicon.png` | Browser tab icon |

## Deployment

Hosted with GitHub Pages from the `main` branch, root folder.

To publish a change:

```
git add -A
git commit -m "Update dashboard"
git push
```

---

Silver Tech Synergy
