# Stochastic Disease Spillover & Risk Simulation

A computational modeling framework built in Python to simulate pathogen transmission across species interfaces. This project utilizes stochastic processes and compartmental modeling to identify environmental and genomic triggers for spillover events.

## 🛠️ Technical Stack
* **Language:** Python 3.9+
* **Modeling:** Monte Carlo Simulations, Compartmental (SIR/SEIR) Modeling
* **Data & Math:** NumPy, Pandas, SciKit-Learn
* **Genomics:** Biopython (Sequence feature extraction)
* **Visualization:** Matplotlib, Seaborn

## 🚀 Key Features
* **Stochastic Transmission Logic:** Implements random-walk variables to simulate unpredictable environmental shifts.
* **Genomic Feature Extraction:** Processes sequence data to evaluate alignment between viral proteins and host receptors.
* **Risk Heatmapping:** Generates predictive distributions for high-risk spillover "hotspots" based on integrated data streams.

## 📁 Project Structure

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
