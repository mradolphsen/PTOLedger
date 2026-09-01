# PTO Ledger

A single-page PTO accrual tracker, calibrated to a Wed–Tue, 14-day pay period
grid. Runs entirely in the browser — no server required — and can sync its
data to a small JSON file in this repo so the same numbers follow you between
computers.

## 1. Put it on GitHub Pages

1. Create a new **repository** on GitHub (public or private — private works
   fine, you'll just always use a token to read and write it).
2. Upload `index.html` to the root of the repo (drag-and-drop on the GitHub
   web UI works, or `git add / commit / push`).
3. Go to **Settings → Pages**, set the source to **Deploy from a branch**,
   pick `main` and `/ (root)`, and save.
4. GitHub gives you a URL like `https://yourname.github.io/pto-ledger/` —
   bookmark that on both computers.

## 2. Create a token so the page can save your data

The page stores your entries as a JSON file inside the same repo, using the
GitHub API. To let it write to the repo, create a **fine-grained personal
access token**:

1. GitHub → **Settings → Developer settings → Personal access tokens →
   Fine-grained tokens → Generate new token**.
2. Under **Repository access**, choose **Only select repositories** and pick
   this repo.
3. Under **Permissions → Repository permissions**, set **Contents** to
   **Read and write**. Leave everything else as **No access**.
4. Generate it and copy the token — GitHub only shows it once.

You'll paste this into the app's Settings panel (username, repo name,
branch, and the token). It's saved only in that browser's local storage, not
in the data file itself — you'll need to generate and paste a token on each
computer you use.

## 3. First-time setup in the app

Open the page, expand **Settings**, and check:

- **Start date** — defaults to Jul 22, 2024.
- **Default FTE** — defaults to 0.75; change it if that's not right.
- **A known pay period end date** — defaults to Aug 25, 2026 (confirmed from
  a pay stub). This calibrates which Tuesdays are period ends; you shouldn't
  need to touch it unless your employer's grid shifts.
- **Accrual tiers** — pre-filled from your employer's table. Edit or add
  rows if your policy differs or changes.
- **Sync to GitHub** — enter your username, repo, and token, then click
  **Save to GitHub** once to create the data file. Turn on **auto-sync** so
  every change is saved without a click.

On your second computer, enter the same GitHub username/repo/token and click
**Load from GitHub** to pull your data down.

## Notes

- The ledger only warns when your balance is above the max accrual cap — it
  doesn't automatically forfeit hours, since your employer's actual payroll
  system is the source of truth for that.
- A **backup export/import** (plain JSON file) is also available in
  Settings, independent of GitHub, if you ever want an offline copy.
- This is a personal calculator, not an official record — always confirm
  balances against your employer's system before making PTO decisions.
