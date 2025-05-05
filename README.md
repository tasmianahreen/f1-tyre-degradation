# 🏎️ Formula 1 Tyre Degradation Prediction
This project builds machine learning models to predict tyre degradation in Formula 1 based on historical pit stop and race data. The goal is to forecast when a tyre's performance is likely to drop off, helping strategists and engineers optimize pit stop timing.

I've used a comprehensive dataset of pit stop records from 1950–2024, which includes:
* Race metadata (season, round, circuit)
* Driver and team information
* Tyre compound used
* Stint details (lap numbers, stint length)
* Pit stop durations
* Track conditions and other performance metrics

The target variable is a degradation indicator that:
* Predicts if tyre performance drops significantly after a certain number of laps (binary classification),
* Predicts the expected number of laps before a pit stop is required (regression).

## 🔧 Workflow
### 1️⃣ Data Preprocessing
Cleaning: Removed irrelevant or redundant columns, handled missing values, and filtered for modern-era data to improve relevance.

### Feature Engineering:
* Created features like laps on tyre, stint length, average lap time drift.
* Labeled degradation: e.g., if tyre performance fell off by X seconds per lap after N laps, we marked it as "degraded."
* Encoding: Transformed categorical data (driver, tyre compound, weather) into numerical format.
* Balancing: If predicting binary degradation (yes/no), applied balancing techniques to address class skew.

### 2️⃣ Exploratory Data Analysis
* Analyzed tyre compound usage and stint lengths.
* Visualized lap time trends vs. tyre age.
* Checked pit stop patterns across different circuits and seasons.

### 3️⃣ Model Training
Trained and compared the following models:
* Decision Tree: To understand key decision points (e.g., stint length thresholds).
* Random Forest: To improve stability and handle feature interactions.
* XGBoost: For high-performance predictions using boosting.

### 4️⃣ Hyperparameter Tuning
Used RandomizedSearchCV with cross-validation to optimize parameters for each model.

### 5️⃣ Model Evaluation
For binary classification:
* Accuracy
* Precision, Recall, F1-score
* Confusion Matrix

### For regression (predicting lifespan):
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* R² Score
