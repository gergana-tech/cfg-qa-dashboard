# CFG · Coforge QA Dashboard

A live, interactive QA analytics dashboard for the CFG/Coforge customer support team.

## Live app

Hosted on GitHub Pages → **[your-username.github.io/cfg-qa-dashboard]()**

## What it does

- Full QA review analytics across 1,223 historical reviews (Sep 2025 – May 2026)
- Filter by agent (multi-select), year, month, channel, and pass/fail result
- Five pages: Overview · Agent Scores · Weekly View · Failure Analysis · Roster
- Failure Analysis has three sub-tabs: By Question · By Topic of Enquiry · Knowledge Gap
- Every score, count, and percentage is clickable → opens a drill-down modal showing exact reviews
- Data persists in the browser via `localStorage` — survives page refreshes and browser restarts
- **+ Add review** — add individual reviews via a form
- **↑ Import CSV** — upload a CSV export from your QA tool to append new data

## How to deploy (GitHub Pages)

1. Create a new repository on GitHub (e.g. `cfg-qa-dashboard`)
2. Upload all files from this folder to the repo root
3. Go to **Settings → Pages**
4. Under **Source**, select **Deploy from a branch**
5. Choose **main** branch, **/ (root)** folder → click Save
6. Wait ~60 seconds → your app is live at `https://your-username.github.io/cfg-qa-dashboard`

## How to add new monthly data

Open the live app and click **↑ Import CSV** in the top-right corner.

The importer auto-maps columns from a standard QA tool export. Required columns:

| Column | Description |
|--------|-------------|
| `Agent` | Agent full name |
| `Relative score` | Numeric score 0–100 |
| `Pass` | `Yes` or `No` |
| `Conversation month` | e.g. `Jun` |
| `Conversation week` | Week number |
| `Source` | `Voice` or anything else (mapped to Non Voice) |
| `ToE` | Topic of Enquiry category |

All question fail-flag columns (e.g. `Documentation.1`, `Grammar and spelling`) and `Knowledge Gap` are also mapped automatically if present.

## Data storage

Data is stored in `localStorage` in each user's browser. This means:
- The 1,223 seed reviews are embedded in `index.html` and loaded on first visit
- Any reviews added via the form or CSV import persist across sessions in that browser
- Different users on different devices have independent storage

## Stack

Pure frontend — no backend, no database, no build step required.

- [React 18](https://react.dev/) via CDN
- [Recharts](https://recharts.org/) for charts
- [Babel Standalone](https://babeljs.io/docs/babel-standalone) for JSX transpilation in-browser
- `localStorage` for data persistence
