# Churn-Analysis

Churn analysis is the process of identifying and understanding why customers stop using a product or service. Churn analysis isn’t only about predicting who will leave, it’s about understanding why they did. Data helps spot patterns, reveal trends, and drive action before it’s too late.

## Types of Churn

- **Voluntary Churn** – When customers actively choose to leave due to dissatisfaction, better alternatives, or pricing concerns.  
- **Involuntary Churn** – When customers are lost due to failed payments, expired subscriptions, or other unintentional reasons.  

## Why Churn Analysis Matters

- **Revenue Protection** – Reducing churn helps maintain a steady revenue stream.  
- **Customer Insights** – Understanding why customers leave helps businesses improve their offerings.  
- **Targeted Retention Strategies** – Identifying at-risk customers allows for proactive engagement to keep them.  
- **Operational Efficiency** – Acquiring new customers is more expensive than retaining existing ones.  

## Key Steps in Churn Analysis

1. **Defining Churn** – Determining whether churn is voluntary (customer cancels) or involuntary (payment failure, inactivity).  
2. **Data Collection & Preparation** – Gather customer data, transaction history, engagement metrics, and support interactions.  
3. **Exploratory Data Analysis (EDA)** – Identifying trends, correlations, and potential churn indicators.    
4. **Insights & Actionable Strategies** – Developing retention strategies such as personalized offers, proactive customer engagement, and loyalty programs to reduce churn.  

Churn analysis is widely used in telecom, SaaS, finance, and e-commerce industries to improve customer retention and business growth.

## Dataset Description  

- **Number of Rows:** 7,043  
- **Number of Columns:** 23  

### Column Headers and Descriptions  

1. **customerID** *(int)* – Unique identifier for each customer.  
2. **gender** *(string)* – Customer’s gender (Male/Female).  
3. **SeniorCitizen** *(int)* – Indicates if the customer is a senior citizen (1 = Yes, 0 = No).  
4. **Partner** *(string)* – Whether the customer has a partner (Yes/No).  
5. **Dependents** *(string)* – Whether the customer has dependents (Yes/No).  
6. **tenure** *(int)* – Number of months the customer has stayed with the company.  
7. **PhoneService** *(string)* – Whether the customer has phone service (Yes/No).  
8. **MultipleLines** *(string)* – Whether the customer has multiple phone lines (Yes/No/No phone service).  
9. **InternetService** *(string)* – Type of internet service (DSL, Fiber optic, No).  
10. **OnlineSecurity** *(string)* – Whether the customer has online security service (Yes/No/No internet service).  
11. **OnlineBackup** *(string)* – Whether the customer has online backup service (Yes/No/No internet service).  
12. **DeviceProtection** *(string)* – Whether the customer has device protection (Yes/No/No internet service).  
13. **TechSupport** *(string)* – Whether the customer has tech support service (Yes/No/No internet service).  
14. **StreamingTV** *(string)* – Whether the customer has streaming TV service (Yes/No/No internet service).  
15. **StreamingMovies** *(string)* – Whether the customer has a streaming movie service (Yes/No/No internet service).  
16. **Contract** *(string)* – Type of contract (Month-to-month, One year, Two year).  
17. **PaperlessBilling** *(string)* – Whether the customer has paperless billing (Yes/No).  
18. **PaymentMethod** *(string)* – Payment method used (Electronic check, Mailed check, Bank transfer, Credit card).  
19. **MonthlyCharges** *(float)* – Monthly amount charged to the customer.  
20. **TotalCharges** *(float)* – Total amount charged.  
21. **numAdminTickets** *(int)* – Number of administrative support tickets raised by the customer.  
22. **numTechTickets** *(int)* – Number of technical support tickets raised by the customer.  
23. **Churn** *(string)* – Whether the customer has churned (Yes/No).  

## Problem Statement  

Customer retention is critical in the telecom industry, as acquiring new customers is costly and time-consuming. Currently, the retention efforts are reactive, they reach out to customers only after they have already terminated their contracts. This approach limits our ability to prevent churn effectively.  

Despite previous attempts to analyze customer data using Excel, those efforts have not yielded actionable insights. They need a data-driven, predictive approach to identify at-risk customers before they churn. Additionally, they require clear and visually intuitive insights to support management in making informed retention decisions.  
A more proactive strategy will help them reduce churn, improve customer satisfaction, and drive business growth.
- **Business Questions**  
Which customer segments are most likely to churn, and what factors contribute to their decision?

## Data Cleaning & Transformation

For this project, I focused on refining the dataset to improve clarity and usability. Key transformations included:  

- **Currency Formatting:** The `MonthlyCharges` and `TotalCharges` columns were converted from plain numerical values to a currency format in **US dollars ($)** for better readability and financial analysis.  
- **Customer Loyalty Categorization:** A new `Loyalty` column was created during the **initial data transformation and load** in Power BI using **Power Query (M language)**. This column categorizes customers based on their tenure:  

  ```M
  Loyalty = 
      if [tenure] < 12 then "<1 year" 
      else if [tenure] < 24 then "<2 years" 
      else if [tenure] < 36 then "<3 years" 
      else if [tenure] < 48 then "<4 years" 
      else if [tenure] < 60 then "<5 years" 
      else if [tenure] < 72 then "<6 years" 
      else "6+ years"

These transformations helped standardize financial data and improve customer segmentation, enabling better insights for retention analysis and churn prediction. 🚀

<img width="121" alt="loyalty column" src="https://github.com/user-attachments/assets/6f1eb3ab-dad7-41d0-ba7f-c87642615f55" />



