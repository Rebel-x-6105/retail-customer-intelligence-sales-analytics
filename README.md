# Retail Customer Intelligence & Sales Analytics

An end-to-end **Data Analytics portfolio project** that transforms raw retail customer data into actionable business insights using **Python, SQL, PostgreSQL, and Power BI**.

This project analyzes customer purchasing behavior, product performance, subscriptions, discounts, shipping preferences, customer loyalty, and revenue patterns to support data-driven retail decision-making.

---

## Project Overview

Retail businesses collect large volumes of customer transaction data, but raw data alone does not provide meaningful business value. The objective of this project is to convert customer shopping data into clear insights that can help a retail business better understand its customers, products, and revenue drivers.

The analysis follows a complete analytics workflow:

**Raw CSV Data → Python Data Cleaning & Feature Engineering → SQL Business Analysis → Power BI Dashboard → Business Insights & Recommendations**

The project demonstrates practical skills in data preparation, database analysis, visualization, and business communication.

---

## Business Objectives

The analysis focuses on questions such as:

* How does revenue vary across customer demographics?
* Do customers using discounts still generate meaningful revenue?
* Which products receive the highest customer ratings?
* Does shipping method affect average purchase value?
* Do subscribed customers spend more than non-subscribers?
* Which products depend most heavily on discounts?
* How can customers be segmented based on purchase history?
* Which products perform best within each product category?
* Are repeat customers more likely to subscribe?
* Which age groups contribute the most revenue?

---

## Dataset

The dataset contains **3,900 customer purchase records** and **18 original attributes** covering customer demographics, transaction details, product information, and purchasing behavior.

| Category         | Example Fields                             |
| ---------------- | ------------------------------------------ |
| Customer         | Customer ID, Age, Gender, Location         |
| Product          | Item Purchased, Category, Size, Color      |
| Transaction      | Purchase Amount, Season, Shipping Type     |
| Engagement       | Review Rating, Subscription Status         |
| Promotions       | Discount Applied, Promo Code Used          |
| Purchase History | Previous Purchases, Frequency of Purchases |
| Payment          | Payment Method                             |

### Initial Data Quality Finding

The raw dataset contained **37 missing values** in the `Review Rating` column. These values were imputed using the **median review rating of the corresponding product category**, preserving category-level behavior rather than applying a single overall value.

---

## Tech Stack

| Technology           | Purpose                                                                  |
| -------------------- | ------------------------------------------------------------------------ |
| **Python**           | Data cleaning, transformation, exploratory analysis, feature engineering |
| **Pandas**           | Data manipulation and preprocessing                                      |
| **Jupyter Notebook** | Interactive analysis and documentation                                   |
| **SQL**              | Business analysis and insight generation                                 |
| **PostgreSQL**       | Primary relational database used for analysis                            |
| **SQLAlchemy**       | Loading the processed DataFrame into the database                        |
| **Power BI**         | Interactive dashboard and business visualization                         |
| **PowerPoint / PDF** | Final reporting and stakeholder presentation                             |

The notebook also contains connection examples for **MySQL** and **Microsoft SQL Server**.

---

## Project Workflow

### 1. Data Loading & Exploration

The raw customer shopping dataset is loaded into Python using Pandas.

Initial exploration includes:

* Dataset dimensions and schema inspection
* Data type validation
* Missing-value analysis
* Duplicate checks
* Distribution and categorical-value inspection

### 2. Data Cleaning & Feature Engineering

The dataset is prepared for analysis by:

* Filling missing review ratings using category-level median values
* Standardizing column names to `snake_case`
* Creating an `age_group` field for demographic analysis
* Converting purchase-frequency labels into approximate numeric day intervals
* Identifying redundant promotional fields
* Removing the redundant `promo_code_used` column
* Preparing the cleaned dataset for database loading

### 3. Database Integration

The cleaned Pandas DataFrame is transferred to a relational database using **SQLAlchemy**.

PostgreSQL is used as the primary database in this implementation, with the cleaned data stored in the `customer` table for SQL analysis.

> **Security Note:** Database credentials should never be committed to a public repository. Use environment variables or local configuration files excluded through `.gitignore`.

### 4. SQL Business Analysis

SQL is used to answer ten business-oriented analytical questions involving:

* Aggregations
* Subqueries
* `CASE` expressions
* Common Table Expressions (CTEs)
* Window functions
* Ranking
* Customer segmentation
* Product-level analysis
* Revenue analysis

### 5. Power BI Dashboard

The analyzed data is visualized in Power BI to provide stakeholders with an interactive overview of customer behavior and business performance.

The dashboard focuses on areas such as:

* Customer volume
* Average purchase amount
* Average customer rating
* Revenue by customer segment
* Revenue by product category
* Subscription behavior
* Shipping-method performance
* Age-group contribution
* Product and discount trends

### 6. Business Reporting

The final stage converts analytical results into a structured report and presentation designed for business stakeholders.

---

## SQL Business Questions

The SQL analysis answers the following questions:

1. What is the total revenue generated by male and female customers?
2. Which customers used a discount but still spent above the average purchase amount?
3. Which five products have the highest average review rating?
4. How do average purchase amounts compare between Standard and Express shipping?
5. Do subscribed customers spend more than non-subscribers?
6. Which products have the highest percentage of discounted purchases?
7. How many customers belong to the New, Returning, and Loyal segments?
8. What are the top three most purchased products within each category?
9. Are repeat buyers also more likely to subscribe?
10. What is the revenue contribution of each age group?

