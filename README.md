# Student Performance Predictor & Educational Analytics Report

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-latest-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

An end-to-end data science and machine learning workflow designed to analyze student demographics, socioeconomic indicators, and academic metrics to predict and evaluate mathematics performance.

---

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Methodology & Modeling Workflow](#-methodology--modeling-workflow)
- [Model Evaluation & Performance Metrics](#-model-evaluation--performance-metrics)
- [Key Findings & Insights](#-key-findings--insights)
- [Key Drivers (Feature Coefficients)](#-key-drivers--feature-coefficients)
- [Getting Started & Installation](#-getting-started--installation)
- [License](#-license)

---

## 🔍 Project Overview

This project establishes a rigorous statistical and machine learning pipeline to analyze what drives student success in mathematics. By leveraging baseline literacy assessments (reading and writing scores), demographic background, parental education levels, and school lunch status, our final optimized regression model achieves an **$R^2$ score of approximately 0.88**. 

This indicates that **88% of the variance** in mathematics performance can be accurately explained and predicted using this feature set.

---

## ⚙️ Methodology & Modeling Workflow

The analytical pipeline is structured into four core phases:

1. **Data Cleaning & Preprocessing:**
   - Standardized column headers into clean `snake_case` format.
   - Performed integrity checks ensuring zero duplicate records and deployed standard imputation strategies.
   - Engineered advanced interaction features, including average literacy score (`literacy_avg`), literacy-to-math score gaps (`score_diff`), and cross-domain interaction metrics (`score_product`).

2. **Feature Encoding:**
   - Applied One-Hot Encoding to categorical attributes (gender, ethnicity/race group, parental education level, lunch status, and test preparation course completion).
   - Dropped baseline dummy columns to prevent multi-collinearity issues.

3. **Baseline vs. Full Model Comparison:**
   - **Baseline Linear Model:** Evaluated a simplified linear regression using only reading and writing scores as predictors ($R^2 \approx 0.68$).
   - **Full Linear Model:** Incorporated engineered socio-demographic features and encoded indicators ($R^2 \approx 0.88$).

4. **Tree-Based Ensembles:**
   - Benchmarked non-linear ensemble models including **Random Forest Regression** and **Gradient Boosting Regression** to inspect feature importance rankings and detect non-linear data structures.

---

## 📊 Model Evaluation & Performance Metrics

| Model Architecture | Training $R^2$ | Test $R^2$ | Mean Absolute Error (MAE) | Root Mean Squared Error (RMSE) |
| :--- | :---: | :---: | :---: | :---: |
| **Baseline Linear Regression** | 0.675 | 0.681 | 7.35 | 8.79 |
| **Full Linear Regression** | **0.884** | **0.879** | **4.21** | **5.39** |
| **Random Forest Regressor** | 0.981 | 0.852 | 4.64 | 6.00 |
| **Gradient Boosting Regressor** | 0.912 | 0.868 | 4.34 | 5.65 |

> *Note: Linear Regression demonstrated optimal generalization on the unseen test set, successfully avoiding the mild overfitting observed in tree-based algorithms due to strong continuous linearity between domain scores.*

---

## 💡 Key Findings & Insights

* **Primary Predictors:** Standardized reading and writing scores account for the vast majority of continuous variance in mathematics success.
* **Test Preparation Impact:** Students who completed a test preparation course performed on average **4 to 6 score points higher** than non-completers, controlling for all other variables.
* **Socioeconomic Factor (Lunch Status):** Standard/unsubsidized lunch status correlates with a positive score shift, highlighting the impact of nutritional security on cognitive focus and academic achievement.
* **Parental Education Level:** Higher levels of parental education (e.g., Master's or Bachelor's degrees) consistently exert a positive linear coefficient on student outcomes compared to high school-only baselines.

---

## 📈 Key Drivers (Feature Coefficients)

The relative direction and magnitude of key non-academic feature impacts derived from the full linear model coefficients:

```text
Positive Performance Drivers:
  [+] Completed Test Preparation Course  (High Positive Impact)
  [+] Standard Lunch Access              (Moderate/High Positive Impact)
  [+] Advanced Parental Degree           (Moderate Positive Impact)

Negative Performance Drivers / Gaps:
  [-] None/Incomplete Test Prep          (Baseline / Negative Delta)
  [-] Free/Reduced Lunch Status          (Negative Delta relative to Standard)
```

---

## 🚀 Getting Started & Installation

To run this data science pipeline locally in your VS Code environment:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/student-performance-analytics.git
   cd student-performance-analytics
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Jupyter Notebook or Python Script:**
   ```bash
   jupyter notebook
   ```

---
