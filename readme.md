% Sales Forecasting with Time-Series Analysis - README (MATLAB style)
%
% Project summary:
%   - Goal: Forecast daily store sales using time-series methods (SARIMA) and
%     machine learning (XGBoost) and compare results.
%   - Dataset source: https://www.kaggle.com/datasets/tanayatipre/store-sales-forecasting-dataset
%
% Key files:
%   - Notebooks:
%       [Modelling.ipynb](Modelling.ipynb)           % model training, tuning, evaluation
%       [EDA.ipynb](EDA.ipynb)                       % exploratory data analysis
%       [Pre-Processing.ipynb](Pre-Processing.ipynb)% feature engineering & preprocessing
%   - Data:
%       [Data/Raw/stores_sales_forecasting.csv](Data/Raw/stores_sales_forecasting.csv)
%       [Data/Processed/final_model_data.csv](Data/Processed/final_model_data.csv)
%       [Data/Processed/X_train.csv](Data/Processed/X_train.csv)
%       [Data/Processed/X_test.csv](Data/Processed/X_test.csv)
%       [Data/Processed/y_train.csv](Data/Processed/y_train.csv)
%       [Data/Processed/y_test.csv](Data/Processed/y_test.csv)
%   - Experiments and tracking:
%       [mlruns](mlruns)                              % MLflow runs and artifacts
%
% Important variables (see [Modelling.ipynb](Modelling.ipynb)):
%   - `X_train`, `y_train`                 % training features/target
%   - `predictions_df`                     % combined actuals and forecasts
%   - `evaluate_model`                     % evaluation helper (returns MAE/RMSE)
%
% How to reproduce:
%   1) Install environment (recommended conda):
%        - Python 3.10+ with packages: pandas, numpy, matplotlib, scikit-learn,
%          xgboost, statsmodels, mlflow, optuna, jupyter
%   2) Open and run notebooks in order:
%        - [EDA.ipynb](EDA.ipynb)
%        - [Pre-Processing.ipynb](Pre-Processing.ipynb)
%        - [Modelling.ipynb](Modelling.ipynb)
%   3) In [Modelling.ipynb](Modelling.ipynb) you can:
%        - Create a validation split from `X_train` and `y_train`
%        - Run hyperparameter tuning (Optuna + MLflow)
%        - Train final XGBoost model and save artifacts to MLflow
%
% Notes on evaluation metrics:
%   - Mean Absolute Error (MAE):
%     $$
%       \text{MAE} = \frac{1}{n}\sum_{i=1}^{n} |y_i - \hat{y}_i|
%     $$
%   - Root Mean Squared Error (RMSE):
%     $$
%       \text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
%     $$
%
% Quick tips:
%   - Check the date range and shapes used in training: see [`X_train`](Modelling.ipynb).
%   - Use MLflow UI to inspect runs in [mlruns](mlruns) or by launching:
%         mlflow ui --backend-store-uri mlruns
%   - If models are logged without an input example, MLflow will warn (benign).
%
% Results summary:
%   - Final tuned XGBoost reported in notebook with MAE and RMSE values.
%   - Compare baseline seasonal naive, SARIMA, and XGBoost forecasts in
%     [`predictions_df`](Modelling.ipynb).
%
% License / attribution:
%   - Dataset from Kaggle (link above). See original dataset page for licensing.
%
% Contact:
%   - See project files for author/maintainer details.
%
% End of README