# Store Sales Time Series Forecasting

This repository contains an end-to-end workflow for the [Kaggle "Store Sales - Time Series Forecasting" competition](https://www.kaggle.com/competitions/store-sales-time-series-forecasting). The accompanying R Notebook walks through loading the public dataset, engineering features that capture seasonal retail patterns, training a global machine learning model, and exporting a submission file ready for the leaderboard.

## Project structure

```
.
├── README.md                         # Project overview and setup instructions
├── Store_Sales_Time_Series_Forecasting.Rproj  # RStudio project file
├── Untitled.Rmd                      # Main analysis notebook (rename as desired)
└── data/                             # Expected location for raw Kaggle CSVs (not tracked)
```

> **Note:** The notebook is currently named `Untitled.Rmd` because it was generated interactively. You can safely rename it (e.g., `store_sales_forecasting.Rmd`) without breaking any code.

## Requirements

- R 4.1 or later (the notebook was written against R 4.3)
- R packages:
  - Core: `tidyverse`, `data.table`, `lubridate`, `janitor`, `skimr`
  - Time series: `tsibble`, `feasts`, `fable`, `forecast`
  - Modeling & validation: `rsample`, `yardstick`, `ranger`
- Kaggle competition data placed locally under `data/` (see below)

The notebook installs any missing packages automatically when executed, but pre-installing them can speed up the first run.

## Getting started

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-account>/Store_Sales_Time_Series_Forecasting.git
   cd Store_Sales_Time_Series_Forecasting
   ```
2. **Download the competition files** from Kaggle (`train.csv`, `test.csv`, `stores.csv`, `oil.csv`, `holidays_events.csv`, `transactions.csv`) and place them in a local `data/` directory at the project root.
3. **Open the project in RStudio** using the `.Rproj` file for the smoothest experience.
4. **Run or knit the notebook** (`Untitled.Rmd`):
   - Each section is self-contained; execute chunk-by-chunk interactively, or
   - Knit the entire document to HTML to reproduce the complete analysis and submission pipeline.

## Workflow overview

The notebook is organized into clearly labeled sections:

1. **Setup** – Loads packages, configures chunk options, and defines the `data/` path.
2. **Load & Inspect Data** – Uses `data.table::fread()` for fast I/O and `skimr` to profile the training set.
3. **Cleaning & Safe Joins** – Harmonizes date fields, builds holiday indicators, forward-fills oil prices, and prepares transactions totals before joining.
4. **Feature Engineering** – Creates lagged sales, rolling statistics, calendar features, and oil/holiday signals for each `(store_nbr, family)` combination.
5. **Validation Split** – Implements a 16-day holdout split that mirrors the competition horizon while keeping preprocessing statistics tied to the training window.
6. **Modeling** – Trains a global Random Forest with `ranger`, evaluates RMSE on the validation set, and discusses potential enhancements (e.g., deep learning models).
7. **Refit & Submission** – Rebuilds features on the full training data, scores the test set, and writes `submission.csv` for Kaggle upload.

Each major transformation is performed with `data.table` for efficiency but leverages tidyverse syntax (`dplyr`, `tibble`) where clarity is improved. Feature preprocessing is handled explicitly: categorical columns are factored and one-hot encoded, zero-variance predictors are pruned, and numeric predictors are scaled using training-set statistics that are then reused for validation and test data.

## Customization tips

- Swap in alternative models (e.g., gradient boosting or deep learning) by replacing the `ranger` training chunk while keeping the shared encoded matrices produced by the preprocessing helpers.
- Extend the calendar features with additional `lubridate` components (e.g., `week`, `quarter`) or country/region-specific holiday flags.
- Experiment with rolling-origin cross-validation via `rsample::rolling_origin()` to better simulate multiple forecasting periods.

## Reproducibility

The notebook avoids writing intermediate artifacts by default and rebuilds encoded design matrices on the fly (no baked recipe outputs). If you plan to persist processed datasets or model objects, create a dedicated `artifacts/` directory and ensure it is ignored by Git. Use `set.seed()` (already included in the modeling chunk) to keep results deterministic across runs.

---

For questions or improvements, feel free to open an issue or submit a pull request.
