<h1 align="center"> AI-Powered Customer Retention Prediction System</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-blue.svg">
  <img src="https://img.shields.io/badge/Machine_Learning-Logistic_Regression-green.svg">
  <img src="https://img.shields.io/badge/Status-Stage_1_Complete-orange.svg">
</p>

---

<h2 align="center">📝 Project Overview</h2>
The goal of this project is to use <b>Machine Learning</b> to predict "Customer Churn". Churn happens when a customer stops using a company’s service. By identifying these customers early, a business can take action to keep them, which saves money and increases revenue.

<h2 align="center"> 💼 Business Problem</h2>

* 💰 **Cost Factor:** Acquiring a new customer is 5 times more expensive than keeping an existing one.
* 📉 **Revenue Loss:** When customers leave, it directly impacts the company’s profit and reputation.
* ⚠️ **Challenge:** Companies often fail to see the early signs of a customer being unhappy.

<h2 align="center"> 📂 Data Description</h2>

* 👥 **Demographics:** Gender, Senior Citizen, Partner, and Dependents.
* 🌐 **Services:** Phone service, Internet (DSL/Fiber optic), Online Security, and Streaming.
* 💳 **Account Info:** Tenure, Contract type, and Payment Method.
* 🎯 **Target Variable:** **Churn (Yes/No)** – This is what we want to predict.

---

<h2 align="center"> 🗺️ Project Roadmap</h2>

| Stage | Task | Status |
| :--- | :--- | :--- |
| **Stage 1** | Data Pipeline | ✅ Completed |
| **Stage 2** | Model Development | ✅ Completed |
| **Stage 3** | Explainability (SHAP/LIME) | 🏗️ In Progress |
| **Stage 4** | Deployment (Streamlit) | ⏳ Pending |

---

<h2 align="center"> ✅ Stage 1: Data Pipeline & Preprocessing</h2>

In this stage, I prepared the raw data for the Machine Learning model. The following steps were taken:

* 🧹 **Handling Missing Values:** I found 11 missing values in the `TotalCharges` column. These rows were removed to ensure data accuracy.
* 🗑️ **Feature Removal:** I dropped the `customerID` column as it does not provide any pattern for predicting churn.
* 🔢 **Categorical Encoding:** Converted text data (Gender, Contract, etc.) into numeric values using **One-Hot Encoding**.
* 📊 **Final Dataset:** The dataset grew from 20 to 31 columns, all in **numeric format**.

<h2 align="center">📊 EDA & Visual Insights</h2>

<p align="center"> <b>Project Flowchart Overview</b>
<br>
<img src="reports/EDA.jpg" width="450"> </p>

* 🟢 **Target Analysis (Churn Distribution):** <p align="center"><img src="reports/churn_dist.png" width="400"></p> 
  The data is imbalanced. More customers stay (0) than leave (1).

* 🔵 **Numerical Data Distribution:** <p align="center"><img src="reports/Numerical_data_distribution.png" width="450"></p> 
  Analyzed the spread of Tenure and Monthly Charges.

* 🟠 **Outlier Detection:** <p align="center"><img src="reports/outliers.png" width="450"></p> 
  Used Boxplots to ensure data quality.

* 🧠 **Feature Correlation (Heatmap):** <p align="center"><img src="reports/heatmap.png" width="450"></p> 
  * **Tenure vs. Churn (-0.35):** Longer stay = Lower churn.
  * **Monthly Charges vs. Churn (0.19):** Higher bills = Higher churn risk.

  

<h2 align="center">🤖 Stage 2: Model Development & Evaluation</h2>

In this stage, I built the predictive engine using Machine Learning. I focused on training a model that can look at customer patterns and calculate the probability of them leaving.

* **🧠 Algorithm Selection:** I started with **Logistic Regression** as the baseline model. It is a powerful algorithm for **binary classification** (Predicting Yes or No).
* **⚖️ Feature Scaling:** Since features like **TotalCharges** have high values and **tenure** has low values, I applied **StandardScaler** to normalize the data. This ensures the model treats all features fairly.
* **✂️ Train-Test Split:** The data was split into **80% for training** (to let the model learn) and **20% for testing** (to check how well it performs on new data).

<h2 align="center">🔍 Key Predictive Insights</h2>

Based on the model's coefficients and my exploratory data analysis (EDA), here are the most important factors driving churn:

* **⏳ Tenure:** Customers with a **longer history** with the company are much less likely to churn.
* **💵 Monthly Charges:** As monthly bills increase, the risk of the customer leaving also increases.
* **📝 Contract Type:** Customers on **"Two-year"** contracts are much more stable than those on **"Month-to-month"** plans.

<h2 align="center">📊 Stage 3: Model Comparison & Final Selection</h2>

To ensure the highest accuracy, I evaluated **7 different Machine Learning algorithms**. Testing diverse models allowed me to compare different mathematical approaches like Linear, Ensemble, and Boosting.

### 📈 Algorithm Performance Table

The following table summarizes the accuracy scores of all the models tested:

| Algorithm | Accuracy Score | Category | Status |
| :--- | :--- | :--- | :--- |
| **XGBoost** | **79.67%** | **Boosting** | **🏆 Winner** |
| **SVM (Support Vector Machine)** | 79.53% | Linear/Non-linear | High Performer |
| **Logistic Regression** | 78.70% | Baseline | Reliable |
| **Random Forest** | 78.46% | Ensemble | Stable |
| **Decision Tree** | 77.54% | Rule-based | Simple |
| **KNN (K-Nearest Neighbors)** | 75.26% | Similarity-based | Moderate |
| **Naive Bayes** | 65.74% | Probability-based | Low |

### 📉 Deep Dive: Confusion Matrix Analysis
Beyond accuracy, I analyzed the **Confusion Matrix** for each algorithm individually to understand the type of errors (False Positives vs. False Negatives). 

* **Recall Matters:** In churn prediction, missing an actual churner (False Negative) is more expensive for the business. 
* **Observation:** XGBoost and SVM provided the best balance, catching the highest number of actual churners compared to other models.



### 🏆 Final Model Choice: XGBoost
I have finalized **XGBoost** for the deployment phase. 

**Reasons:** 
1. Highest accuracy (79.67%).
2. Best handling of complex, non-linear relationships in customer data.
3. Excellent performance in minimizing False Negatives.




