# MatPat & Theorist Channels - YouTube Analytics Project

Analysis of The Game Theorists, The Film Theorists, The Food Theorists, The Style Theorists and GTLive.

## IMPORTANT: what is real and what is simulated
| Component | Status |
|---|---|
| `data/channel_snapshots.csv`, `channel_meta.csv`, `combined_snapshots.csv` | **Real** public figures (Wikipedia-derived mirrors; each row has `source` and `confidence`). Some sources lag or disagree. Verify on YouTube before publishing. |
| `data/videos_simulated.csv` (2,280 rows) | **Simulated.** Not real videos. Calibrated so each channel's total views match real totals. |
| Models and video-level charts (fig05-fig12) | Run on the simulated data. They demonstrate the method and say nothing about real viewer behaviour. |

To use real video data: `python src/collect_youtube_data.py --api-key YOUR_KEY`, then point `02_analyze.py` at `data/videos_real.csv` (add `topic` and title-feature columns).

## Contents
- `MatPat_YouTube_Analytics_Paper.pdf` - 10-page research paper (figures, diagrams, tables, limitations)
- `MatPat_YouTube_Analytics_Dataset.xlsx` - workbook: README, formula-driven Channel_Summary, snapshots, meta, simulated videos, OLS coefficients
- `dashboard.html` - interactive dashboard (open in a browser; needs internet for Chart.js from cdnjs)
- `figures/` - 12 graph PNGs (`fig01-04` real, `fig05-12` simulated)
- `diagrams/` - 4 diagram PNGs (pipeline, model architecture, data schema, network)
- `src/` - reproducible pipeline

## Run
```
pip install pandas numpy scipy scikit-learn matplotlib openpyxl reportlab pillow
python src/01_build_data.py
python src/02_analyze.py
python src/03_excel.py
python src/04_paper.py
python src/05_dashboard_readme.py
```

## Headline results (real data)
- Mar 2024 subscribers: Game Theory 18.4M, Film Theory 12.3M, Food Theory 4.83M, GTLive 3.3M, Style Theory 2.09M.
- Avg views per video (May 2023): Film Theory 6.38M, Food Theory 4.51M, Style Theory 1.74M, GTLive 0.59M.
- Annualised subscriber growth May 2023 to Mar 2024: {'Game Theory': 6.7, 'Film Theory': 3.9, 'Food Theory': 7.5, 'Style Theory': 32.7, 'GTLive': 6.0}.

## Limitations
Secondary-source snapshots; short growth window; simulated video-level data; observational design. Data ends March 2024 (MatPat's retirement from hosting).
