# CA1 – Machine Learning: Predicting Maternal Health Risk

HDip in Science in Data Analytics for Business – CCT College Dublin

Module: Machine Learning | Lecturer: Dr. Muhammad Iqbal | Student: Daniella Silveira e Silva

## Project overview

This project predicts the risk level of a pregnancy (low, mid or high risk) from six vital signs, using two classification models: **Random Forest** and **Support Vector Machine (SVM)**. The work follows the CRISP-DM methodology.

## Dataset

- **Maternal Health Risk** (Ahmed, 2020), UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/863/maternal+health+risk (licence: CC BY 4.0)
- 1,014 records, 6 numeric features (Age, SystolicBP, DiastolicBP, BS, BodyTemp, HeartRate) and the target RiskLevel.
- After removing 2 records with an impossible heart rate (7 bpm) and the exact duplicates, 451 records were used.

## Repository contents

| File | Description |
|---|---|
| `CA1_Notebook.ipynb` | Jupyter notebook with all the code, charts and explanations |
| `maternal_health_risk.csv` | Original dataset (unchanged) |
| `README.md` | This file |

## How to run

1. Install Python 3 with pandas, matplotlib, seaborn, scipy and scikit-learn (all included in Anaconda).
2. Keep `CA1_Notebook.ipynb` and `maternal_health_risk.csv` in the same folder.
3. Open the notebook in Jupyter and run all cells in order.

## Methods

- **Data preparation:** removal of duplicates (to avoid data leakage) and impossible values, plus data quality checks.
- **Feature significance:** Kruskal-Wallis and ANOVA tests, correlation matrix.
- **Models:** Random Forest and SVM (RBF kernel, StandardScaler).
- **Validation:** stratified splits with 5%, 15% and 25% test sets, and 5-fold stratified cross-validation.
- **Tuning:** GridSearchCV on the 25% split.
- **Evaluation:** accuracy, confusion matrices, precision, recall, F1-score and feature importance.
- **Deployment:** a simple example in which the final model predicts the risk level of new patients.

## Main results

| Model (25% test split) | CV accuracy | Test accuracy |
|---|---|---|
| Random Forest (tuned) | 0.716 | 0.770 |
| SVM (tuned) | 0.684 | 0.690 |

- The tuned Random Forest was chosen as the final model (best CV and test accuracy, high-risk recall 0.821).
- Blood sugar and systolic blood pressure are the most important predictors.
- Tuning removed the overfitting of Random Forest (the train-test accuracy gap fell from 0.277 to almost zero).

## Reference

Ahmed, M. (2020) *Maternal Health Risk* [Dataset]. UCI Machine Learning Repository. Available at: https://doi.org/10.24432/C5DP5D (Accessed: 9 November 2026).
