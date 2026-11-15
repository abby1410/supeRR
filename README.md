# Pressure Ratings Lab

[![Deploy to GitHub Pages](https://github.com/abby1410/supeRR/actions/workflows/pages.yml/badge.svg)](https://github.com/abby1410/supeRR/actions/workflows/pages.yml)

**Explore who performs when a T20 cricket match is under pressure—and how reliable those ratings are.**

[Open the live dashboard](https://abby1410.github.io/supeRR/)

Pressure Ratings Lab is a responsive, interactive dashboard for exploring pressure performance in T20 cricket. It presents player rankings alongside the match context, component metrics, and uncertainty behind those rankings.

## Explore the dashboard

- **Rankings:** Browse eligible batters and bowlers, search and sort the table, and select a player to inspect their statistics and rating breakdown.
- **What is pressure:** Explore how pressure varies across innings, overs, and chase situations, alongside model validation and win-probability calibration.
- **Clutch:** Compare players' pressure performance with their performance in normal situations, and examine whether the difference appears repeatable.
- **Reliability:** See rank ranges from match resampling, sensitivity to alternative settings, and split-half reliability.
- **Accessible, responsive design:** Use the dashboard on desktop or mobile, with keyboard-visible focus states and light/dark color schemes.

## About the ratings

A delivery is treated as high pressure when its possible outcomes can have a large effect on the batting side's win probability. The model accounts for the asking rate, wickets in hand, balls remaining, and how close the match is.

The composite rating combines five measures:

| Component | Weight |
| --- | ---: |
| Pressure-adjusted net runs above expectation | 35% |
| Observed pressure-only net runs above expectation | 30% |
| Win probability added | 15% |
| Pressure lift over normal situations | 10% |
| Consistency | 10% |

Ratings are shrunk toward the league average to temper small-sample results. The dashboard applies minimum sample requirements of 100 balls and 12 matches for batters, and 150 balls and 12 matches for bowlers. It also shows uncertainty and sensitivity analyses so a rank is not presented without context.

The dashboard contains a **precomputed snapshot** covering **867 matches** and **200,961 deliveries** from **January 22, 2022 through November 1, 2026**. It does not fetch live scores or update its data automatically. The live site shows the current committed snapshot.

## Run locally

No build step, package installation, or backend is required. Open [`index.html`](./index.html) directly in a modern browser, or serve the project locally:

```sh
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## Deployment

The site is deployed to GitHub Pages from the `main` branch by [`.github/workflows/pages.yml`](./.github/workflows/pages.yml). Each push to `main` uploads the static project files and deploys them; the workflow can also be started manually from the **Actions** tab. There is no build process or runtime dependency.

## Project structure

```text
.
├── index.html                 # Dashboard, styles, JavaScript, and embedded data
├── dashboard.html             # Redirect to the current dashboard URL
├── README.md
└── .github/
    └── workflows/
        └── pages.yml          # GitHub Pages deployment
```
