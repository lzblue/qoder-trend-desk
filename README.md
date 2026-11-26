# Qoder Trend Desk — submission

Moomoo × Qoder AI Paper Trading Agent Challenge, 2026. Paper account `5830104`, $100,000 NAV.

Start here: **[index.html](index.html)** (or the GitHub Pages link once enabled) — it carries the deck, the demo capture, and the download for the runnable package.

| File | What it is |
|---|---|
| `qoder-trend-desk-submission.pdf` | The 8-page deck, exported from the .pptx (560,934 B) |
| `qoder-trend-desk-submission.pptx` | The deck as generated, sha256 `c2824ac96cb8b3e49af1101613e393a5ad3175cf2fde1409309789c456afdf40` (1,545,595 B) |
| `trend-desk-submission-package.zip` | The runnable package, 103 files / 3.3 MB: dashboard app, the six skills as pinned in the cloud with a per-file SHA-256 manifest, the replay engine and its recorded outputs, the decision journal, the fills/orders/equity logs, and a dated read-only snapshot of the cloud configuration |
| `dashboard-capture.gif` | The dashboard running on the recorded logs |

Inside the package, `PACKAGE-README.md` maps every figure in the deck to the file that produces it, and
`docs/submission/trading-journal.md` §4 is the backtest method and result tables.

## Run the dashboard (from inside the unzipped package)

```bash
cd app
npm install
cp .env.example .env      # paste your own PAT into .env
npm start                 # http://localhost:4173
```

## Re-run the backtest (from inside the unzipped package)

```bash
cd backtest/intraday
node build_store.mjs        # fetches 5-minute bars through the moomoo MCP
python3 build_regimes.py
python3 replay.py           # -> replay_out.json
```

The raw bar store is not shipped (broker quota); the recorded outputs it produced are.

## Credential policy

No token is in this repository or in the package. `.env` is excluded and `.env.example` carries an empty
`QODER_PAT=`. All trading is paper-only; the live-order tool family is denied by configuration on every
template.
