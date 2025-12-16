# Online Retail Transaction Analysis

## Overview
This project analyses real transactional data from an online retailer using **Online Retail.csv**.  
The dataset contains hundreds of thousands of purchase transactions, including product information, pricing, customer IDs and timestamps.

The goal of the project is to demonstrate a complete data analytics workflow:
- ETL (Extract, Transform, Load)
- Exploratory Data Analysis (EDA)
- Visualisation and storytelling
- Customer segmentation (RFM)
- Hypothesis validation

This work is part of a Data Analytics & Python for Data Preparation capstone project.

---

## Business Case
An online retailer wants to improve profitability by understanding:

- Which products drive the most revenue  
- What customer groups purchase the most  
- How revenue varies by country  
- When sales peak throughout the year  

Insights from this analysis support decisions in:

- Inventory management  
- Pricing  
- Marketing and promotions  
- Customer retention strategies  

---

## Dataset

**Raw source file:**  
`data/raw/Online Retail.csv`

**Columns:**
- `InvoiceNo` – Invoice number  
- `StockCode` – Product code  
- `Description` – Product description  
- `Quantity` – Quantity of product per transaction  
- `InvoiceDate` – Date and time of invoice  
- `UnitPrice` – Price per unit  
- `CustomerID` – Customer identifier  
- `Country` – Country of the customer  

The dataset contains multiple months of transactions from an online retailer, with hundreds of thousands of rows.

---

## Hypotheses

1. **H1:** A small number of products generate the majority of revenue.  
2. **H2:** Approximately 20% of customers contribute around 80% of total revenue (Pareto principle).  
3. **H3:** Sales show clear monthly or seasonal patterns.  
4. **H4:** Revenue varies significantly between countries.

These hypotheses are tested and discussed in the notebook.

---

## ETL Summary

### Extract
- Loaded the raw dataset from `data/raw/Online Retail.csv` using:
  - `pandas.read_csv(..., encoding="latin1")` to handle special characters.

### Transform
Cleaning and transformation steps:

- Removed **duplicate rows**.  
- Removed rows with **missing `Description`**.  
- Converted `InvoiceDate` to a proper `datetime` type.  
- Removed rows where:
  - `Quantity <= 0`  
  - `UnitPrice <= 0`  
  (These typically represent cancellations, refunds, or data entry errors.)  
- Created a new feature:
  - `TotalValue = Quantity * UnitPrice`  
- Extracted additional time-based features:
  - `Year`, `Month`, `Day`, `Hour` from `InvoiceDate`

These steps ensure that only valid, positive, and interpretable transaction records are used for analysis.

### Load

- Saved the cleaned dataset to:  
  `data/clean/online_retail_clean.csv`

All subsequent analysis in the notebook is performed on this cleaned file.

---

## Analysis & Methods

The Jupyter Notebook (`Online_Retail_Analysis.ipynb`) includes:

- Initial data inspection and descriptive statistics  
- Calculation of key KPIs:
  - Total revenue  
  - Number of unique customers  
  - Number of unique products  
  - Number of countries  
- Time series aggregation of revenue by month  
- Product-level aggregation of revenue  
- Country-level aggregation of revenue  
- RFM (Recency, Frequency, Monetary) analysis at customer level  
- Simple baseline revenue forecasting using rolling averages  

---

## Visualisations

At least four different plot types are included, each answering a specific business question:

1. **Line plot – Monthly Sales Trend**  
   - *Question:* When do sales peak, and are there seasonal patterns?

2. **Bar chart – Top 10 Products by Revenue**  
   - *Question:* Which products generate the most revenue?

3. **Bar chart – Top 10 Countries by Revenue**  
   - *Question:* Which markets contribute the most to revenue?

4. **Heatmap – Correlation between Quantity, UnitPrice, and TotalValue**  
   - *Question:* How are key numeric variables related?

Additional visuals include:
- Boxplot of order values  
- Histograms of RFM metrics  
- Pareto curve showing cumulative revenue vs cumulative customers  

---

## Tools & Technologies

- **Programming Language:** Python  
- **Libraries:**
  - `pandas` – data manipulation and ETL  
  - `numpy` – numerical operations  
  - `matplotlib`, `seaborn` – static visualisations  
  - `plotly` – optional interactive visualisations  
- **Environment:** Jupyter Notebook  

---

## Project Structure

```text
online_retail_project/
│
├── Online_Retail_Analysis.ipynb
│
└── data/
    ├── raw/
    │   └── Online Retail.csv
    └── clean/
        └── online_retail_clean.csv
