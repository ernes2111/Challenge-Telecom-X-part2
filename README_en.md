# 📡 Telecom X — Customer Churn Analysis and Prediction

[🇪🇸 Ver en Español](README.md) | [🇬🇧 Read in English](README_en.md)

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.8-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=flat)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)

---

## 📌 Project Description

This project was developed as part of a data analysis challenge for **Telecom X**, a telecommunications company facing a critical customer churn problem.

The work is divided into **two complementary parts**:

- **Part 1 — ETL and EDA:** Extraction, cleaning, and exploratory data analysis to understand the profile of customers who churn.  
  📎 Repository available at: https://github.com/ernes2111/Challenge-Telecom-X
- **Part 2 — Machine Learning:** Data preparation, training predictive models, and generating strategic insights to reduce churn (this repository).

Both parts make up a complete **end-to-end** workflow: from raw data to an actionable predictive model.

---

## 🗂️ Repository Structure

```
telecom-x-churn/
│
├── datos_tratados.csv           # Clean dataset generated in Part 1
├── TelecomX_Part1_EDA.ipynb     # Notebook Part 1: ETL and Exploratory Analysis
├── TelecomX_Part2_Final.ipynb   # Notebook Part 2: Predictive Modeling
├── README.md                    # Spanish documentation
└── README_en.md                 # English documentation
```

---

## 🔧 Part 1 — ETL and Exploratory Data Analysis (EDA)

> 📎 This stage is developed in detail in the repository:  
> https://github.com/ernes2111/Challenge-Telecom-X

### Objectives
- Extract and load raw data from the original source.
- Clean the dataset: handle null values, duplicates, and incorrect data types.
- Standardize column names and categorical values.
- Analyze the profile of churning customers through visualizations.

### Main EDA Findings

| Factor | Observation |
|---|---|
| **Tenure** | Customers with shorter tenure have a higher churn rate |
| **Contract type** | Month-to-month contracts account for the most cancellations |
| **Monthly charges** | Customers who churn tend to have higher monthly charges |
| **Demographics** | Customers without partners or dependents show greater instability |

---

## 🤖 Part 2 — Churn Prediction with Machine Learning

This stage uses the clean dataset generated in Part 1 (`datos_tratados.csv`) as input and transforms descriptive analysis into a predictive model applicable to the business.

### Complete Pipeline

```
Load cleaned data
        ↓
Cleaning and encoding (One-Hot)
        ↓
Class balance verification
        ↓
Train / Test Split (Stratified 80/20)
        ↓
Normalization (StandardScaler for LR)
        ↓
Model training
        ↓
Evaluation and comparison
        ↓
Variable interpretation + Conclusions
```

### 📊 Model Results

| Model | Accuracy | Precision | Recall | F1-Score | Train Acc. |
|---|:---:|:---:|:---:|:---:|:---:|
| **Logistic Regression** | 0.801 | 0.656 | **0.529** | **0.586** | 0.808 |
| Random Forest | 0.788 | 0.636 | 0.468 | 0.539 | 0.998 |

> ✅ **Selected model for production: Logistic Regression.**
> It achieves better Recall and F1-Score without overfitting (Train ≈ Test).
> The Random Forest shows clear overfitting (Train 99.8% vs Test 78.8%).

---

## 🔍 Most Influential Variables

Three methods agree on the same determining factors:

| Variable | Correlation | LR Coef. | RF Import. | Effect |
|---|:---:|:---:|:---:|:---:|
| `Antiguedad_Meses` | −0.35 | −1.32 | 15.7% | ↓ Reduces churn |
| `Contract_Two year` | — | −0.57 | 5.4% | ↓ Reduces churn |
| `InternetService_Fiber optic` | — | +0.64 | 3.5% | ↑ Increases churn |
| `Cargo_Total` | — | +0.62 | 17.0% | ↑ Increases churn |
| `Cargo_Mensual` | +0.19 | — | 14.0% | ↑ Increases churn |
| `Metodo_Pago_Electronic check` | — | +0.17 | 4.1% | ↑ Increases churn |

---

## 💡 Proposed Retention Strategies

### 🎯 1. Onboarding Program for New Customers
The first few months are the period of highest risk of abandonment.
- Progressive discounts during the first 6–12 months.
- Active onboarding: personalized follow-up, priority support.
- Activation of proactive campaigns based on the model score.

### 💰 2. Review of Fiber Optic Value Proposition
Customers with fiber optics have a higher probability of churn, possibly due to the perception of high cost.
- Offer bundled plans with higher perceived value.
- Price benchmarking against competitors.

### 📄 3. Incentives for Long-Term Contracts
Monthly contracts concentrate the highest risk.
- Discounts for annual or bi-annual contracts (e.g., 2 free months).
- Exclusive benefits for loyalty: upgrades, premium support.

### 📊 4. Model Implementation in Production
- Monthly customer scoring with Logistic Regression.
- Suggested risk threshold: churn probability > 0.60.
- Quarterly monitoring and retraining cycle.

---

## 🛠️ Technologies Used

| Library | Use |
|---|---|
| `pandas` | Data manipulation and analysis |
| `numpy` | Numerical operations |
| `matplotlib` / `seaborn` | Visualizations |
| `scikit-learn` | Models, metrics, and preprocessing |

---

## ▶️ How to Run the Project

1. Clone the repository:
```bash
git clone https://github.com/ernes2111/Challenge-Telecom-X-part2.git
cd Challenge-Telecom-X-part2
```

2. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

3. Run the notebooks in order:
   - `TelecomX_LATAM_en.ipynb` (or `TelecomX_LATAM.ipynb` for Spanish)
   - `TelecomX_Part2_Final.ipynb`

---

## 📝 Conclusion

Customer churn at Telecom X is **strongly determined by customer tenure, contract type, and monthly spending level**. The developed models allow anticipating with good accuracy which customers present the highest risk, providing a strategic tool to implement preventive actions and improve retention.

The practical application of this pipeline can generate a direct impact on reducing churn and improving the **Customer Lifetime Value (CLV)** of Telecom X.

---
