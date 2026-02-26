# 📊 Customer Churn Prediction using Logistic Regression

## 📖 Introduction

Customer churn - the rate at which customers stop doing business with a company - is a critical metric in the telecommunications industry.

This project builds a **Logistic Regression model** to predict customer churn using demographic, service usage, and account information.

The objective is to:
- Identify key churn drivers
- Improve customer retention strategies
- Build an interpretable and reliable prediction model

---

# 📁 Dataset Overview

- 7,043 customers
- 21 features
- Target variable: `Churn`

### Feature Categories

**Demographics**
- Gender
- SeniorCitizen
- Partner
- Dependents

**Services**
- PhoneService
- MultipleLines
- InternetService
- OnlineSecurity
- OnlineBackup
- DeviceProtection
- TechSupport
- StreamingTV
- StreamingMovies

**Account Information**
- Contract
- PaperlessBilling
- PaymentMethod
- Tenure
- MonthlyCharges
- TotalCharges

---

# 🔧 Data Preprocessing

- No missing values found
- Converted `TotalCharges` to numeric
- Encoded categorical variables
- Feature engineering applied

---

# 📊 Exploratory Data Analysis

### Key Correlations

- Tenure ↔ TotalCharges → 0.825
- MonthlyCharges ↔ TotalCharges → 0.650
- Contract ↔ Tenure → 0.672
- Contract ↔ Churn → -0.307

Insights:
- Long-term contracts reduce churn
- Short tenure increases churn risk
- Higher monthly charges are associated with higher churn

---

# 🧠 Feature Engineering

Created new features:

- `Tenure_Contract` → Interaction between tenure and contract
- `AvgMonthlyCharge = TotalCharges / (Tenure + 1)`
- `Tenure²`
- `MonthlyCharges²`

Dropped:
- `TotalCharges` (high multicollinearity)

---

# ⚙️ Model Building

- Logistic Regression
- Train-Test Split (80-20)
- Standard Scaling
- Performance evaluation using AUC and Accuracy

---

# 📈 Model Performance

| Metric | Initial Model | Improved Model |
|--------|---------------|----------------|
| Pseudo R² | 0.2906 | 0.3054 |
| AUC | 0.83 | 0.84 |
| Accuracy | 0.79 | 0.79 |

Final Model AUC: **0.84**

## 📌 Conclusion

The Logistic Regression model provides valuable insights into customer churn factors in the telecommunications industry. With an AUC of **0.84**, the model demonstrates strong predictive performance and reliable discrimination between churned and retained customers.

### 🔎 Key Factors Influencing Churn

- **Contract Type** - Customers on month-to-month contracts are significantly more likely to churn compared to those on long-term contracts.
- **Tenure** - Customers with shorter tenure exhibit a higher probability of churn.
- **Senior Citizen Status** - Senior customers show different churn behavior patterns.
- **Tech Support Services** - Customers without tech support are more likely to leave.
- **Internet Service Type** - Fiber optic users display higher churn risk compared to DSL users.

### 💡 Business Implications

By focusing on these high-impact areas, the company can:

- Promote long-term contract incentives
- Target early-tenure customers with retention campaigns
- Offer bundled services including tech support
- Design specialized plans for high-risk customer segments
