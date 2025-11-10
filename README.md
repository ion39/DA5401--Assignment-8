

# **DA5401 A8: Ensemble Learning for Complex Regression – Bike Share Demand Prediction**

### Name: Pragati L  
### Roll No: CE22B089


## **Overview**

This project explores three primary ensemble learning techniques—**Bagging, Boosting, and Stacking**—to predict bike rental demand in a city using the **Bike Sharing Demand Dataset**. The goal is to minimize prediction error (RMSE) for the total hourly bike rental count (`cnt`) by addressing **bias** and **variance** in regression models.

## **Dataset**

* **Name:** Bike Sharing Demand Dataset (Hourly Data)
* **Samples:** ~17,000 hourly observations
* **Source:** Fanaee-T, Hadi, and Gamper, H. (2014), [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset)

## **Project Structure**

### **Part A: Data Preprocessing and Baseline Models**

1. **Data Loading & Feature Engineering**

   * Removed irrelevant columns: `instant`, `dteday`, `casual`, `registered`
   * Encoded categorical variables (One-Hot Encoding for `season`, `weathersit`, `mnth`, `hr`)

2. **Train/Test Split**

   * Split data into training and testing sets.

3. **Baseline Models**

   * **Decision Tree Regressor** (max depth=6)
   * **Linear Regression**
   * Evaluated using **RMSE**; better-performing model serves as the baseline.

### **Part B: Ensemble Techniques**

#### **1. Bagging (Variance Reduction)**

* Implemented **Bagging Regressor** with Decision Tree as base learner.
* Trained multiple trees on bootstrapped samples.
* Evaluated **RMSE** to check for variance reduction compared to baseline.

#### **2. Boosting (Bias Reduction)**

* Implemented **Gradient Boosting Regressor**.
* Sequentially trained weak learners to correct errors of previous models.
* Evaluated **RMSE** to observe bias reduction relative to baseline and Bagging.


### **Part C: Stacking (Optimal Performance)**

* **Principle:** Meta-learner combines predictions of diverse base learners to optimize final prediction.

**Level-0 (Base Learners):**

1. K-Nearest Neighbors Regressor
2. Bagging Regressor (from Part B)
3. Gradient Boosting Regressor (from Part B)

**Level-1 (Meta-Learner):**

* Ridge Regression

* **Stacking Regressor** trained using out-of-fold predictions.

* Evaluated final **RMSE** on test set.

### **Part D: Final Analysis**

**Conclusions**

* Stacking was identified to be the best-performing model identified.
* Explanation based on **bias-variance tradeoff** and **model diversity**:

  * Bagging reduces variance.
  * Boosting reduces bias.
  * Stacking combines strengths of multiple models for superior performance.

## **Installation and Requirements**

* **Running the Notebook:**

  1. Download the `hour.csv` dataset from the UCI repository and change the path accordingly.
  2. Open the Jupyter Notebook.
  3. Run all cells sequentially.
  4. View plots, RMSE results, and comparative analysis.

