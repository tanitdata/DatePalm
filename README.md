# DatePalm

Satellite-based monitoring of aquifer sustainability and climate–yield
decoupling in southern Tunisia's date palm oases (2002–2024).

**Associated paper:** "Emerging climate–yield re-coupling in overexploited
date palm oases: satellite evidence from a 22-year temporal decoupling
index in southern Tunisia" — submitted to *Agricultural Water Management*.

## What this repository contains

- **`notebooks/`** — Two Colab notebooks reproducing the complete analysis:
  - `DatePalm_GEE_Data_Pipeline.ipynb` — Satellite data extraction (MODIS,
    ERA5-Land, CHIRPS, Sentinel-2, GRACE/GRACE-FO), ONAGRI/CRDA data
    harmonization, master dataset compilation
  - `DatePalm_FeatureEng_Modeling.ipynb` — Feature engineering (GDD, VPD,
    DTR, phenological windows), anomaly-based ML modeling (Ridge, Random
    Forest, XGBoost), temporal decoupling analysis, area integration,
    and the yield/ha critical test

- **`data/`** — All input and compiled datasets:
  - `raw_gee/` — Individual satellite extraction CSVs from Google Earth Engine
  - `onagri/` — ONAGRI production data and CRDA aquifer bulletins
  - `compiled/` — Master analysis tables ready for modeling
  - `area/` — Stage 1 persistent-NDVI oasis area estimates (2002–2024)
  - `grace_podaac/` — Download instructions for the GRACE NetCDF

- **`results/`** — Figures, metrics, and diagnostic outputs from the analysis

- **`documentation/`** — Thesis outline and connex PFE specification (see folder README)

## Key findings

1. **Yield forecasting fails in irrigated oases.** No ML model outperforms
   a naive trend baseline (~4.2% MAPE). All models return negative R² on
   yield anomaly prediction.

2. **GRACE reveals −16.6 cm groundwater loss** over 22 years, with the
   depletion rate tripling from −0.44 cm/yr (2002–2012) to −1.19 cm/yr
   (2012–2024).

3. **A temporal decoupling index detects emerging vulnerability.** Under
   leakage-free linear detrending, Kébili's VPD–yield/ha coupling increases
   at +0.031/yr (HAC p = 3.7×10⁻⁶). The signal survives area normalization
   (Δ|r| = +0.444) and is robust to break-year choice and placebo-feature tests.

## Data sources

| Source | Product | Resolution | Period |
|--------|---------|-----------|--------|
| MODIS | MOD13A2 NDVI, MOD11A2 LST | 1 km | 2002–2024 |
| ERA5-Land | Monthly aggregates | 9 km | 2002–2024 |
| CHIRPS | Daily precipitation | 5 km | 2002–2024 |
| GRACE/GRACE-FO | JPL Mascon RL06.3M v04 | ~50 km | 2002–2024 |
| Sentinel-2 | L2A NDVI/NDWI | 10 m | 2015–2024 |
| ONAGRI | Date production (tonnes) | Governorate | 2002–2024 |
| CRDA | Aquifer exploitation bulletins | Governorate | 2020–2024 |
| agridata.tn | Palm area, exports | National/Gov. | Various |

## Study area

Four governorates of southern Tunisia: Tozeur, Kébili, Gafsa, Gabès.

## Requirements

- Google Colab (for GEE authentication and GPU)
- Python 3.10+
- Key packages: `earthengine-api`, `earthaccess`, `xarray`, `pandas`,
  `scikit-learn`, `xgboost`, `matplotlib`, `scipy`, `statsmodels`

## How to reproduce

1. Clone this repository
2. Download the GRACE NetCDF file (see `data/grace_podaac/README.md`)
3. Open `notebooks/DatePalm_GEE_Data_Pipeline.ipynb` in Colab
4. Run all cells (requires GEE authentication via `bonplan-6c907` project)
5. Open `notebooks/DatePalm_FeatureEng_Modeling.ipynb` in Colab
6. Run all cells — this reproduces all modeling, decoupling analysis,
   and the yield/ha critical test

## License

GPL-3.0. See [LICENSE](LICENSE).

## Citation

If you use this data or code, please cite:

> Gasmi, T., Gasmi, R., Abdelbari, S., Boulares, S., & Albarghati, S. (2026).
> Emerging climate–yield re-coupling in overexploited date palm oases:
> satellite evidence from a 22-year temporal decoupling index in southern
> Tunisia. *Agricultural Water Management* (submitted).
