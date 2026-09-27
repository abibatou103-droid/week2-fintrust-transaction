# FinTrust Data Science Track — Week 2 Project Documentation

## 1. Objective
The objective was to prepare the customer and transaction datasets, investigate the synthetic Risk_Review_Flag target, engineer useful modelling features, and build a baseline machine-learning model to assess whether transaction and customer information can predict review flags.

## 2. Data Preparation Decisions
- Loaded the customer dataset and transaction dataset from CSV files.
- Parsed Transaction_DateTime to datetime values so time-based features could be created.
- Merged customer information onto the transaction records using Customer_ID.
- Reviewed duplicate records, missing values, and type consistency before modelling.
- Treated missing Device_Type and Location values as an explicit modelling issue and recorded them in the data-prep notes.
- Kept the target variable as a binary educational label: 1 = Risk Review, 0 = No Risk Review.

## 3. Exploratory Data Analysis
Eight visual analyses were produced to study risk patterns across transaction types, statuses, international activity, customer segments, channels and time of day. The highest-risk patterns were observed for transfer and cash-withdrawal transactions, failed or international transactions, and higher-value outlier spends.

## 4. Feature Engineering
A set of engineered features was created to express transaction timing, magnitude, context, and customer profile. The features included transaction-hour, transaction-day, amount logs, customer transaction frequency, average spending, and engagement/tenure bands.

## 5. Baseline Model
A logistic regression pipeline with one-hot encoding for categorical variables and scaling for numeric inputs was used as the baseline model. The model was trained on an 80/20 split with class balancing enabled to improve sensitivity to the minority positive class.

## 6. Model Evaluation
The baseline model achieved:
- Accuracy: 0.6312
- Precision: 0.2893
- Recall: 0.6064
- F1-score: 0.3918
- ROC AUC: 0.6676

These results indicate the model is better than random guessing but still leaves room for improvement. The positive class is challenging because the target is imbalanced.

## 7. Interpretation
The strongest positive signals included transfer transactions, cash withdrawals, high transaction values, international transactions, failed transactions, and low digital engagement bands. Negative coefficients were strongest for card purchases, deposits, and active account statuses, suggesting these patterns were less associated with a positive risk-review flag in the baseline model.

## 8. Limitations
- The target variable is synthetic and educational only; it should not be interpreted as a real fraud decision.
- There are missing values in transaction Device_Type and Location, which can reduce quality for some modelling paths.
- The baseline model uses a simple logistic-regression setup and does not yet include advanced class-balancing or tree-based modelling.
- No explicit temporal holdout or out-of-time validation was used.

## 9. Testing and Quality Review
The work was checked by verifying dataset shape, missing values, duplicates, target distribution, feature engineering logic, and model evaluation through a consistent pipeline. The generated outputs were saved to disk and reviewed for reproducibility.

## 10. Remaining Work
Potential next steps include:
- testing tree-based models such as RandomForest or XGBoost;
- tuning class thresholds and calibration;
- validating performance across more realistic temporal splits;
- documenting a richer business interpretation for risk-review drivers.
