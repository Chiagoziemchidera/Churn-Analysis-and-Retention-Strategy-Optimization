# Churn-Analysis & Retention Strategy Optimization

![istockphoto-2157150390-612x612](https://github.com/user-attachments/assets/3f6c7772-0f36-4d1e-b1ee-6e23fa627b43)


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
What factors contributed to their decision to churn?

## Data Cleaning & Transformation

I refined the dataset to improve clarity and usability. Key transformations included:  

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


- **DAX formula can be seen in [DAX Formula](https://github.com/Chiagoziemchidera/Churn-Analysis/blob/main/DAX-Formula).

## Analysis Insights and Recommendations

<img width="595" alt="churn1" src="https://github.com/user-attachments/assets/97d1a092-fb3e-4a3a-821b-b24c155b5fcb" />


<img width="591" alt="churn2" src="https://github.com/user-attachments/assets/ac827dce-c1a2-4474-b99f-06ae924d8ebb" />

 

## ** 1️. Short-Term Contracts & First-Year Customers Are at High Risk**  
📊 **55% of churned customers were on month-to-month contracts, while only 21% had one-year contracts and 24% had two-year contracts.**  
📊 **29% of churned customers left within their first year, with churn rates decreasing as tenure increases.**  

💡 **Insight:**  
Customers on **short-term contracts or in their first year** are significantly more likely to leave due to a lack of commitment, early dissatisfaction, or unmet expectations.  

✅ **Recommendations:**  
- **Push longer contracts** with discounts, exclusive perks, or bundling options to lock in customers.  
- **Improve onboarding** by providing proactive customer support, tutorials, and engagement within the first 90 days.  
- **Offer retention incentives** like a 6-month loyalty discount to encourage longer tenure.  

## ** 2️. Fiber Optic Customers Have the Highest Churn Rate**  
📊 **41.89% of fiber optic users churn, compared to 18.96% of DSL users and 7.40% of customers with no internet.**  

💡 **Insight:**  
Despite being a premium service, fiber optic users are leaving at a **higher rate**, likely due to **service issues, high pricing, or unmet expectations.**  

✅ **Recommendations:**  
- **Investigate service complaints:** Are there frequent outages or slow speeds? Address network issues.  
- **Improve customer support:** Prioritize fiber optic customers with faster issue resolution and VIP service options.  
- **Introduce retention incentives:** Discounts, loyalty rewards, or free service upgrades to keep fiber users engaged.  

## ** 3️. Electronic Check Users Face the Highest Churn Risk**  
📊 **34% of churned customers used electronic checks for payments, compared to 23% using mailed checks, 22% using bank transfers, and 22% using credit cards.**  

💡 **Insight:**  
Customers using **electronic checks may face payment failures, security concerns, or inconvenience**, making them more likely to leave.  

✅ **Recommendations:**  
- **Encourage auto-pay setups** via credit card or bank transfer with discounts or bonuses.  
- **Simplify payment processes** for electronic check users and reduce failed transaction rates.  
- **Investigate customer feedback** to understand why electronic check users are dissatisfied.  

## ** 4️. High Monthly Charges Drive Churn**  
📊 **Customers with higher monthly bills are more likely to churn, with an average monthly charge of $74.44 among churned customers.**  

💡 **Insight:**  
Customers may feel they are **overpaying** or **not receiving enough value** for the price.  

✅ **Recommendations:**  
- **Introduce tiered pricing models** to offer more flexibility and affordability.  
- **Provide bundled discounts** to make high-cost plans feel more valuable.  
- **Offer premium benefits** (priority support, exclusive content, or loyalty rewards) to justify higher pricing.  

## ** 5️. Service Bundling Reduces Churn**  
📊 **91% of churned customers used phone services, while 44% had streaming TV & movies.**  
📊 **Customers with tech support & online security services had lower churn (only 17% & 16% adoption among churned users).**  

💡 **Insight:**  
Customers who bundle multiple services (e.g., internet + streaming + tech support) **tend to stay longer**, while single-service users (e.g., internet-only) **are more likely to churn.**  

✅ **Recommendations:**  
- **Cross-sell & bundle services** (e.g., internet + streaming TV) at a discounted rate.  
- **Promote value-added services** like tech support & security with free trials.  
- **Reward multi-service customers** with loyalty benefits or exclusive perks.

## ** 6️. Tech Support & Online Security Services Are Underutilized**  
📊 Only 17% of churned customers had tech support, and 16% had online security services.  

💡 **Insight:** These add-ons have low adoption, which suggests that customers do not see enough value in them or are unaware of their benefits.  

✅ **Recommendation:** Promote tech support and security services through free trials, proactive customer education, and bundling with internet services to improve perceived value.  
  

## ** Final Takeaways & Business Actions**  
📌 **Convert short-term contract users** into long-term subscribers through discounts & incentives.  
📌 **Fix service issues for fiber optic users** to reduce their unexpectedly high churn rate.  
📌 **Shift electronic check users** to more reliable payment methods with autopay incentives.  
📌 **Make high-cost plans feel worthwhile** through bundled discounts & premium perks.  
📌 **Encourage service bundling** to increase customer stickiness and long-term retention.  
 
