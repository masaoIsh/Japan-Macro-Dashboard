# Japan-Macro-Dashboard 

A macroeconomic research project that extracts interpretable factors, detects structural regimes, and simulates realistic agent behavior—offering tools for forecasting, policy analysis, and macro-financial strategy.

---

## 1 | Overview

This repository creates a multi-stage "macroeconomic factor analysis platform" focused on Japan and the United States.

| Stage | Notebook | Goal |
|-------|----------|------|
| **1** | `01_data_collection_and_preprocessing.ipynb` | Pull macro series from FRED, the World Bank, and the Bank of Japan; clean, align, and export a monthly panel (`macro_features.csv`). |
| **2** | `02_macro_factor_exploration.ipynb` | Standardize variables, run PCA, visualize loadings/biplot, derive the dominant factor (PC1), label three regimes (Stagnation/Recovery/Expansion), and save `macro_factor.csv` and `macro_regime.csv`. |
| **3** | `03_differentiable_ABM.ipynb` | Train a differentiable GRU-based agent-based model whose collective actions reproduce PC1 and classify regimes; evaluate forecasts, confusion matrix, and agent behaviors. |

## 2 | Quick-Start

```bash
# Clone the repo
git clone https://github.com/<your-username>/Japan-Macro-Dashboard.git
cd Japan-Macro-Dashboard

# Create environment
conda env create -f environment.yml
conda activate macro

# Launch notebooks
jupyter lab
```

> **Colab users**: Each notebook contains a "Run on Colab" badge. After launching, simply `pip install -r requirements_colab.txt`.

---

## 3 | Repository Layout

```
├── data/
│   ├── macro_features.csv
│   ├── macro_factor.csv
│   └── macro_regime.csv
├── notebooks/
│   ├── 01_data_collection_and_preprocessing.ipynb
│   ├── 02_macro_factor_exploration.ipynb
│   └── 03_differentiable_ABM.ipynb
└── README.md
```

---

## 4 | Data Sources

- **FRED** – US CPI, unemployment, Fed funds rate, 10-year Treasury
- **Bank of Japan** / **IMF** – Japanese CPI, lending rate
- **World Bank** – GDP growth, industrial production

All data pulls are scripted and reproducible (see Notebook 1).

---

## 5 | Highlights & Results

| Module               | Metric                            | Result              |
|----------------------|-----------------------------------|---------------------|
| PCA                  | Variance explained by PC1         | **78%**             |
| Regime classifier    | Confusion matrix accuracy         | **89%**             |
| Differentiable ABM   | One-step-ahead RMSE (norm PC1)    | **0.09**            |
| Agent heterogeneity  | Avg. forecast spread by regime    | **~1.5 range**      |

---

## 6 | How to Re-Use

1. Swap in new macro series — update `series_dict` in Notebook 1.  
2. Change prediction horizon — modify `WINDOW` in Notebook 3.  
3. Replace agents — try MLP, Transformer, or even rule-based logic.  
4. Integrate into a larger pipeline — use `macro_factor.csv` for forecasting or risk modeling.

---

## 7 | Contributing

Pull requests are welcome — especially for:

- New macro sources (e.g., OECD indicators)
- Alternative dimensionality reductions (e.g., ICA, VAEs)
- More expressive agent architectures or training objectives

---

*Maintainer: [Masao Ishihara](mailto:26ishiharam@keio.jp) — Tokyo*  
