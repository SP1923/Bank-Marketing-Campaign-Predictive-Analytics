## Bank Marketing Campaign Predictive Analytics Using Machine Learning

---

# Chapter 1: Introduction

## 1.1 Project Title

**Bank Marketing Campaign Predictive Analytics Using Machine Learning**

## 1.2 Background

Banks depend heavily on customer deposits to generate revenue and maintain liquidity. One of the most common financial products offered by banks is the **Term Deposit**, where customers deposit money for a fixed period and receive interest in return.

The Portuguese bank used in this study experienced a decline in customer deposits. To address this issue, the bank conducted marketing campaigns through telephone calls to encourage customers to subscribe to term deposits.

However, marketing campaigns involve significant costs:

* Telecalling expenses
* Employee salaries
* Infrastructure costs
* Customer acquisition costs

Therefore, it becomes essential to identify which customers are more likely to subscribe to a term deposit before conducting campaigns.

This project applies **Machine Learning** techniques to predict customer responses and optimize marketing efforts.

---

## 1.3 Problem Statement

The bank wants to answer the following question:

**"Will a customer subscribe to a term deposit after a marketing campaign?"**

Predicting this outcome helps the bank:

* Reduce marketing costs
* Increase campaign effectiveness
* Improve conversion rates
* Target potential customers efficiently

---

## 1.4 Business Objective

The primary business objective is:

> To build a predictive model that identifies customers who are likely to subscribe to a term deposit, enabling the bank to focus marketing efforts on high-potential leads.

---

## 1.5 Project Objectives

The major objectives include:

1. Understanding customer behavior.
2. Performing exploratory data analysis.
3. Cleaning and preprocessing the data.
4. Engineering useful features.
5. Selecting important variables.
6. Building predictive machine learning models.
7. Evaluating model performance.
8. Generating actionable business recommendations.

---

# Chapter 2: Dataset Description

## 2.1 Dataset Overview

The project uses the **Bank Marketing Dataset**, collected from direct marketing campaigns of a Portuguese banking institution.

The dataset contains:

* Approximately 41,188 records
* 21 attributes
* Binary target variable

Target Variable:

| Variable | Description                                 |
| -------- | ------------------------------------------- |
| y        | Whether customer subscribed to term deposit |

Values:

* Yes
* No

---

## 2.2 Features Description

### Customer Information

| Feature   | Description           |
| --------- | --------------------- |
| age       | Customer age          |
| job       | Occupation            |
| marital   | Marital status        |
| education | Education level       |
| default   | Credit default status |
| housing   | Housing loan          |
| loan      | Personal loan         |

---

### Campaign Information

| Feature     | Description                        |
| ----------- | ---------------------------------- |
| contact     | Contact communication type         |
| month       | Last contact month                 |
| day_of_week | Last contact day                   |
| duration    | Call duration                      |
| campaign    | Number of contacts during campaign |

---

### Previous Campaign Information

| Feature  | Description                 |
| -------- | --------------------------- |
| pdays    | Days since previous contact |
| previous | Previous contacts           |
| poutcome | Previous campaign outcome   |

---

### Economic Indicators

| Feature        | Description               |
| -------------- | ------------------------- |
| emp.var.rate   | Employment variation rate |
| cons.price.idx | Consumer price index      |
| cons.conf.idx  | Consumer confidence index |
| euribor3m      | Euribor interest rate     |
| nr.employed    | Number of employees       |

---

# Chapter 3: Data Understanding and Exploration

## 3.1 Data Inspection

Initial steps included:

* Loading dataset
* Creating copy of dataset
* Checking dimensions
* Reviewing data types
* Understanding variable distributions

### Findings

* No missing values were observed.
* Both numerical and categorical variables were present.
* Several categorical columns contained "unknown" values.

---

## 3.2 Statistical Summary

Descriptive statistics revealed:

### Age

* Wide age distribution
* Majority customers between 30–50 years

### Campaign

* Most customers contacted only a few times
* Some customers received excessive contacts

### Duration

* Highly skewed distribution
* Longer calls correlated with successful subscriptions

---

## 3.3 Categorical Analysis

Frequency analysis was performed for:

* Job
* Marital status
* Education
* Housing loan
* Personal loan
* Previous outcomes

### Key Findings

#### Job Category

Major customer groups:

* Admin
* Technician
* Blue-collar workers

#### Education

Most customers had:

* University degree
* High school education

#### Marital Status

Most customers were:

* Married

---

# Chapter 4: Data Cleaning

## 4.1 Missing Value Analysis

A missing value matrix was generated.

### Results

No missing values were detected.

Therefore:

* No imputation was required.
* Dataset quality was considered good.

---

## 4.2 Handling Unknown Categories

Several categorical variables contained:

* Unknown

Examples:

* Education
* Job
* Housing loan
* Personal loan

These values were retained and later encoded.

---

## 4.3 Data Consistency Checks

Validation performed on:

* Numerical ranges
* Category labels
* Target variable

No major inconsistencies were found.

---

# Chapter 5: Exploratory Data Analysis (EDA)

## 5.1 Duration vs Job Role

Analysis examined relationship between:

* Occupation
* Call duration

### Insights

Customers with professional jobs generally had longer conversations.

Longer conversations often resulted in successful subscriptions.

---

## 5.2 Campaign Contacts vs Subscription

The project investigated:

* Number of calls
* Subscription outcome

### Findings

As the number of campaign contacts increased:

* Conversion rates decreased

This suggests excessive calling may annoy customers.

---

## 5.3 Campaign Month Analysis

Campaign performance varied significantly by month.

### Strong Months

