# Pathology Genomics — Spillover Model

A machine learning project for modeling pathogen spillover risk using genomic sequence data.

## Project Structure

```
spillover_model/
├── data/
│   ├── raw/          # Original, unmodified input data (not tracked by git)
│   ├── processed/    # Cleaned and transformed data (not tracked by git)
│   └── external/     # Third-party or reference datasets (not tracked by git)
├── src/
│   ├── data_preprocessing/   # Scripts for loading and cleaning data
│   ├── feature_engineering/  # Feature extraction from genomic sequences
│   ├── models/               # Model definitions and training
│   └── evaluation/           # Metrics and evaluation utilities
├── notebooks/        # Exploratory analysis and experiments
└── results/          # Model outputs, figures, and reports
```

## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip install pandas numpy scikit-learn biopython matplotlib seaborn tensorflow torch
```

## Data

Raw data files (including `sequences.csv`) are excluded from version control due to size. Place input files in `spillover_model/data/raw/`.
