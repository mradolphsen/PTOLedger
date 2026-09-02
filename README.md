# PTO Ledger

A single-page PTO accrual tracker, calibrated to a Wed–Tue, 14-day pay period
grid and styled with Mayo Clinic's colors and typefaces. Runs entirely in
the browser — no server required — and syncs its data to a JSON file in the
`mradolphsen/PTOcalculator` repo so the same numbers follow you between
computers.

## 1. Put it on GitHub Pages

`index.html` and `README.md` are already in the repo. To publish it:

1. Go to **Settings → Pages** in this repo, set the source to **Deploy from
   a branch**, pick `main` and `/ (root)`, and save.
2. GitHub gives you a URL like `https://mradolphsen.github.io/PTOcalculator/`
   — bookmark that on both computers.

## 2. Create a token so the page can save your data

The page stores your entries as `data/pto-data.json` in this same repo,
using the GitHub API. To let it write to the repo, create a **fine-grained
personal access token**:

1. GitHub → **Settings → Developer settings → Personal access tokens →
   Fine-grained tokens → Generate new token**.
2. Under **Repository access**, choose **Only select repositories** and pick
   `PTOcalculator`.
3. Under **Permissions → Repository permissions**, set **Contents** to
   **Read and write**. Leave everything else as **No access**.
4. Generate it and copy the token — GitHub only shows it once.

Paste it into the app's Settings panel, under **Sync to GitHub**. It's saved
only in that browser's local storage, not in the data file itself and not
anywhere in the page's code — you'll need to generate and paste a token on
each computer you use.

## 3. First-time setup in the app

Open the page and click the **⚙ gear icon** in the top right to open Settings:

- **Start date** — defaults to Jul 22, 2024.
- **Default FTE** — defaults to 1.0; change it if that's not right.
- **A known pay period end date** — defaults to Aug 25, 2026 (confirmed from
  a pay stub). This calibrates which Tuesdays are period ends; you shouldn't
  need to touch it unless your employer's grid shifts.
- **Accrual tiers** — pre-filled from your employer's table. Edit or add
  rows if your policy differs or changes.
- **Sync to GitHub** — paste your token, then click **Save to GitHub** once
  to create the data file. **Autosave** is on by default, so after that,
  changes save on their own.

Close Settings by clicking the ✕, clicking outside the dialog, or pressing
Escape. On your second computer, paste the same token and click **Load from
GitHub** to pull your data down.

## Reading the ledger

Pay periods are grouped into collapsible year sections (2024, 2025, 2026…),
each showing its period count and ending balance in the header — click a
year to expand it. The current year opens automatically. Each row shows:

- **Pay period** — e.g. `Jul 17 - Jul 30, 2024`
- **Pay date** — when that period is actually paid out
- **Earning rate** — hours accrued that period; editable, so a partial
  period (like a hire date mid-period) can be corrected by hand
- **FTE** — editable per row, in case it changed over time
- **Used** — hours of PTO you took that period; type it in directly
- **Beginning balance** — what you had available to use as of the *start*
  of that period, before that period's own earning posts (so the very
  first period always begins at 0.00)
- **Max** — the accrual cap for that period at that tier and FTE; a row is
  highlighted if your beginning balance was already over it

## Notes

- The GitHub repo and file path are fixed in the page's code (not shown or
  editable in the Settings UI) — only the token is entered per device.
- The ledger only warns when your balance is above the max accrual cap — it
  doesn't automatically forfeit hours, since your employer's actual payroll
  system is the source of truth for that.
- A **backup export/import** (plain JSON file) is also available in
  Settings, independent of GitHub, if you ever want an offline copy.
- This is a personal calculator, not an official record — always confirm
  balances against your employer's system before making PTO decisions.
