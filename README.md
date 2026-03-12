# 📊 Customer Lifetime Value (CLV) Analysis & Prediction
End-to-End Data Science Project · UK Online Retail Dataset · 541,909 Transactions

## 📌 Table of Contents
	∙	Project Overview
	∙	Business Problem
	∙	Dataset
	∙	Project Pipeline
	∙	Key Results
	∙	Customer Segments
	∙	Tech Stack
	∙	How to Run
	∙	Skills Demonstrated
	∙	Author

  ## 🧭 Project Overview
This project delivers a complete, production-style Customer Lifetime Value analysis on real UK e-commerce transaction data. Starting from 541,909 raw transactions, the project moves through data cleaning, RFM feature engineering, statistical CLV modelling using the BG/NBD + Gamma-Gamma framework, and unsupervised machine learning customer segmentation using K-Means clustering.
The goal is not just to build models — it is to answer real business questions with data and translate the findings into clear, actionable recommendations that a non-technical stakeholder can act on.

## 💼 Business Problem
A UK-based online retailer with over half a million transactions and thousands of customers needed a data-driven approach to understand customer value and prioritise retention efforts. Three core business questions drove every analytical decision in this project:

### Business Questions
    Q1 Who are our most valuable customers and how do we identify them reliably?
    Q2 Which customers are at risk of churning and how much revenue is at stake?
    Q3 How much Revenue can we predict from our customer base in the next 90 days?

## 📂 Dataset

    Attribute              Detail
    Source:               UCI Machine Learning Repository
    Dataset:              https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset
    Raw Rows:             541,909 transaction
    Period:                December 2010 - December 2011
    Geography:            United Kingdom(Primary focus)
    Customers:             ~3,900 Unique UK customers after cleaning
    Columns:               InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country

### Data Cleaning Steps
	∙	✅ Removed rows with missing CustomerID (~25% of raw data)
	∙	✅ Removed cancelled transactions (InvoiceNo starting with 'C')
	∙	✅ Removed rows with Quantity <= 0 (returns and errors)
	∙	✅ Removed rows with UnitPrice <= 0 (zero-price records)
	∙	✅ Filtered to UK customers only
	∙	✅ Converted CustomerID to integer and InvoiceDate to datetime
	∙	✅ Engineered TotalPrice column: Quantity × UnitPrice

  ## 🔁 Project Pipeline

 Raw Data (541,909 rows)
 
        │
        ▼
┌─────────────────────────────────┐

Stage 1 · Business Understanding  │  Define problem, KPIs, business questions 

└─────────────────┬───────────────┘

                  │
                  ▼
                  
┌─────────────────────────────────┐

Stage 2 · Data Loading & EDA   │  Load, explore, clean, validate 

└─────────────────┬───────────────┘

                  │
                  ▼
                  
┌─────────────────────────────────┐

Stage 3 · RFM Engineering      │  Recency · Frequency · Monetary + quintile scoring 

└─────────────────┬───────────────┘

                  │
                  ▼
                  
┌─────────────────────────────────┐

Stage 4 · Predictive CLV       │  BG/NBD + Gamma-Gamma → 90-day CLV per customer │

└─────────────────┬───────────────┘

                  │
                  ▼
                  
┌─────────────────────────────────┐

Stage 5 · K-Means Clustering   │  k=3 (Silhouette=0.90) → Champion · Loyal · At Risk │ 

└─────────────────────────────────┘

## 📈 Key Results

    Metric                    Value
    Customers Analysed        3,900 + UK customers
    Optimal Clusters (k)      3
    Silhouette Score          0.90 (Excellent - well-Seperated Clusters)
    Prediction Window         90 days
    Gross Margin Applied      20%
    Monthly Discount Rate     1%

    Why k=3 over k=4?k=4 was initially tested but produced a Silhouette Score of 0.56 — indicating poor cluster separation and unreliable segment boundaries. K=3 scored 0.90, confirming three genuinely distinct customer groups. The decision was driven by data not assumption.

## 👥 Customer Segments
Three segments were discovered by K-Means and named by analysing their full financial profile. CLV and monetary value were the primary naming criteria — recency and frequency provided supporting context.


   ### 🏆 Champions — Cluster 1

     Metric                Value
    Avg Recency           163 days
    Avg Frequency         1.5 purchases
    Avg Order Value       £66,670
    Historical CLV        £24,566
    Predicted CLV(90d)    £5,648
    Despite the longest inactivity window, Champions are the highest-value customers by every financial metric. Their extraordinary average order value of £66,670 suggests       wholesale or institutional buyers. A single re-engaged Champions customer is worth more than 1,800 At Risk customers combined.
    Action: Personal win-back outreach, exclusive VIP offer, direct account manager contact.

    

  ### 🔄 Loyal Customers — Cluster 2

    Metric               Value
    Avg Recency         6 days
    Avg Frequency       63 purchases
    Avg Order Value      £188
    Historical CLV       £13,175
    Predicted CLV (90d)   £2,537
    The most operationally active segment — last purchase just 6 days ago with an average of 63 transactions. Their CLV is driven by extraordinary frequency rather than unit price. These are the business engine and must be protected.
    Action: Loyalty rewards program, cross-sell and upsell campaigns, referral incentives.

### ⚠️ At Risk — Cluster 0

    Metric                Value
    Avg Recency          93 days
    Avg Frequency        3.9 purchases
    Avg Order Value      £37
    Historical CLV       £288
    Predicted CLV (90d)   €70
    Lowest value across all metrics. Drifting toward dormancy with a predicted 90-day CLV of just £70. These customers do not justify high-cost retention investment.
    Action: Automated low-cost re-engagement emails, seasonal promotions, browse abandonment triggers.

  ## 🛠 Tech Stack
    # Core
    pandas          # Data manipulation and feature engineering
    numpy           # Numerical operations

    # Modelling
    lifetimes       # BG/NBD and Gamma-Gamma CLV models
    scikit-learn    # K-Means clustering, StandardScaler, Silhouette Score

    # Visualisation
    matplotlib      # Base plotting
    seaborn         # Statistical visualisation

  ## ▶️ How to Run
1. Clone the Repository

        git clone https://github.com/Promise-Emefile/Customer-LifeTime-Value-Analysis.git
        cd Customer-LifeTime-Analysis
2. Install Dependencies

       pip install -r requirements.txt
3. Download the Dataset

Download the UCI Online Retail Dataset from 🔗https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset in the data/ folder.

4. Run the Notebook
   
       jupyter notebook

### Requirements
    pandas>=1.3.0
    numpy>=1.21.0
    scikit-learn>=1.0.0
    lifetimes>=0.11.3
    matplotlib>=3.4.0
    seaborn>=0.11.0
    openpyxl>=3.0.0
    jupyter>=1.0.0
## 🧠 Skills Demonstrated
    Area                     Techniques Applied
    Data Engineering        pandas • data cleaning • datetime handling •feature engineering
    Statistical Modelling   BG/NBD model • Gamma-Gamma model • lifetimes library
    Machine Learning        K-Means clustering • StandardScaler • Silhouette Score • Elbow Method
    Feature Engineering     RFM framework • quintile scoring • snapshot date methodology
    Data Visualisation      matplotlib • seaborn
    Business Communication  Cluster profiling • naming rationale • segment action recommendations

## 👤 Author
Promise EmefileData Analyst & AI Engineer · Lagos, Nigeria (Open to Remote, Hybrid and Onsite)



*“The model is only 20% of the work. The other 80% is asking the right business question, cleaning the data properly, and communicating the findings clearly.”*
