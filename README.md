# Demand Forecasting with Uncertainty Quantification

# Objective
Built a forecasting model that outputs prediction intervals (10th, 50th, 90th percentiles) rather than single point estimates to inform inventory decisions under asymmetrical risk.

# Setup and Reproduction
1. Dataset: Kaggle Store Item Demand Forecasting Challenge
2. Dependencies: `pandas`, `numpy`, `lightgbm`, `scikit-learn`
3. Reproduction: Run the included Jupyter Notebook from top to bottom.

# Key Decisions & Approach
* **Feature Engineering:** Used 7-day lags and rolling averages to capture time-series patterns.
* **Model:** Trained three LightGBM models using quantile loss (alpha = 0.1, 0.5, 0.9) to generate prediction intervals.
* **Evaluation:** Evaluated point accuracy via MAE and calibration by confirming that nominal coverage (78.91%) matches actual interval coverage (~80%).

## Business Results
Setting safety stock using the upper quantile (90th percentile) resulted in a lower total cost ($456,395.03) compared to the point forecast ($744,293.94), as the model successfully minimized the $10/unit stockout penalty at the expense of the smaller $2/unit holding cost. Overconfidence was observed primarily during sudden weekend demand spikes where intervals remained too narrow.
