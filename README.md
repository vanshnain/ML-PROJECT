# Crop Yield Prediction Using Machine Learning

## Project overview
This project explores crop-yield prediction with supervised machine-learning **regression** models. The notebook uses crop, season, state, cultivated area, annual rainfall, fertiliser and pesticide inputs to estimate yield.

The analysis is predictive and descriptive. It does not establish causal effects of agricultural inputs.

## Dataset
The notebook expects a CSV file named `crop_yield.csv` with these columns:

- `Crop`, `Crop_Year`, `Season`, `State`
- `Area`, `Production`, `Annual_Rainfall`, `Fertilizer`, `Pesticide`, `Yield`

The dataset file `crop_yield.csv` is now included in this repository. The notebook's earlier recorded run used 19,689 rows, 10 columns and years 1997–2020. Re-run the notebook against the committed CSV to confirm the current dataset's shape and year range.

## Workflow
1. Load and inspect the CSV.
2. Clean column names and categorical values; inspect missing values and duplicates.
3. Remove exact duplicates and rows without a usable year/target; treat invalid negative input values as missing.
4. Explore yield distributions, yearly patterns and seasonal summaries.
5. Split chronologically: training data through 2015 and a final hold-out test set from 2016 onward.
6. Fit preprocessing inside scikit-learn pipelines. Numeric values are imputed, clipped using training-fitted quantiles and scaled; categorical values are imputed and one-hot encoded.
7. Compare regression models and a median dummy baseline.
8. Use expanding-window temporal cross-validation on training years only. Tune the Decision Tree with GridSearchCV using those same time-ordered folds.
9. Select the model using temporal cross-validation, then report final hold-out metrics on 2016–2020.
10. Inspect actual-versus-predicted values, residuals, input-intensity associations, state-level summaries and permutation feature importance.

## Models
- Median Dummy Regressor (baseline)
- Multiple Linear Regression
- Polynomial Regression (degree 2)
- Ridge Regression
- Lasso Regression
- Decision Tree Regressor
- k-Nearest Neighbours Regressor
- Tuned Decision Tree Regressor (GridSearchCV)

## Validation and metrics
- **Final hold-out:** chronological split, training years 1997–2015 and test years 2016–2020 for the recorded dataset.
- **Cross-validation:** expanding-window folds constructed from training years only; validation periods always occur after their corresponding training periods.
- **Tuning:** Decision Tree hyperparameters are selected using only the temporal CV folds. The final hold-out is not used for tuning or model selection.
- **Regression metrics:** RMSE, MAE and R². MAE is also used as the temporal-CV selection score after converting predictions back to the original yield scale.

ROC curves are classification diagnostics and are not appropriate for this continuous regression target. The notebook therefore reports regression metrics and regression diagnostics instead.

## Additional analysis
- Yield distributions and yearly/seasonal summaries
- Actual vs. predicted yield and residual distribution
- Fertiliser/pesticide input intensity per area
- State-level descriptive summaries
- Permutation feature importance
- Export of test predictions and model-comparison tables

## Run locally or in Google Colab
1. Clone or download this repository.
2. Keep `crop_yield.csv` in the notebook's working directory (or upload it in Colab).
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Open `vanshnain-24570087.ipynb` in Jupyter Notebook, JupyterLab or Google Colab.
5. Run all cells from top to bottom.

The notebook saves `crop_yield_test_predictions.csv` and `crop_yield_model_comparison.csv` after a successful run.

## Repository files
- `vanshnain-24570087.ipynb` — complete analysis and modelling workflow
- `requirements.txt` — Python dependencies
- `README.md` — project documentation

## Limitations
- Results depend on the dataset version and its coverage.
- A chronological hold-out tests later years in the available data; it does not guarantee performance in every region or future season.
- Aggregated observational data can contain confounding factors and measurement limitations.
- Input/yield relationships are associations, not causal estimates.
- Model metrics should be interpreted in the original yield units and in the context of the dataset.

## Author
Vansh Nain
