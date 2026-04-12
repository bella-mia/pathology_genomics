# Spillover Model — Next Steps Checklist

## 1. Finish Data Cleaning (`cleaning_data.ipynb`)
- [ ] Drop the `Genotype` column (~98% missing, not usable)
- [ ] Standardize `Collection_Date` to a consistent format (YYYY-MM-DD)
- [ ] Decide on `Tissue_Specimen_Source` (~64% missing) — fill with "unknown" or drop
- [ ] Decide on `Submitters` (~43% missing) — likely safe to drop for modeling
- [ ] Save cleaned output to `spillover_model/data/processed/sequences_clean.csv`

## 2. Feature Engineering
- [ ] Encode `Molecule_type` as a numeric category (ssDNA, dsDNA, ssRNA, etc.)
- [ ] Encode `Geo_Location` into broader regions (continent or country-level)
- [ ] Classify `Host` into animal groups (bat, primate, rodent, bird, etc.)
- [ ] Merge in phylogenetic risk scores from `genomics.ipynb`
- [ ] Save feature matrix to `spillover_model/data/processed/features.csv`

## 3. Build / Verify the SIR/SEIR Stochastic Model
- [ ] Confirm whether the model exists somewhere (not found in notebooks or `src/` yet)
- [ ] If not built: implement Monte Carlo SIR/SEIR in `spillover_model/src/models/`
- [ ] Run model on a small host subset to validate outputs

## 4. Risk Heatmapping
- [ ] Generate spillover probability scores per host/region combination
- [ ] Plot geographic heatmap of high-risk spillover zones
- [ ] Save figures to `spillover_model/results/`

## 5. Refactor Code into `src/` Modules
- [ ] Move `NCBIPhyloEstimator` → `src/feature_engineering/phylo_estimator.py`
- [ ] Move cleaning logic → `src/data_preprocessing/clean.py`
- [ ] Move model code → `src/models/sir_model.py`
- [ ] Add `__init__.py` files so modules are importable

## 6. Gathering Intensity Algorithm (In Progress)
- [ ] Finish weighting transmission risk by calendar event types
- [ ] Integrate with TimeTree API human event density data
- [ ] Test algorithm output against known spillover events

## 7. Dashboard (Next Steps)
- [ ] Design layout for visualizing spillover probability shifts
- [ ] Connect to model outputs and heatmap figures
- [ ] Choose framework (Streamlit recommended for simplicity)
