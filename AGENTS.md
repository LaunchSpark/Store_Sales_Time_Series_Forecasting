# Repository Guide

## Scope
This file applies to the entire repository. Follow these conventions whenever you modify or add code, notebooks, or documentation.

## Project flow overview
1. **Environment setup**
   - The R notebook loads all required packages at the top and installs missing dependencies on the fly.
   - Global chunk options in the `setup` section suppress verbose warnings and messages for cleaner output.
2. **Data ingestion**
   - Competition CSVs (`train`, `test`, `stores`, `oil`, `holidays_events`, `transactions`) are read from a local `data/` directory using `data.table::fread()`.
   - Each dataset is immediately converted to a `data.table` via `setDT()` before any in-place column updates.
3. **Preprocessing & joins**
   - Date columns are normalized with `as.Date()`.
   - Holiday information is aggregated to daily signals, and oil prices are forward-filled over missing days.
   - Transactions are summarized to store-level counts prior to merging with the main training data.
4. **Feature engineering**
   - Lagged sales (`lag7`, `lag14`, `lag28`) and rolling statistics (`roll7`, `roll28`, `roll56`) are generated per `(store_nbr, family)` segment.
   - Calendar features (day-of-week, day-of-month, etc.) are derived with `lubridate`.
   - Recipe steps standardize numeric predictors and encode categorical variables consistently across datasets.
5. **Modeling workflow**
   - Data is split into training and validation sets that replicate the 16-day forecast horizon using `rsample`.
   - A global Random Forest (`ranger`) consumes the baked recipe outputs; validation performance is assessed with RMSE via `yardstick`.
6. **Refit & submission**
   - After validation, the model is retrained on the full dataset with identical preprocessing steps.
   - Predictions for the competition `test` set are post-processed with `expm1()` and written to `submission.csv`.

## Architecture notes
- **Primary artifact**: A single R Markdown notebook (`Untitled.Rmd`) encapsulates the entire pipeline from ingestion to submission.
- **Data handling**: `data.table` is favored for mutations; tidyverse tibbles are used when readability benefits outweigh conversion costs.
- **Feature pipeline**: `recipes` defines the transformation graph, ensuring training, validation, and test matrices remain synchronized.
- **Model abstraction**: The Random Forest is a modular component. Alternative models should expect the same preprocessed features and target (`y = log1p(sales)`).
- **Outputs**: The notebook creates `submission.csv` in the project root; no intermediate artifacts are persisted by default.

## Contribution tips
- Keep notebook sections self-contained and labeled with numeric prefixes to preserve the documented flow.
- When adding new scripts or modules, update `README.md` with usage instructions and ensure file paths remain relative to the project root.
- Prefer reproducible seeds and avoid writing raw Kaggle data to version control.
