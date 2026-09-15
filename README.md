# FUTURE_DS_02
Customer Retention &amp; Churn Analysis
# 📊 Future Interns – Data Science & Analytics Task 2

## Customer Retention & Churn Analysis

### 📌 Internship Task

This project was completed as part of the **Future Interns Data Science & Analytics Internship – Task 2**.

The objective of this task is to analyze customer data from a subscription-based business to understand:

- Why customers are leaving the platform
- Which customer segments are most likely to churn
- How long customers typically remain active
- What factors are associated with customer retention
- What actions can help reduce customer churn

The analysis was performed using **Power BI** with data cleaning and transformation through **Power Query**.

---

# 🎯 Project Objective

Customer churn is an important business problem for subscription-based companies.

The main objectives of this project are to:

1. Clean and prepare customer subscription data
2. Calculate customer churn and retention metrics
3. Identify customer segments with higher churn
4. Analyze customer lifetime and tenure patterns
5. Analyze retention across different subscription characteristics
6. Identify potential churn and retention drivers
7. Build an interactive Power BI dashboard
8. Provide actionable business recommendations

---

# 📂 Dataset

### Dataset Used

**Telco Customer Churn Dataset**

The dataset contains customer-level information from a telecommunications subscription business.

### Dataset Source

Kaggle – Telco Customer Churn Dataset:

https://www.kaggle.com/datasets/blastchar/telco-customer-churn

### Dataset Size

- Approximately **7,043 customer records**
- 21 customer, service, and account-related attributes

### Important Columns

Some of the important columns used in the analysis include:

- `customerID`
- `gender`
- `SeniorCitizen`
- `Partner`
- `Dependents`
- `tenure`
- `PhoneService`
- `MultipleLines`
- `InternetService`
- `OnlineSecurity`
- `OnlineBackup`
- `DeviceProtection`
- `TechSupport`
- `StreamingTV`
- `StreamingMovies`
- `Contract`
- `PaperlessBilling`
- `PaymentMethod`
- `MonthlyCharges`
- `TotalCharges`
- `Churn`

---

# 🛠️ Tools Used

### Power BI

Power BI was used to:

- Clean and transform the dataset
- Create calculated columns
- Create DAX measures
- Perform churn and retention analysis
- Analyze customer lifetime patterns
- Create interactive dashboards
- Present business insights

### Power Query

Power Query was used for:

- Data type correction
- Missing-value handling
- Data validation
- Data transformation
- Data preparation before analysis

---

# 🧹 Data Cleaning & Preparation

The dataset was inspected and cleaned before creating the dashboard.

## 1. Customer ID

The `customerID` column was checked to ensure that each customer could be uniquely identified.

Data type:

**Text**

---

## 2. Tenure

The `tenure` column represents the number of months a customer has remained with the company.

Data type:

**Whole Number**

---

## 3. Monthly Charges

The `MonthlyCharges` column represents the customer's monthly subscription charges.

Data type:

**Decimal Number**

---

## 4. Total Charges

The `TotalCharges` column contained missing/null values.

The affected records had:

- `tenure = 0`
- `TotalCharges = null`

These customers were newly subscribed and had not accumulated any charges yet.

Therefore, the missing `TotalCharges` values were replaced with:

**0**

This prevents the records from being removed while maintaining a logical value for customers with zero tenure.

---

## 5. Churn

The `Churn` column contains two categories:

- `Yes` – Customer churned
- `No` – Customer retained

The column was used as the primary target for churn and retention analysis.

---

# 📐 Data Transformation

Several calculated fields and measures were created in Power BI to support the analysis.

## Churn Flag

A binary churn flag was created:

