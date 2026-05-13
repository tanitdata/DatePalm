# Trained Models

Trained model files (.pkl) are excluded from git (binary, non-portable).

## Regeneration

Run `notebooks/DatePalm_FeatureEng_Modeling.ipynb` (Cells 13–15) to
regenerate:
- `ridge_model.pkl`
- `random_forest_model.pkl`
- `xgboost_model.pkl`
- `feature_scaler.pkl`

Requires the compiled data in `data/compiled/`.
