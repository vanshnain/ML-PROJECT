# Crop Yield Prediction Using Machine Learning

## Project Overview
This project focuses on predicting crop yield using
Machine Learning regression algorithms.

The project uses agricultural features such as crop,
season, state, area, annual rainfall, fertilizer and
pesticide usage to predict crop yield.

## Dataset
- Total Records: 19,689
- Total Columns: 10
- Year Range: 1997–2020
- Target Variable: Yield

## Machine Learning Models
1. Multiple Linear Regression
2. Polynomial Regression
3. Ridge Regression
4. Lasso Regression
5. Decision Tree Regressor
6. K-Nearest Neighbors Regressor

## Data Preprocessing
- Missing value inspection
- Duplicate removal
- Numerical data conversion
- Outlier treatment
- Median imputation
- Standard scaling
- One-hot encoding

## Model Evaluation
Models are evaluated using:
- RMSE
- MAE
- R² Score

The dataset is divided using a time-based split:
- Training: 1997–2015
- Testing: 2016–2020

## Additional Analysis
- Exploratory Data Analysis
- Actual vs Predicted Yield
- Residual Analysis
- Fertilizer and Pesticide Analysis
- State-level Yield Analysis
- Permutation Feature Importance

## Technologies Used
- Python
- Google Colab
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## How to Run
1. Clone this repository.
2. Install dependencies:

   pip install -r requirements.txt

3. Open the notebook using Google Colab
   or Jupyter Notebook.
4. Upload crop_yield.csv when prompted.
5. Run all notebook cells.

## Project Files
- vanshnain-24570087.ipynb
- requirements.txt
- crop_yield.csv
- README.md

## Limitations
The analysis is based on historical agricultural
data. Results do not establish causal relationships
between agricultural inputs and crop yield.

## Author
Vansh Nain
