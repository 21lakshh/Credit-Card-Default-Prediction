# Credit Card Default Prediction

## Objective
To develop a predictive model for estimating the probability of default by credit card customers, using development data and validating predictions on a separate validation dataset.

---

## Column Descriptions
- **On-us Attributes:** Customer credit limits and credit utilization.
- **Transaction Attributes:** Represent customer transaction patterns (e.g., number of transactions, transaction value across merchant types).
- **Bureau Tradeline Attributes:** Historical delinquency and product holding details.
- **Bureau Enquiry Attributes:** Represent recent credit inquiries reported by credit bureaus (e.g., number of personal loan inquiries in the past 3 months).

---

## Data Analysis
### Steps Taken:
1. **Statistical Insights:**
   - Calculated mean, standard deviation, and count.
2. **Class Imbalance:**
   - Observed imbalance in the `bad_flag` attribute (target column).
3. **Missing Values:**
   - Checked and replaced missing values with meaningful values.
4. **Feature Correlation:**
   - Used heatmaps to visualize correlations between features.

---

## Data Preprocessing
1. **Handling Missing Values:**
   - Bureau enquiry attributes with missing values were filled with `0` (indicating no inquiries).
   - Used statistical methods (mean, median) to replace missing values in other columns.
   - Columns `bureau_436` and `bureau_447` were fully missing and replaced with `0`.

2. **Scaling Features:**
   - Used `StandardScaler` to normalize all features, ensuring equal scaling for better model performance.

3. **Dataset Split:**
   - Splitted the dataset into **80% training** and **20% validation**.

---

## Model Building
### Algorithms Used:
- **Logistic Regression:** A simple and interpretable linear model.
- **Decision Tree:** Captures non-linear relationships.
- **Random Forest:** Reduces overfitting by aggregating multiple decision trees.
- **Gradient Boosting:** Focuses on correcting errors made by previous models.
- **K-Nearest Neighbors:** Non-parametric and considers feature similarity.
- **XGBoost:** Highly efficient gradient boosting algorithm.

### Model Selection:
- Trained all models on the training set and evaluated performance on the validation set.
- **Metrics Used for Comparison:**
  - **Accuracy:** Overall correctness of predictions.
  - **Precision:** Ability to avoid false positives.
  - **Recall:** Proportion of actual positive observations correctly predicted.
  - **F1-Score:** Harmonic mean of precision and recall.

### Best Model:
- Selected **RandomForestClassifier** with a score of **98.60%**.

---

## Validation and Prediction
1. Preprocessed the validation dataset similarly to the training dataset:
   - Filled missing values using the same strategy.
   - Scaled features using `StandardScaler` fitted on the training data.

2. Predicted default probabilities using the **RandomForestClassifier**.

3. Saved results in a CSV file containing:
   - **Primary Key:** `account_number`
   - **Predicted Probability** against the account.

---

## Key Insights and Observations
### Most Impactful Features:
- **Bureau Tradeline Attributes:** Strong predictive power, reflecting historical defaults.
- **Transaction Attributes:** Spending patterns associated with risk.

### Data Challenges:
- Addressed **class imbalance**, as defaults were less frequent.
- Logical imputation for missing data (e.g., `bureau_436` and `bureau_447`).

---
Dev Data: https://drive.google.com/file/d/1oWS7oXSKRGpxhd7Fh7S9yyky1feXLtpc/view?usp=sharing  
Validation Data: https://drive.google.com/file/d/1naKeoBk3Rdh2Nxfntk1bb6KLJSkbF5pi/view?usp=sharing  
