# notebooks/

Phase 2 — Python EDA notebooks (Google Colab).

**Status:** ⬜ Not started — Phase 2 begins Day 15.

## Planned notebooks

| Notebook | Days | Focus |
|---|---|---|
| `01_loading_and_cleaning.ipynb` | 15–16 | Load the CSV, inspect structure, handle missing values (`df.info()`, `df.describe()`) |
| `02_exploration.ipynb` | 17–18 | `groupby`, sorting, filtering, bar / line / scatter plots |
| `03_relationships.ipynb` | 19–20 | Heatmaps, boxplots, correlation matrix |
| `04_outliers_and_features.ipynb` | 21–22 | IQR, Z-score, engineered columns, impact on SoH |
| `05_feature_importance.ipynb` | 23–24 | scikit-learn, Random Forest feature importance |

## Conventions

- One notebook per topic — no giant catch-all notebooks
- Each notebook opens with a markdown cell stating the question it answers
- Findings written in my own words after each chart, not just plotted

## Goal

Statistically confirm — or challenge — the Phase 1 SQL findings, especially that
fast charging, temperature and charging cycles drive battery degradation.