* May
* June
* July

These months showed higher subscription rates.

### Weak Months

Several other months produced significantly lower conversions.

---

## 5.4 Economic Indicators Analysis

Quarterly indicators were analyzed.

Variables:

* Employment variation rate
* Consumer confidence
* Price index
* Euribor rate

### Findings

Economic conditions influence customer willingness to invest in deposits.

---

## 5.5 Marital Status Analysis

Comparison performed between:

* Single
* Married
* Divorced

### Findings

Marital status showed meaningful differences in subscription behavior.

---

## 5.6 Positive Deposit Analysis

The project compared positive subscriptions across multiple features.

Important factors included:

* Job
* Education
* Duration
* Month
* Previous campaign outcome

---

## 5.7 Correlation Analysis

Correlation matrix was generated.

Purpose:

* Detect relationships
* Identify multicollinearity
* Support feature selection

---

# Chapter 6: Feature Engineering

Feature engineering transformed raw data into machine-learning-ready format.

---

## 6.1 Education Category Grouping

Education categories were consolidated into broader groups.

Benefits:

* Reduced dimensionality
* Improved model learning

---

## 6.2 Month Encoding

Months were encoded numerically.

Example:

| Month | Encoded |
| ----- | ------- |
| Jan   | 1       |
| Feb   | 2       |
| Mar   | 3       |

---

## 6.3 Day-of-Week Encoding

Weekdays converted into numerical values.

This allowed machine learning algorithms to process them.

---

## 6.4 Handling pdays

Variable:

* pdays = 999

Meaning:

Customer never contacted before.

The value 999 was transformed into a more meaningful representation.

---

## 6.5 Ordinal Encoding

Applied to categorical variables having ordered relationships.

Examples:

* Education
* Previous outcomes

---

## 6.6 Frequency Encoding

Categories were replaced with frequency counts.

Benefits:

* Handles high-cardinality variables
* Preserves useful information

---

## 6.7 Target Guided Encoding

Categories were encoded using target subscription rates.

Advantages:

* Captures predictive strength
* Improves model performance

---

# Chapter 7: Feature Scaling

## Standardization

Numerical variables were standardized using:

[
Z = \frac{X-\mu}{\sigma}
]

Benefits:

* Faster convergence
* Improved model performance
* Better feature comparability

Variables scaled:

* Age
* Duration
* Campaign
* Economic indicators

---

# Chapter 8: Feature Selection

## Method Used

### Extra Trees Classifier

The project used:

**ExtraTreesClassifier**

to determine feature importance.

---

## Important Features Identified

Highly influential variables included:

### Duration

Most important feature.

Reason:

Longer customer engagement indicates stronger interest.

---

### Job

Customer occupation strongly affected subscription probability.

---

### Education

Higher educational qualifications influenced investment behavior.

---

### Previous Campaign Outcome

Past success strongly predicted future success.

---

### Economic Indicators

Macroeconomic conditions affected customer decisions.

---

## Features Removed

Several less influential features were dropped:

* pdays
* month
* cons.price.idx
* loan
* housing
* emp.var.rate

Removing them reduced complexity.

---

# Chapter 9: Model Development

## 9.1 Train-Test Split

Dataset split:

| Dataset  | Percentage |
| -------- | ---------- |
| Training | 80%        |
| Testing  | 20%        |

Purpose:

* Train model
* Evaluate generalization

---

## 9.2 Logistic Regression Model

The final model selected:

### Logistic Regression

Reason:

* Simple
* Interpretable
* High performance

Model equation:

[
P(Y=1)=\frac{1}{1+e^{-(b_0+b_1X_1+\cdots+b_nX_n)}}
]

---

## Hyperparameter Tuning

Regularization parameter:

[
C = 0.18420699693267145
]

This value provided optimal performance.

---

# Chapter 10: Model Evaluation

## Accuracy

The notebook reports:

### Mean Accuracy ≈ 92.4%

This indicates:

92 out of every 100 predictions are correct.

---

## Interpretation

High accuracy suggests:

* Effective feature engineering
* Strong predictive variables
* Suitable model choice

However, for banking applications, additional metrics should also be considered:

* Precision
* Recall
* F1 Score
* ROC-AUC

---

# Chapter 11: Business Insights

The project produced several actionable insights.

---

## Insight 1

Call duration is the strongest predictor.

### Recommendation

Train agents to engage customers effectively and understand their needs.

---

## Insight 2

Job type significantly affects conversion.

### Recommendation

Segment customers based on occupation.

Prioritize:

* Professionals
* Corporate employees
* Skilled workers

---

## Insight 3

Education influences subscriptions.

### Recommendation

Customize marketing messages based on educational background.

---

## Insight 4

Campaign timing matters.

### Recommendation

Focus campaigns during:

* May
* June
* July

---

## Insight 5

Economic indicators affect customer decisions.

### Recommendation

Align marketing budgets with favorable economic conditions.

---

# Chapter 12: Conclusion

This project successfully developed a predictive analytics framework for bank marketing campaigns.

The workflow included:

1. Data collection
2. Data cleaning
3. Exploratory data analysis
4. Feature engineering
5. Feature selection
6. Model development
7. Performance evaluation

The final Logistic Regression model achieved approximately **92.4% accuracy**, demonstrating strong predictive capability.

The study revealed that:

* Call duration is the most influential factor.
* Job and education strongly impact customer decisions.
* Campaign timing affects success rates.
* Economic conditions influence subscription behavior.

By implementing the recommendations generated from this analysis, the bank can improve campaign efficiency, reduce operational costs, and increase term deposit subscriptions.

---
