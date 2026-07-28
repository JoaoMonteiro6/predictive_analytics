# Multiple Linear Regression Analysis - CO2 Emissions Prediction

## Overview

This project demonstrates the implementation and analysis of multiple linear regression models using scikit-learn. The primary objective is to predict CO2 emissions from light-duty vehicles based on engine specifications and fuel consumption characteristics.

The analysis includes:
- **Data exploration and feature selection** using correlation analysis
- **Feature standardization** for optimal model performance
- **Multiple regression modeling** with multiple predictors
- **Simple regression comparison** exploring individual feature relationships
- **Model evaluation** and interpretation of regression coefficients

## Dataset

**Source:** [Open Canada - Vehicle Fuel Consumption and Emissions Data](http://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64)

### Dataset Features

- **MODEL YEAR:** Vehicle model year (e.g., 2014)
- **MAKE:** Vehicle manufacturer (e.g., VOLVO)
- **MODEL:** Vehicle model name (e.g., S60 AWD)
- **VEHICLE CLASS:** Classification category (e.g., COMPACT)
- **ENGINE SIZE:** Engine displacement in liters
- **CYLINDERS:** Number of engine cylinders
- **TRANSMISSION:** Transmission type code
- **FUEL TYPE:** Fuel type indicator
- **FUEL CONSUMPTION (CITY/HWY/COMBINED):** Fuel economy in L/100 km
- **FUEL CONSUMPTION (MPG):** Combined fuel economy in miles per gallon
- **CO2 EMISSIONS:** Target variable - estimated emissions in g/km

## Project Structure

```
linear_regression_co2_emissions/
│
├── Multiple_Linear_Regression.ipynb    # Main analysis notebook with exercises
├── README.md                           # Project documentation
├── requirements.txt                    # Python dependencies
└── images/                             # Visualization outputs (optional)
    ├── correlation_heatmap.png
    ├── scatter_matrix.png
    ├── 3d_regression_plane.png
    └── regression_fits.png
```

## Learning Objectives

After working through this analysis, you will understand:

1. **Feature Selection:** How to use correlation analysis to identify predictive features and remove redundant variables
2. **Data Preprocessing:** Standardization techniques and their importance in linear regression
3. **Model Development:** Building both multiple and simple linear regression models with scikit-learn
4. **Model Interpretation:** Understanding regression coefficients and intercepts in both standardized and original feature spaces
5. **Model Evaluation:** Comparing model performance across different feature subsets and identifying overfitting scenarios
6. **Regression Diagnostics:** Visual analysis of model fit quality through scatter plots and residual analysis

## Key Findings

### Multiple Regression Analysis
- Using engine size and fuel consumption (MPG) together produces a suboptimal fit
- The non-linear relationship between fuel consumption and CO2 emissions suggests the data contains distinct vehicle classes with different emission patterns
- The model's intercept is unrealistic when extrapolated to zero values, indicating predictions should stay within training data ranges

### Simple Regression - Engine Size
- Engine size shows a strong **linear relationship** with CO2 emissions
- Univariate model provides superior fit quality compared to multiple regression
- High predictive power demonstrates engine displacement is a critical emission factor

### Simple Regression - Fuel Consumption (MPG)
- Fuel consumption (MPG) is the **strongest single predictor** of CO2 emissions
- Inverse relationship shows near-perfect association with target variable
- Model outperforms both the multiple regression and engine-size-only approaches

## Implementation Details

### Technology Stack
- **Python 3.8+**
- **scikit-learn:** Machine learning library for regression models
- **pandas:** Data manipulation and analysis
- **NumPy:** Numerical computing
- **Matplotlib:** Data visualization

### Key Steps

1. **Load and Explore Data**
   ```python
   df = pd.read_csv(url)
   df.describe()
   df.corr()
   ```

2. **Feature Selection**
   - Drop categorical and constant columns (MODELYEAR, MAKE, MODEL, etc.)
   - Remove highly correlated features (CYLINDERS, redundant fuel consumption metrics)
   - Final features: ENGINE SIZE, FUELCONSUMPTION_COMB_MPG

3. **Data Preprocessing**
   - Standardize features using StandardScaler (mean=0, std=1)
   - Train-test split: 80% training, 20% testing (random_state=42 for reproducibility)

4. **Model Training**
   ```python
   regressor = linear_model.LinearRegression()
   regressor.fit(X_train, y_train)
   ```

5. **Model Evaluation**
   - Compare coefficients across different feature combinations
   - Visualize regression lines on test data
   - Assess goodness-of-fit through scatter plots

## How to Use

### Prerequisites
Ensure Python 3.8 or higher is installed on your system.

### Installation

1. Clone or download this repository
2. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook Multiple_Linear_Regression.ipynb
   ```

### Running the Analysis

- Execute cells sequentially from top to bottom
- Follow the exercise sections (Exercise 1-5) to practice implementing regression models
- Refer to insights provided after each analysis section for interpretation guidance
- Modify code and parameters to explore how they affect model performance

## Exercises Included

**Exercise 1:** Implement simple linear regression using engine size as the sole predictor

**Exercise 2:** Create a scatter plot with regression line for training data (engine size vs CO2)

**Exercise 3:** Evaluate the model on test data and compare with training performance

**Exercise 4:** Build a regression model using fuel consumption (MPG) instead of engine size

**Exercise 5:** Generate predictions on test data and reflect on model quality and potential improvements

## Model Insights

### What the Data Shows

1. **Feature Relationships:** Engine size and fuel consumption are inversely related, both strongly predicting CO2 emissions
2. **Model Complexity:** While multiple regression is more sophisticated, simpler univariate models often provide better fit for this dataset
3. **Non-linear Patterns:** The presence of distinct clusters suggests vehicle class substantially influences emissions beyond what engine features capture

### Practical Implications

- **Single Feature Advantage:** For this dataset, using fuel consumption alone provides accurate predictions with greater interpretability
- **Standardization Value:** Scaling features to comparable ranges ensures regression coefficients reflect true feature importance
- **Model Selection:** Choosing between multiple and simple regression demonstrates the bias-variance tradeoff in machine learning

## Next Steps for Enhancement

1. **Polynomial Regression:** Test polynomial features to capture non-linear relationships
2. **Include Categorical Variables:** Incorporate vehicle class, fuel type, and transmission into models
3. **Advanced Metrics:** Calculate R², RMSE, and cross-validation scores for robust evaluation
4. **Feature Engineering:** Create interaction terms or derived features to improve model performance
5. **Regularization:** Implement Ridge or Lasso regression to handle multicollinearity

## Author

**João Monteiro**  
Commercial Assistant at Caixa Geral de Depósitos  
IBM Data Science Professional Certificate Candidate

### Course Reference

This analysis is based on the **IBM Data Science Professional Certificate** program, specifically the Machine Learning foundations module covering regression analysis and model evaluation.

## License

This project is provided for educational purposes as part of the IBM Data Science Professional Certificate program.

## Acknowledgments

- IBM Skills Network for the foundational course materials and dataset
- Open Canada government data portal for the vehicle emissions dataset
- scikit-learn documentation and community for ML implementation best practices

---

**Last Updated:** July 2026  
**Status:** Active - Available for portfolio and learning purposes