The complete queries are available in [`customer_behavior_sql_queries.sql`](customer_behavior_sql_queries.sql).

---

## Selected Findings

Some notable findings from the dataset include:

* Total recorded purchase revenue is approximately **$233,081**.
* Average purchase amount is approximately **$59.76**.
* Average customer review rating is approximately **3.75 / 5**.
* **Express shipping** customers recorded an average purchase amount of approximately **$60.48**, compared with **$58.46** for Standard shipping.
* Subscribers recorded an average purchase amount of approximately **$59.49**, while non-subscribers averaged approximately **$59.87**.
* Customer segmentation produced approximately **3,116 Loyal**, **701 Returning**, and **83 New** customers based on previous-purchase history.
* The **Young Adult** age group generated the highest revenue among the four age segments, at approximately **$62,143**.
* **Gloves** had the highest average review rating at approximately **3.86**.
* **Hat** purchases had the highest discount usage rate at approximately **50%**.

> These results describe this dataset and should be interpreted in the context of its customer distribution and available variables.

---

## Business Recommendations

Based on the analysis, a retail business could consider the following actions:

* **Strengthen subscription benefits:** Subscribers do not show a higher average purchase value in the current data, suggesting an opportunity to improve subscriber-exclusive incentives and value propositions.
* **Develop loyalty strategies:** A large share of customers fall into the Loyal segment. Personalized rewards, early product access, and loyalty benefits could help retain these customers.
* **Review discount dependency:** Products with high discount usage should be evaluated to determine whether promotions are increasing incremental demand or unnecessarily reducing margins.
* **Promote highly rated products:** Products with consistently strong ratings can be highlighted in campaigns, bundles, and recommendation systems.
* **Use demographic segmentation:** Revenue differences across age groups can support more targeted campaigns and personalized product recommendations.
* **Optimize product-category strategy:** Category-level best sellers can guide inventory planning, merchandising, and cross-selling opportunities.

---

## Repository Structure

```text
retail-customer-intelligence-sales-analytics/
│
├── customer_shopping_behavior.csv
│   └── Raw customer shopping dataset
│
├── Customer_Shopping_Behavior_Analysis.ipynb
│   └── Python data cleaning, transformation and database loading
│
├── customer_behavior_sql_queries.sql
│   └── SQL queries for business analysis
│
├── customer_behavior_dashboard.pbix
│   └── Interactive Power BI dashboard
│
├── Customer Shopping Behavior Analysis.pdf
│   └── Final project report
│
├── Customer-Shopping-Behavior-Analysis.pptx
│   └── Stakeholder presentation
│
├── Business Problem Document.pdf
│   └── Business problem and analytical requirements
│
├── README.md
└── LICENSE
```

---

## How to Run the Project

### Prerequisites

Install or have access to:

* Python 3.x
* Jupyter Notebook or JupyterLab
* PostgreSQL and pgAdmin
* Power BI Desktop

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/retail-customer-intelligence-sales-analytics.git
cd retail-customer-intelligence-sales-analytics
```

### 2. Install Python Dependencies

```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### 3. Run the Python Notebook

Open:

```text
Customer_Shopping_Behavior_Analysis.ipynb
```

Run the notebook cells to:

* Load the CSV dataset
* Inspect and clean the data
* Engineer additional analytical features
* Connect to PostgreSQL
* Load the processed dataset into the database

Before running the database section, replace local connection settings with your own secure configuration.

### 4. Run the SQL Analysis

Create a PostgreSQL database such as:

```text
customer_behavior
```

After loading the `customer` table from the notebook, execute:

```text
customer_behavior_sql_queries.sql
```

### 5. Open the Power BI Dashboard

Open:

```text
customer_behavior_dashboard.pbix
```

If necessary, update the Power BI data-source credentials to point to your local database.

---

## Skills Demonstrated

This project demonstrates practical experience with:

* Data cleaning and preprocessing
* Missing-value treatment
* Feature engineering
* Exploratory data analysis
* Python and Pandas
* SQL querying
* CTEs and window functions
* Customer segmentation
* Database integration
* PostgreSQL
* Power BI dashboard development
* KPI design
* Business insight generation
* Data storytelling
* Stakeholder reporting

---

## Future Improvements

Potential extensions include:

* Building an automated ETL pipeline
* Adding RFM customer segmentation
* Creating customer lifetime value metrics
* Performing cohort and retention analysis
* Building predictive models for customer churn or purchase propensity
* Publishing the Power BI report through Power BI Service
* Adding automated data-quality validation
* Moving database credentials to environment variables

---

## Acknowledgement

This portfolio implementation is based on and adapted from the **Customer Behavior Data Analyst Portfolio Project** originally created by **Amlan Mohanty**.

Original project:

[amlanmohanty1/customer-trends-data-analysis-SQL-Python-PowerBI](https://github.com/amlanmohanty1/customer-trends-data-analysis-SQL-Python-PowerBI)

The project has been worked through and presented here for educational and portfolio purposes. The original MIT license and attribution are retained in accordance with the repository's license terms.

---

## License

This project is distributed under the **MIT License**.

See [`LICENSE`](LICENSE) for the original copyright and license terms.

---

## Contact

If you would like to discuss this project, data analytics, or potential opportunities, connect with me through GitHub or LinkedIn.

**GitHub:** `https://github.com/YOUR_USERNAME`
**LinkedIn:** `YOUR_LINKEDIN_URL`

---

If you found this project useful, consider giving the repository a ⭐.
