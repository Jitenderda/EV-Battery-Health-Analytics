# data/

⚠️ **No data files are stored in this repository.**

The source dataset lives on Kaggle:
[Electric Vehicle (EV) Battery Degradation & Charge](https://www.kaggle.com/datasets/bertnardomariouskono/electric-vehicle-ev-battery-degradation-and-charge)

## Why nothing is committed here

- Keeps the repository lightweight
- The dataset is publicly available from the original source
- Licensing stays with the original publisher

## Where the data lives during the project

| Stage | Location |
|---|---|
| Raw dataset | Kaggle |
| Phase 1 — SQL | Imported into SQL Server (`EV_Projects.dbo.ev_battery_data`) |
| Phase 2 — Python | Google Colab (loads the CSV directly) |
| Phase 3 — Power BI | Cleaned export produced by Phase 2 |

## Tables used in Phase 1

- `dbo.ev_battery_data` — 10,000 rows, 13 columns
- `dbo.car_info` — lookup table: `Car_Model` → `Manufacturer_Country`, `Launch_Year`

Column details are in the main [README](../README.md).
