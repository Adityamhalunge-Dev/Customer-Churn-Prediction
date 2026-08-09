# Customer churn prediction using machine learning

An end-to-end machine learning project to predict customer churn using the **IBM Telco Customer Churn dataset**. This project demonstrates the complete analytics workflow, including **data cleaning, exploratory data analysis (EDA), feature engineering, predictive modeling, model evaluation, and business interpretation**.

---

## Project overview

Customer churn is one of the most important challenges for subscription-based businesses because losing existing customers directly impacts revenue and customer lifetime value (CLV).

The objective of this project is to build a classification model that predicts whether a customer will churn and identify the factors that contribute most to churn behavior.

<Box background="surface" border={{size:1,color:"default"}} radius="3xl" padding={4} gap={2}><Row justify="between"><Text weight="semibold">Dataset</Text><Text>IBM Telco Customer Churn</Text></Row><Row justify="between"><Text weight="semibold">Customers analyzed</Text><Text>7,032</Text></Row><Row justify="between"><Text weight="semibold">Churn rate</Text><Text>26.6%</Text></Row><Row justify="between"><Text weight="semibold">Best model</Text><Text>Logistic Regression</Text></Row><Row justify="between"><Text weight="semibold">Accuracy</Text><Text>80.5%</Text></Row><Row justify="between"><Text weight="semibold">ROC AUC</Text><Text>0.836</Text></Row></Box>

---

## Project workflow

<Box width="100%" background="surface" border={{size:1,color:"default"}} radius="3xl" padding={4}><Row justify="between" align="center" width="100%" gap={2}><Text size="sm">Data cleaning</Text><Icon name="arrow-right" color="secondary"/><Text size="sm">EDA</Text><Icon name="arrow-right" color="secondary"/><Text size="sm">Feature engineering</Text><Icon name="arrow-right" color="secondary"/><Text size="sm">Modeling</Text><Icon name="arrow-right" color="secondary"/><Text size="sm">Evaluation</Text></Row></Box>

---

## Exploratory data analysis

### Customer churn distribution

![Churn Distribution](churn_distribution.png)

### Key findings from EDA

* **26.6% of customers churned**
* Customers with **shorter tenure** were significantly more likely to churn
* Customers with **higher monthly charges** showed a higher probability of churn
* Long-term customers were much more likely to remain active

---

## Machine learning models

Two classification models were developed and evaluated.

<Table columnSizing="equal"><Table.Row header><Table.Cell>Model</Table.Cell><Table.Cell>Accuracy</Table.Cell><Table.Cell>ROC AUC</Table.Cell></Table.Row><Table.Row><Table.Cell>Logistic Regression</Table.Cell><Table.Cell>**0.805**</Table.Cell><Table.Cell>0.836</Table.Cell></Table.Row><Table.Row><Table.Cell>Random Forest</Table.Cell><Table.Cell>0.791</Table.Cell><Table.Cell>**0.838**</Table.Cell></Table.Row></Table>

The Logistic Regression model achieved the best balance between predictive performance and churn detection, making it the preferred model for customer retention analysis.

---

## Feature importance

The Random Forest model identified the following variables as the strongest predictors of churn.

![Feature Importance](feature_importance.png)

Top predictive features:

* **Tenure**
* **TotalCharges**
* **MonthlyCharges**
* **InternetService (Fiber Optic)**
* **Contract type**

---

## Business insights

The analysis suggests that customer churn is primarily driven by **customer tenure, pricing, and contract structure**.

### Key business insights

* Customers with **short tenure** are at the highest risk of churn
* **Higher monthly charges** increase churn probability
* Customers with **two-year contracts** are significantly less likely to churn
* Fiber optic customers require closer monitoring due to their higher churn importance

### Business implication

The company should prioritize **early retention campaigns**, **contract renewal strategies**, and **targeted interventions for high-value customers with short tenure and high monthly charges**. These actions could reduce churn and improve customer lifetime value (CLV).

---

## Tools and libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn

---

## Repository structure

```text
customer-churn-prediction/
├── Customer_Churn_Prediction.ipynb
├── churn_distribution.png
├── feature_importance.png
└── README.md
```

---

## How to run

1. Clone this repository
2. Open `Customer_Churn_Prediction.ipynb` in Jupyter Notebook or Google Colab
3. Install the required Python libraries
4. Run the notebook from top to bottom

---

## Project highlights

* End-to-end machine learning workflow
* Business-oriented churn analysis
* Comparative model evaluation
* Feature importance interpretation
* Actionable customer retention insights

---

This project was created as part of my **Data Analytics and Consumer Insight portfolio**, focusing on predictive modeling, customer analytics, and business decision support.
