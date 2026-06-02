# Notes
1. Some country names are represented with localized country names and non-English character representations
2. The circular histogram revealed that wind directions are not uniformly distributed across all angles. Instead, several directional concentrations were observed, suggesting prevailing wind patterns and regional climatic biases within the dataset.
3. Based on Pearson correlation, air pollution features are all positively correlated except Ozoen and PM 10. This is consistent with the pollutants released sue to urban human pollution like vehicular exhausts etc. 
4. The `temperature_celsius` vs `feels_like_celsius` scatter plot shows a strong positive linear relationship between actual and perceived temperature. Around the moderate temperature range (~16°C to 22°C), the feels-like temperature closely matches the measured temperature, lying near the y = x reference line.
5. For temperatures above ~22°C, the feels-like temperature is generally higher than the measured temperature, likely due to humidity effects increasing heat perception. Conversely, for temperatures below ~16°C, the feels-like temperature tends to be lower than the measured temperature, indicating colder perceived conditions caused by factors such as wind chill.
6. The spread (dispersion) of feels-like values increases at both high and low temperature extremes, while mid-range temperatures show relatively low variability. This suggests that environmental factors influencing perceived temperature become more significant under extreme weather conditions.

# Forecasting Target Selection

Weather is inherently a multivariate phenomenon rather than a single measurable quantity. Variables such as temperature, humidity, atmospheric pressure, precipitation, cloud cover, and wind conditions are physically interconnected and together describe the overall state of the atmosphere.

Initially, the possibility of forecasting a *composite weather representation* was considered. However, predicting an abstract combined weather variable would require a more advanced multivariate or coupled forecasting framework capable of simultaneously modeling complex dependencies among multiple atmospheric variables.

Another forecasting formulation explored was weather-condition classification using the `condition_text` feature, since it provides a broader semantic description of overall weather conditions rather than representing a single atmospheric measurement.

* a large number of categorical weather states,
* significant class imbalance,
* and inconsistencies in condition labels.

To maintain interpretability and enable a clear comparison between forecasting techniques within the scope of this assessment, the problem was therefore simplified to forecasting a single continuous target variable:

* `temperature_celsius`

At the same time, other weather-related variables — including humidity, pressure, cloud cover, precipitation, and wind measurements — are retained as predictive input features to preserve the multivariate nature of the dataset.

This formulation:

* simplifies model evaluation and comparison,
* improves interpretability of forecasting performance,
* while still leveraging relationships among multiple atmospheric variables through feature engineering.

Although temperature serves as the primary forecasting target, the remaining weather variables continue to play an important role during exploratory data analysis, correlation analysis, and anomaly detection due to their strong interdependent behavior.

* For further simplification, i.e. to have no dependence of location, I chose the target variable for frecasting to be **Daily Global Average Temperature**.

# Project Flow
1. Data Cleaning, Preprocessing & Validation
   ├── Missing Values
   ├── Outliers - Univariate analysis
   ├── Missing Values
   ├── Missing Values
   ├── Missing Values
   └── weather_validated.csv

2. EDA Domain Exploration
   ├── Weather Phenomena Analysis
   ├── Geographic Analysis
   ├── Temporal Analysis
   ├── Climate Zone Analysis
   ├── Seasonal Patterns
   └── Air Quality Analysis
   
3. Advanced EDA
   ├── Correlation Analysis
   ├── Anomaly Detection - Multivariate analysis
   │   ├── Isolation Forest
   │   ├── PCA Visualization
   │   └── SHAP Interpretation
   └── weather_cleaned.csv

4. Feature Engineering
   ├── Derived Features
   ├── Climate Zone Feature
   ├── Cyclical Time Features
   ├── Encoding
   ├── Scaling / Normalization
   ├── Feature Selection
   └── weather_features.csv

5. Modeling
   ├── Forecasting
   │    ├── Time Series Analysis
   │    │    ├── MA - 7
   │    │    ├── MA - 3
   │    │    ├── ARIMA
   │    │    ├── Prophet
   │    ├── Machine Learning
   │    │    ├── Linear Regression
   │    └── Performance Comparison
   └── Evaluation
   