```DAX
Churn Flag =
IF(
    'Telco Customer Churn'[Churn] = "Yes",
    1,
    0
)
Where:

1 = Churned
0 = Not Churned
Retention Flag

A retention flag was created:

Retention Flag =
IF(
    'Telco Customer Churn'[Churn] = "No",
    1,
    0
)

Where:

1 = Retained
0 = Churned
📊 Key DAX Measures
Total Customers
Total Customers =
DISTINCTCOUNT(
    'Telco Customer Churn'[customerID]
)
Churned Customers
Churned Customers =
CALCULATE(
    DISTINCTCOUNT(
        'Telco Customer Churn'[customerID]
    ),
    'Telco Customer Churn'[Churn] = "Yes"
)
Retained Customers
Retained Customers =
CALCULATE(
    DISTINCTCOUNT(
        'Telco Customer Churn'[customerID]
    ),
    'Telco Customer Churn'[Churn] = "No"
)
Churn Rate
Churn Rate =
DIVIDE(
    [Churned Customers],
    [Total Customers],
    0
)

The result was formatted as a percentage.

Retention Rate
Retention Rate =
DIVIDE(
    [Retained Customers],
    [Total Customers],
    0
)

The result was formatted as a percentage.

👥 Customer Lifetime / Tenure Analysis

The dataset does not contain an actual customer signup date.

Therefore, a traditional signup-month cohort analysis could not be performed.

Instead, customer tenure was used as a proxy for customer lifetime cohorts.

The following tenure groups were created:

Tenure	Customer Lifetime Group
0–6 months	New Customers
7–12 months	Early Stage
13–24 months	Developing
25–36 months	Established
37–48 months	Loyal
49–60 months	Long-Term
61–72 months	Very Long-Term

These groups were used to analyze how churn and retention change throughout the customer lifecycle.

📊 Power BI Dashboard

The final Power BI dashboard was organized into three analytical pages.

📄 Page 1 – Executive Overview

The first page provides a high-level summary of customer retention and churn.

KPI Cards

The following KPIs were included:

Total Customers
Churned Customers
Churn Rate
Retention Rate
Average Tenure
Total Revenue
Visualizations
1. Churn vs Retention

Shows the overall distribution of customers who remained with the company versus customers who churned.

2. Churn Rate by Contract

Compares churn across:

Month-to-month
One year
Two year
3. Churn Rate by Tenure Group

Shows how customer churn changes across different customer lifetime stages.

4. Churn Rate by Internet Service

Compares churn patterns across different internet service categories.

📄 Page 2 – Churn Analysis

The second page focuses on identifying customers and subscription characteristics associated with churn.

Visualizations
1. Churn Rate by Contract

Analyzes whether contract type is associated with different churn levels.

2. Churn Rate by Payment Method

Compares churn across different payment methods.

3. Churn Rate by Internet Service

Analyzes churn patterns across internet service types.

4. Churn Rate by Monthly Charges

Examines the relationship between monthly subscription charges and customer churn.

5. Churn Rate by Tenure Group

Identifies customer lifetime stages with higher churn.

6. Customer Segment Analysis

Customer characteristics such as:

Senior Citizen
Partner
Dependents

were analyzed to identify segments with different churn patterns.

📄 Page 3 – Retention & Customer Lifetime Analysis

The third page focuses on customer retention and lifetime behavior.

Visualizations
1. Retention Rate by Tenure Group

Shows the percentage of customers retained across different lifetime stages.

2. Churn Rate by Tenure Group

Highlights customer lifetime stages where churn is higher.

3. Average Monthly Charges by Churn Status

Compares monthly charges between retained and churned customers.

4. Total Revenue by Churn Status

Compares revenue contribution from retained and churned customers.

5. Retention by Contract Type

Analyzes retention across different subscription contracts.

6. Retention by Service Usage

Examines how different services are associated with customer retention.

🎛️ Interactive Dashboard Filters

The dashboard includes slicers to allow users to explore customer behavior interactively.

The main slicers include:

Contract
Internet Service
Payment Method
Gender
Senior Citizen
Partner
Dependents
Tenure Group

These filters allow business users to investigate specific customer segments.

🔎 Key Analysis Areas

The analysis focuses on four major business questions.

1. Why are customers leaving?

Churn was analyzed based on:

Contract type
Payment method
Internet service
Monthly charges
Tenure
Customer demographics
Service usage

This helps identify customer groups where churn is relatively high.

2. Which customer segments are most likely to churn?

Customer segments were compared using:

Contract
Tenure
Internet Service
Payment Method
Senior Citizen status
Partner status
Dependents
Service subscriptions

This helps identify segments that may require targeted retention strategies.

3. How long do customers typically stay active?

Customer tenure was analyzed using lifetime groups:

New Customers
Early Stage
Developing
Established
Loyal
Long-Term
Very Long-Term

Churn and retention rates were compared across these groups to understand customer lifetime patterns.

4. What actions can improve customer retention?

Based on the analysis, businesses can consider:

Encouraging customers to move from short-term to long-term contracts
Providing targeted retention offers to high-risk customers
Improving customer support for segments showing higher churn
Reviewing pricing for customers with high monthly charges
Creating special onboarding programs for new customers
Providing loyalty benefits to long-term customers
💡 Business Insights

The analysis demonstrates several important patterns that are useful for subscription-based businesses.

Insight 1 – Contract Type

Contract type is an important factor to consider when analyzing churn.

Customers on different contract types show different levels of churn, making contract structure an important area for retention strategies.

Insight 2 – Customer Tenure

Customer lifetime is an important indicator of retention behavior.

Customers at different tenure stages show different churn patterns, allowing businesses to identify stages of the customer lifecycle that require additional attention.

Insight 3 – Customer Segmentation

Churn is not uniform across all customers.

Analyzing customer demographics, services, contract type, and payment methods helps businesses identify segments with relatively higher churn.

Insight 4 – Pricing and Charges

Monthly charges can be compared against churn behavior to identify whether customers with higher subscription costs show different retention patterns.

This can help businesses evaluate pricing and targeted offers.

Insight 5 – Service Usage

Different combinations of subscribed services can be analyzed to understand their relationship with customer retention.

This can help businesses identify opportunities for improving service value and customer engagement.

🚀 Actionable Recommendations

Based on the analysis, the following strategies can help improve customer retention.

1. Encourage Long-Term Contracts

Provide discounts, loyalty benefits, or additional services to encourage customers to move from month-to-month contracts to longer-term plans.

2. Focus on New Customers

Customers in the early stages of their lifecycle can be given additional onboarding support and engagement campaigns.

This can help reduce early-stage churn.

3. Create Targeted Retention Campaigns

Use customer segmentation to identify high-risk groups and provide targeted offers instead of applying the same strategy to every customer.

4. Improve Customer Support

Customers showing higher churn patterns can be provided with proactive customer support and service assistance.

5. Review Pricing Strategies

Customers with higher monthly charges can be analyzed for price sensitivity.

Businesses can consider personalized plans, discounts, or value-added services where appropriate.

6. Reward Loyal Customers

Long-term customers can be offered loyalty rewards, special benefits, or personalized plans to encourage continued subscription.

📈 Business Value

This analysis can help a subscription business:

Reduce customer churn
Improve customer retention
Identify high-risk customer segments
Understand customer lifetime behavior
Improve customer engagement
Develop targeted retention campaigns
Support data-driven business decisions
🧠 Skills Demonstrated

This project demonstrates practical skills in:

Data Cleaning
Data Transformation
Power Query
Power BI
DAX
Customer Churn Analysis
Customer Retention Analysis
Customer Segmentation
Cohort/Lifetime Analysis
KPI Development
Data Visualization
Business Intelligence
Business Insight Generation
Data-Driven Decision Making
📁 Project Structure
FUTURE_DS_02/
│
├── README.md
│
├── FUTURE_DS_02.pbix
│
├── Dataset/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
└── Dashboard/
    └── Customer_Retention_Churn_Dashboard.png
📊 Dashboard Preview

The Power BI dashboard provides an interactive view of:

Customer churn
Customer retention
Customer lifetime
Contract-based churn
Tenure-based churn
Customer segmentation
Payment methods
Internet services
Revenue and charges
🏁 Conclusion

The Customer Retention & Churn Analysis project demonstrates how customer subscription data can be transformed into meaningful business insights.

Using Power BI and Power Query, the dataset was cleaned, transformed, analyzed, and presented through an interactive dashboard.

The analysis focuses on understanding:

Who is leaving, who is staying, how long customers remain active, which segments show higher churn, and what businesses can do to improve customer retention.

The project demonstrates a complete data analytics workflow from data preparation to business recommendations.

👩‍💻 Project Information

Project: Customer Retention & Churn Analysis
Task: Future Interns – Data Science & Analytics Task 2
Domain: Customer Analytics / Subscription Analytics
Tool: Microsoft Power BI
Data Preparation: Power Query
Analysis: DAX + Power BI
Dataset: Telco Customer Churn Dataset
Project Type: Data Analytics & Business Intelligence

🔗 Dataset

https://www.kaggle.com/datasets/blastchar/telco-customer-churn
