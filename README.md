# CLV Prediction for Online Retail Customers

## Project Objective
To predict **Customer Lifetime Value (CLV)** using probabilistic models (**BG/NBD** & **Gamma-Gamma**) based on past transaction data.  
This allows businesses to estimate future revenue from individual customers and **optimize marketing investment** accordingly.

---

## Dataset Used
- `Online Retail`  
By: [Chen, D. (2015). Online Retail [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5BW33.](https://archive.ics.uci.edu/dataset/352/online+retail)

---

## Business Questions Answered
- Which customers are worth investing in for long-term retention?
- How much revenue can we expect from each customer in the future?
- What is the predicted average transaction value of each customer?
- How frequently will a customer likely make a purchase in the future?

---

## Process

### 1. Data Cleaning and Preparation
- Removed null values, duplicates, unnecessary columns, and canceled orders 
- Converted date fields and calculated total price per transaction  
- Filtered data to include only transactions with **positive quantity and price**  
  *[View cleaned dataset](https://github.com/zidvision/CLV-Prediction/blob/main/Data/Online_Retail_Cleaned.csv)*
  
### 2. Feature Engineering
Created a customer summary from transaction data with key features:
- **Frequency:** Number of repeat purchases  
- **Recency:** Time between first and last purchase  
- **T (Customer Age):** Time between first purchase and end of dataset  
- **Monetary:** Average revenue per transaction

  *[Explore the code](https://github.com/zidvision/CLV-Prediction/blob/main/Code/Preparation_for_Modelling.ipynb)*
  
  *[View Data for Modeling](https://github.com/zidvision/CLV-Prediction/blob/main/Data/Data_for_Modeling.csv)*
---

## CLV Modeling

### BG/NBD Model (Beta-Geometric Negative Binomial Distribution)
- Predicts the number of **future transactions** a customer will make

  *[Explore the code](https://github.com/zidvision/CLV-Prediction/blob/main/Code/BG-NBD_Model.ipynb)*
  
### Gamma-Gamma Model
- Predicts the **average value** of those future transactions

  *[Explore the code](https://github.com/zidvision/CLV-Prediction/blob/main/Code/Gamma-Gamma_Model.ipynb)*
  
Combined both models to estimate **Expected Customer Lifetime Value**

  *[Explore the code](https://github.com/zidvision/CLV-Prediction/blob/main/Code/CLV%20_Prediction.ipynb)*

---

## Model Outputs

- Trained models saved using `joblib`:
  - `bgf_model.joblib` — BG/NBD model
    *[[View Model](https://github.com/zidvision/CLV-Prediction/blob/main/Models/bgf_model.joblib)]*
  - `ggf_model.joblib` — Gamma-Gamma model
    *[[View Model](https://github.com/zidvision/CLV-Prediction/blob/main/Models/ggf_model.joblib)]*

- CLV predictions generated for each customer
- Results exported in `.csv` format

*[View CLV Predictions](https://github.com/zidvision/CLV-Prediction/blob/main/Data/CLV_Predicted.csv)*

---

## Key Insights

- Highly Skewed CLV Distribution. Majority of customers are predicted to have a low CLV, with a small portion projected to generate significantly higher revenue.
This indicates the classic Pareto Principle (80/20 rule), where a minority of customers contribute the majority of future revenue.

- Top Customers Stand Out Significantly. Most of the top 10 customers exhibit a CLV exceeding $20,000, with one customer predicted to generate nearly $140,000 in future revenue. These customers are prime targets for loyalty programs and marketing strategies focused on direct interaction.

- Based on Gamma-Gamma modeling results, the average customer is estimated to spend approximately $471,000 per transaction.

- The results of the BG/NBD model indicate that each customer is predicted to make an average of 1.49 future transactions within three months.
This means that most customers are likely to make at least one repeat purchase, with retention opportunities that can be optimized through loyalty programs or automated reminders.

---

## Conclusion

- Predictive CLV modeling highlights a clear disparity in future value across customers.

- Businesses can leverage this information to:

  - Personalize retention strategies for high-value customers

  - Avoid overinvesting in low-potential segmentsn       

  - Drive smarter resource allocation across acquisition, loyalty, and support efforts

- This approach transforms static past purchase analysis into a forward-looking strategy for sustainable growth.

---

## Tools & Libraries Used
- Excel
- Python
- Jupyter Notebook
- `Lifetimes`
- `Pandas`, `Matplotlib`, `Seaborn`
- `Joblib`
