🛍️ Customer Shopping Behavior Analysis
> Uncovering actionable insights from 3,900 purchases to guide strategic business decisions — using Python, SQL, and Power BI.
---
📋 Table of Contents
Project Overview
Dataset
Tech Stack
Project Structure
Data Preparation
SQL Analysis
Key Findings
Strategic Recommendations
How to Run
Dashboard
---
📌 Project Overview
This end-to-end data analysis project explores customer shopping behavior to identify revenue drivers, customer segments, and product performance patterns. The analysis combines Python-based data wrangling, SQL querying via PostgreSQL/MySQL/SQL Server, and Power BI dashboarding to deliver a comprehensive view of customer purchasing habits.
Business Questions Addressed:
Which customer segments contribute the most revenue?
Do subscribed customers spend more than non-subscribers?
How does shipping preference relate to purchase value?
Which products receive the best reviews?
How can customers be segmented into actionable loyalty tiers?
---
📊 Dataset
Attribute	Value
Source	`customer_shopping_behavior.csv`
Records	3,900 transactions
Features	18 columns
Missing Values	37 (in `Review Rating` column only)
Key Columns:
Column	Description
`Customer ID`	Unique identifier per customer
`Age`	Customer age
`Gender`	Male / Female
`Item Purchased`	Product name
`Category`	Product category (e.g., Clothing, Footwear)
`Purchase Amount (USD)`	Transaction value
`Review Rating`	Product rating (1–5)
`Subscription Status`	Whether the customer is subscribed
`Shipping Type`	Express, Standard, Free Shipping, etc.
`Discount Applied`	Yes / No
`Previous Purchases`	Count of past purchases
`Frequency of Purchases`	Shopping cadence (Weekly, Monthly, etc.)
---
🛠️ Tech Stack
Tool	Purpose
Python (pandas)	Data loading, cleaning, feature engineering
MySQL	Analytical SQL queries
SQLAlchemy	Python–database bridge
Power BI	Interactive dashboard
Jupyter Notebook	Exploratory data analysis
---
📁 Project Structure
```
customer-shopping-behavior-analysis/
│
├── customer_shopping_behavior.csv          # Raw dataset
├── Customer_Shopping_Behavior_Analysis.ipynb  # Python EDA & data prep notebook
├── sql_project.sql                         # SQL analytical queries
├── customer_behaviour_analysis.pbix        # Power BI dashboard
└── Customer-Shopping-Behavior-Analysis.pptx  # Presentation of findings
```
---
🔧 Data Preparation
All data cleaning and feature engineering was performed in the Jupyter Notebook:
Loading — Imported dataset using `pandas.read_csv()`
Exploration — Checked structure with `.info()` and `.describe()`
Missing Value Handling — Imputed `Review Rating` with the median rating per product category
Column Renaming — Standardized all columns to `snake_case`; renamed `purchase_amount_(usd)` → `purchase_amount`
Feature Engineering:
`age_group` — Created 4 quantile-based age bands: Young Adult, Adult, Middle-aged, Senior
`purchase_frequency_days` — Mapped text frequency labels (e.g., "Weekly" → 7, "Monthly" → 30) to integer day values
Deduplication — Verified `discount_applied` and `promo_code_used` were identical columns; dropped `promo_code_used`
Database Export — Loaded the cleaned DataFrame into a relational database using SQLAlchemy for SQL analysis
---
🗄️ SQL Analysis
Ten business questions were answered using SQL (compatible with PostgreSQL, MySQL, and SQL Server):
#	Question
Q1	Total revenue by gender
Q2	Discount users who still spent above average
Q3	Top 5 products by average review rating
Q4	Average purchase amount: Standard vs. Express shipping
Q5	Do subscribed customers spend more?
Q6	Top 5 products by discount usage rate
Q7	Customer segmentation: New / Returning / Loyal
Q8	Top 3 most purchased products per category (window functions)
Q9	Are repeat buyers more likely to subscribe?
Q10	Revenue contribution by age group
> See [`sql_project.sql`](sql_project.sql) for all queries.
---
💡 Key Findings
💰 Revenue & Demographics
Female customers generate slightly higher total revenue than male customers, suggesting gender-based marketing could optimize returns.
Adult and Middle-aged groups are the top revenue contributors by age group.
📦 Shipping & Purchase Value
Express shipping customers spend ~12% more per transaction ($65 avg) compared to Standard shipping ($58 avg).
Premium shipping selection is a strong signal of higher-value buyers.
🎟️ Subscriptions
Subscribers account for 45% of total revenue despite being fewer in number.
Subscribed customers show 68% higher spend and a 78% loyalty rate vs. non-subscribers.
Repeat buyers (>5 purchases) are more likely to be subscribers.
🏷️ Discounts
A meaningful group of customers use discounts and still spend above average — a "smart shopper" segment worth targeting with exclusive premium offers.
⭐ Top-Rated Products
Blouse, Dress, and Shirt are the top 3 highest-rated products (all rating ≥ 4/5).
👥 Customer Segments
Segment	Share	Definition
New	50%	1 previous purchase
Returning	35%	2–10 previous purchases
Loyal	15%	11+ previous purchases
---
🎯 Strategic Recommendations
Boost Subscriptions — Promote exclusive subscriber benefits; they drive disproportionate revenue.
Loyalty Programs — Reward returning customers to convert them into loyal, high-LTV buyers.
Targeted Marketing — Focus campaigns on high-revenue segments (subscribers, express shipping users, adult age groups).
Product Positioning — Feature top-rated products (Blouse, Dress, Shirt) prominently in campaigns.
Smart Shopper Offers — Target discount-using, high-spend customers with premium exclusive deals.
---
▶️ How to Run
Python Notebook
```bash
# 1. Clone the repository
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis

# 2. Install dependencies
pip install pandas sqlalchemy pymysql jupyter

# 3. Launch the notebook
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```
SQL Queries
Load the cleaned dataset into MySQL, then run:
```bash
mysql -u root -p customer_behavior < sql_project.sql
```
Power BI Dashboard
Open `customer_behaviour_analysis.pbix` in Power BI Desktop to explore the interactive dashboard.
---
📈 Dashboard
The Power BI dashboard (`customer_behaviour_analysis.pbix`) visualizes all key metrics including revenue by gender, subscription impact, shipping preferences, customer segmentation, and top-rated products.
---
🙌 Acknowledgements
Dataset used for educational and analytical purposes. All analysis performed independently as a portfolio project.
