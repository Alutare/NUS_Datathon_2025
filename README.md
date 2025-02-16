# Corporate Ownership Classification - NUS Datathon 2025

## Overview
This project was developed as part of the **NUS Datathon 2025**, where our team aimed to predict corporate ownership classifications using machine learning techniques. The goal was to classify firms into three distinct categories based on their ownership status:

1. **Neither Domestic nor Global Ultimate**
2. **Domestic Ultimate but not Global Ultimate**
3. **Both Domestic & Global Ultimate**

Using **XGBoost**, our model achieved a **mean accuracy of 91.45%** and a **mean weighted F1-score of 91.48%**, demonstrating strong predictive power.

---

## Dataset
The dataset was provided by **SingLife** and contained financial and corporate attributes of various firms. Data preprocessing, feature engineering, and model selection were crucial to extracting meaningful insights.

### Key Steps in Data Preparation:
- **Redefined the Target Variable**: Converted binary ownership indicators into a single multi-class target.
- **Data Cleaning**:
  - Removed irrelevant columns (e.g., geographic coordinates, company identifiers, etc.).
  - Imputed missing values and handled outliers.
  - Merged infrequent categorical values to reduce noise.
- **Feature Engineering**:
  - Created new features such as `Company Age`, `SameSalesEmployees`, `Total_Sales`, and `Total_Employees`.
  - Engineered ratio-based features to capture relationships between financial and employment figures.

---

## Model Development
### Model Selection
Several models were considered, including linear models and Random Forests. Due to its balance between performance and efficiency, **XGBoost** was chosen for its:
- **Ability to handle skewed data**
- **Fast training time**
- **Regularization techniques to prevent overfitting**

### Feature Selection
Using **Recursive Feature Elimination (RFE)** with cross-validation, we identified the most predictive features and reduced redundancy.

### Hyperparameter Tuning
We used **GridSearchCV** with a limited parameter grid due to time constraints. The final tuned hyperparameters were:
| Parameter | Best Value |
|-----------|------------|
| `n_estimators` | 100 |
| `learning_rate` | 0.1 |
| `max_depth` | 10 |
| `subsample` | 0.9 |
| `colsample_bytree` | 0.9 |

### Evaluation Metrics
Our primary metric was **F1-score**, as it balances precision and recall, ensuring an optimal trade-off between false positives and false negatives. We also considered **accuracy** and the confusion matrix to assess performance.

---

## Results
| Class | Precision | Recall | F1-Score |
|--------|-----------|--------|----------|
| 0 = Neither | 0.96 | 0.88 | 0.92 |
| 1 = Domestic Ultimate | 0.91 | 0.96 | 0.93 |
| 2 = Global Ultimate | 0.85 | 0.94 | 0.89 |
| **Macro Average** | **0.90** | **0.93** | **0.91** |
| **Weighted Average** | **0.92** | **0.91** | **0.91** |

### Key Insights:
- **Feature Importance**:
  - **SameSalesEmployees** was a major predictive factor.
  - Missing values in **Employees (Single Site)** turned out to be an informative signal rather than just noise.
  - Industry classification played a significant role, especially in distinguishing Global Ultimates.
- **Handling Missing Data**:
  - Instead of traditional imputation, we converted missing values into binary flags, which significantly boosted model performance.
- **Feature Interactions**:
  - Combining features (e.g., `Total Sales`, `Employees Growth`, and `Ownership Type`) uncovered deep structural patterns that improved predictions.

---

## Limitations & Future Improvements
- **Domain Expertise**: Consulting industry professionals could refine feature engineering and better interpret missing data.
- **Collinear Features**: Some highly correlated features could have been eliminated earlier for better efficiency.
- **Further Hyperparameter Tuning**: Due to time constraints, a broader search space for hyperparameters could yield additional performance gains.
- **Model Interpretability**: Using techniques like **LIME** or **SHAP** could help explain predictions better.

---

## Conclusion
This project successfully demonstrated the potential of **machine learning in corporate analytics** by predicting ownership classifications with high accuracy. Through **iterative feature engineering**, **strategic handling of missing data**, and **XGBoost optimization**, we developed a robust model that can provide valuable insights for regulatory compliance and risk assessment.

---

## Team Members
- **Bryan Kee Tze Ren**
- **Soh Kai Le**
- **Li Qi Ying**
- **Nevin Allen Marian**
- **Chan Wei Wen Kevin**

