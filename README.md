// ...existing code...
# Sales Forecasting with Time-Series Analysis

A reproducible project to forecast daily store sales using classical time-series (SARIMA) and machine-learning (XGBoost) approaches. The project includes data preprocessing, exploratory data analysis, modelling, hyperparameter tuning with Optuna, and experiment tracking with MLflow.

- Dataset: https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset

Repository structure (relevant files)
- Notebooks:
  - [Modelling.ipynb](Modelling.ipynb)
  - [EDA.ipynb](EDA.ipynb)
  - [Pre-Processing.ipynb](Pre-Processing.ipynb)
- Data:
  - [Data/Raw/stores_sales_forecasting.csv](Data/Raw/stores_sales_forecasting.csv)
  - [Data/Processed/final_model_data.csv](Data/Processed/final_model_data.csv)
  - [Data/Processed/X_train.csv](Data/Processed/X_train.csv)
  - [Data/Processed/X_test.csv](Data/Processed/X_test.csv)
  - [Data/Processed/y_train.csv](Data/Processed/y_train.csv)
  - [Data/Processed/y_test.csv](Data/Processed/y_test.csv)
- Experiments:
  - [mlruns](mlruns)

Key variables and helpers (see [Modelling.ipynb](Modelling.ipynb))
- [`Modelling.X_train`](Modelling.ipynb), [`Modelling.y_train`](Modelling.ipynb)
- [`Modelling.predictions_df`](Modelling.ipynb)
- [`Modelling.evaluate_model`](Modelling.ipynb)

Requirements
- Python 3.10+ (recommended via conda/miniconda)
- Main packages: pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, statsmodels, mlflow, optuna, jupyter

Quickstart
1. Create environment and install dependencies (example):
   ```sh
   conda create -n sales-forecast python=3.10 -y
   conda activate sales-forecast
   pip install -r requirements.txt  # or install the packages listed above
   ```
2. Run notebooks in order:
   - Open and run [EDA.ipynb](EDA.ipynb)
   - Open and run [Pre-Processing.ipynb](Pre-Processing.ipynb)
   - Open and run [Modelling.ipynb](Modelling.ipynb)

Reproduce modelling & experiments
- The modelling notebook loads preprocessed splits from:
  - [Data/Processed/X_train.csv](Data/Processed/X_train.csv)
  - [Data/Processed/X_test.csv](Data/Processed/X_test.csv)
  - [Data/Processed/y_train.csv](Data/Processed/y_train.csv)
  - [Data/Processed/y_test.csv](Data/Processed/y_test.csv)
- Hyperparameter tuning uses Optuna with MLflow tracking. Launch MLflow UI to inspect runs:
  ```sh
  mlflow ui --backend-store-uri mlruns
  ```
- Final models and artifacts are saved under [mlruns](mlruns).

Evaluation metrics
- Mean Absolute Error (MAE):
  $$
    \mathrm{MAE} = \frac{1}{n}\sum_{i=1}^{n} |y_i - \hat{y}_i|
  $$
- Root Mean Squared Error (RMSE):
  $$
    \mathrm{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
  $$

Results summary (see [Modelling.ipynb](Modelling.ipynb) for full details)
- Baseline seasonal naive, SARIMA, and XGBoost forecasts are compared in [`Modelling.predictions_df`](Modelling.ipynb).
- Examples of reported metrics appear in the notebook outputs (MAE / RMSE for each method).

Notes & tips
- Confirm date ranges and shapes before training (see [`Modelling.X_train`](Modelling.ipynb) info printed in the notebook).
- If mlflow warns about models logged without an input example/signature, this is informational — include `input_example` when logging to avoid the warning.
- Use the provided processed CSVs in [Data/Processed](Data/Processed) for faster iteration.

License & attribution
- Dataset sourced from Kaggle: https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset — check the original page for licensing details.

Contact / Maintainer
- See repository files for author details.

% End of README
// ...existing code...
