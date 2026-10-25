# 📊 Customer Churn Intelligence & Retention Prediction Engine

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E.svg?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458.svg?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-013243.svg?logo=numpy&logoColor=white)](https://numpy.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()

> An end-to-end predictive analytics framework designed to detect early churn signals in subscription services, quantify customer attrition risk, and empower revenue teams with actionable retention strategies.

---

## 🎯 Executive Overview

Customer acquisition costs (CAC) across the telecommunications and subscription sectors have surged in recent years. Industry benchmarks indicate that acquiring a new subscriber is **5x to 7x more costly** than retaining an existing customer. Furthermore, reducing attrition by just **5%** can elevate overall profitability by up to **25% to 95%**.

This repository delivers a complete data science pipeline using the **IBM Telco Customer Churn dataset** (7,032 verified subscriber profiles). It transitions raw demographic, account, and transactional records into an interpretable machine learning system that pinpoints high-risk accounts prior to service termination.

---

## 🏗️ Architecture & Pipeline Flow

```
┌─────────────────────────┐
│ Raw Telecom Dataset     │  (7,043 rows, 21 multi-modal features)
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Data Sanitation & Clean │  • Empty TotalCharges handling & type casting
└───────────┬─────────────┘  • Missing value imputation (7,032 valid records retained)
            │
            ▼
┌─────────────────────────┐
│ Feature Engineering &   │  • One-hot encoding for nominal categories
│ Matrix Transformation   │  • Min-Max scaling for continuous numeric predictors
└───────────┬─────────────┘  • Stratified 80/20 train-test partition
            │
            ▼
┌─────────────────────────┐
│ Predictive Modeling     │  • Baseline: Logistic Regression (Probability Calibrated)
│ & Validation            │  • Ensemble: Random Forest Classifier (Non-linear interactions)
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Business Evaluation &   │  • ROC-AUC & Confusion Matrix analysis
│ Retention Playbook      │  • Top-K Feature ranking & Prescriptive interventions
└─────────────────────────┘
```

---

## 📁 Repository Structure

```plaintext
customer-churn-prediction/
│
├── Customer_Churn_Prediction.ipynb   # Main end-to-end analytical notebook
├── churn_distribution.png            # EDA visual: Attrition vs. Active customer base
├── feature_importance.png            # Model visual: Random Forest feature ranking
└── README.md                         # Project documentation and reproduction guide
```

---

## 🔍 Exploratory Data Analysis & Key Discoveries

The dataset encompasses customer demographics, subscribed services (voice, multi-line, fiber optic, streaming), and contractual billing setups.

<div align="center">
  <img src="churn_distribution.png" alt="Customer Churn Distribution" width="600px" />
</div>

### Primary Data Findings:
* **Attrition Baseline**: The overall subscriber churn rate settles at **26.6%** (1,869 churned vs. 5,163 retained).
* **The "Tenure Cliff"**: Attrition is heavily concentrated within the **first 1 to 12 months** of customer onboarding. Customers crossing the 24-month mark exhibit dramatically reduced departure probabilities.
* **Pricing & Billing Friction**: Accounts with higher monthly billing bands ($70 – $100+/month) churn at twice the rate of lower-tier customers.
* **Contractual Dependency**: Month-to-month contracts demonstrate the highest vulnerability, whereas 1-year and 2-year commitments anchor customer retention.
* **Service Vector Risk**: Fiber Optic internet subscribers experience significantly higher churn rates compared to DSL or voice-only customers, signalling potential product expectation or reliability gaps.

---

## 🤖 Model Performance & Evaluation Benchmark

Both linear and non-linear classification architectures were trained and validated on an independent **test split of 1,407 subscribers**.

| Evaluation Metric | Logistic Regression (Recommended) | Random Forest Classifier |
| :--- | :---: | :---: |
| **Overall Accuracy** | **80.5%** | 79.1% |
| **ROC - AUC Score** | **0.836** | **0.838** |
| **Class 1 (Churn) Precision** | **0.65** | 0.64 |
| **Class 1 (Churn) Recall** | **0.57** | 0.48 |
| **Class 1 (Churn) F1-Score** | **0.61** | 0.55 |
| **Model Interpretability** | High (Log-odds coefficients) | Moderate (Gini feature importance) |
| **Primary Strength** | Superior Churn Recall & Probability Calibration | Strongest separation (highest ROC-AUC) |

> **Model Selection Rationale**: While Random Forest achieved a slightly higher raw ROC-AUC (0.838), **Logistic Regression** is selected as the primary decision engine due to its significantly higher **recall (57% vs. 48%)** on churners and its transparent probability outputs, allowing risk scores to be directly mapped into customer tiers.

---

## 📈 Feature Importance & Strategic Drivers

Variable importance was computed to reveal which operational dimensions most aggressively shift the probability needle toward attrition:

<div align="center">
  <img src="feature_importance.png" alt="Feature Importance Ranking" width="700px" />
</div>

### Top 5 Predictors:
1. **Tenure**: Customer lifetime length serves as the single strongest retention anchor.
2. **Total Charges**: Cumulative lifetime spend reflecting relationship depth and billing longevity.
3. **Monthly Charges**: Current price burden impacting price-sensitive consumer segments.
4. **Internet Service (Fiber Optic)**: Strong indicator of high customer expectations and competitive alternatives.
5. **Contract Type (Month-to-Month)**: Lack of contractual lock-in creates low switching barriers.

---

## 💼 Prescriptive Business Retention Playbook

Based on empirical model drivers, the following proactive retention framework is recommended:

| Risk Trigger | Target Segment | Recommended Strategic Action |
| :--- | :--- | :--- |
| **Onboarding Vulnerability** | Tenure < 6 Months | Implement an automated 90-day onboarding check-in sequence with customer success outreach and setup incentives. |
| **Fiber Optic Discontent** | Fiber Optic + High Monthly Bill | Conduct service quality audits; offer temporary loyalty pricing or bundle streaming perks to reinforce perceived value. |
| **Month-to-Month Exposure** | Flexible monthly billing | Target users with discounted annual lock-in offers (e.g., 2 months free with a 12-month contract). |
| **Payment Method Friction** | Electronic check payers | Incentivize auto-pay via credit card/bank transfer with a one-time bill credit, reducing involuntary payment lapses. |

---

## 🚀 Getting Started & Reproduction

### Prerequisites
* Python 3.8 or higher installed on your system.

### 1. Clone the Repository
```bash
git clone https://github.com/Adityamhalunge-Dev/Customer-Churn-Prediction.git
cd customer-churn-prediction
```

### 2. Set Up a Virtual Environment (Recommended)
```bash
# On Windows
python -m venv venv
.\venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

### 4. Run the Analysis Notebook
```bash
jupyter notebook Customer_Churn_Prediction.ipynb
```

---

## 🔮 Roadmap & Future Enhancements

- [ ] **Advanced Gradient Boosting**: Benchmark LightGBM, XGBoost, and CatBoost with Bayesian Hyperparameter Optimization (`Optuna`).
- [ ] **Explainable AI (XAI)**: Implement `SHAP` (SHapley Additive exPlanations) for local, customer-level reason codes.
- [ ] **Real-Time API**: Package the selected model into a lightweight `FastAPI` endpoint for real-time scoring.
- [ ] **Threshold Optimization**: Align classification decision thresholds with financial cost-benefit matrices (cost of retention offer vs. lost customer lifetime value).

---

## 📄 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT) - feel free to adapt, extend, and deploy in research or commercial settings.
