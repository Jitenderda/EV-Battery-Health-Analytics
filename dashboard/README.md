# dashboard/

Phase 3 — Power BI dashboard.

**Status:** ⬜ Not started — Phase 3 begins Day 25.

## Planned report structure (3 pages)

### Page 1 — Fleet KPIs
- Total vehicles, average SoH, average internal resistance
- Health distribution (Healthy / Warning / Critical)
- Slicers: battery type, car model, manufacturer country

### Page 2 — Risk Tiers
- High-risk vehicle count and vehicle-level list
- Risk by usage level (Light / Moderate / Heavy)
- Drill-through to vehicle detail

### Page 3 — Model Comparison
- Average SoH by model and battery chemistry
- Internal resistance comparison (LFP vs NMC)
- Country-level health view

## Planned DAX measures

- `Avg SoH %`
- `Risk Vehicle Count`
- `% Vehicles Below Threshold`
- `Fast Charge Impact` — SoH delta across fast-charge bands

## Files

`.pbix` files and dashboard exports go here.
Screenshots of the finished pages go in [`../screenshots/`](../screenshots/).
