[![Code Institute](image/code_institute_logo.png)](https://codeinstitute.net/)

# Online Retail Transaction Analysis

## Project Purpose

This project demonstrates how data analytics and Python-based ETL can support **evidence-based decision-making** in an online retail business.  
By analysing transactional data from **Online Retail.csv**, the project uncovers patterns in customer behaviour, product performance, and sales trends, showing how analytics delivers real business value.

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

These hypotheses are tested and validated in the Jupyter Notebook.

---

## ETL Summary

### Extract

- Loaded the raw dataset from `data/raw/Online Retail.csv` using:  
  `pandas.read_csv(..., encoding="latin1")` to correctly handle special characters.

### Transform

The following cleaning and transformation steps were applied:

- Removed **duplicate rows**  
- Removed rows with **missing `Description` values**  
- Converted `InvoiceDate` to a proper `datetime` format  
- Removed rows where:
  - `Quantity <= 0`  
  - `UnitPrice <= 0`  
  (These typically represent cancellations, refunds, or data entry errors.)  
- Created a new feature:
  - `TotalValue = Quantity * UnitPrice`  
- Extracted time-based features:
  - `Year`, `Month`, `Day`, `Hour` from `InvoiceDate`

These steps ensure the dataset is clean, consistent, and suitable for reliable analysis.

### Load

- Saved the cleaned dataset to:  
  `data/clean/online_retail_clean.csv`

All analysis in the notebook is performed on this cleaned dataset.

---

## Analysis & Methods

The Jupyter Notebook (`Online_Retail_Analysis.ipynb`) includes:

- Initial data inspection and descriptive statistics  
- Calculation of key KPIs:
  - Total revenue  
  - Number of unique customers  
  - Number of unique products  
  - Number of countries  
- Monthly time-series aggregation of revenue  
- Product-level revenue analysis  
- Country-level revenue comparison  
- Customer segmentation using RFM (Recency, Frequency, Monetary) analysis  
- Simple baseline revenue forecasting using rolling averages  

---

## Visualisations

At least four different plot types are included, each answering a specific business question:

1. **Line Plot – Monthly Sales Trend**  
   - *Business question:* When do sales peak, and are there seasonal patterns?

2. **Bar Chart – Top 10 Products by Revenue**  
   - *Business question:* Which products generate the most revenue?

3. **Bar Chart – Top 10 Countries by Revenue**  
   - *Business question:* Which markets contribute the most to revenue?

4. **Heatmap – Correlation Analysis**  
   - *Business question:* How are Quantity, UnitPrice, and TotalValue related?

Additional visuals include:

- Boxplot of order values  
- Histograms of RFM metrics  
- Pareto curve showing cumulative revenue vs cumulative customers  

---

## Tools & Technologies

- **Programming Language:** Python  
- **Libraries Used:**
  - `pandas` – data manipulation and ETL  
  - `numpy` – numerical operations  
  - `matplotlib`, `seaborn` – data visualisation  
  - `plotly` – interactive visualisations (optional)  
- **Environment:** Jupyter Notebook  

---

## AI Integration

AI tools were used to:

- Assist with structuring the ETL pipeline  
- Suggest appropriate visualisation techniques  
- Help refine insight narratives and hypothesis explanations  
- Support the organisation and clarity of the notebook and README  

All AI-assisted outputs were reviewed, adapted, and implemented manually.

---

## Ethical & Data Handling Considerations

- Customer identifiers are anonymised numerical values; no personally identifiable information (PII) is included.  
- Invalid or misleading records (e.g. negative quantities or prices) were removed to improve analytical accuracy.  
- The dataset is used solely for educational and analytical purposes in this capstone project.

---

## Limitations

- Missing `CustomerID` values reduce full coverage in customer segmentation.  
- Refunds and cancellations were excluded rather than analysed separately.  
- The dataset represents a single time period, limiting long-term trend analysis.

These limitations mean that results should be interpreted as indicative patterns rather than precise forecasts.

---

## Future Work

Possible extensions to this project include:

- Advanced time-series forecasting (e.g. ARIMA, Prophet)  
- Machine learning-based customer clustering  
- Separate analysis of refunds and cancellations  
- Development of an interactive dashboard for stakeholders  

---

## Project Structure

```text
online_retail_project/
│
├── Online_Retail_Analysis.ipynb
│
├── data/
│   ├── raw/
│   │   └── Online Retail.csv
│   └── clean/
│       └── online_retail_clean.csv
│
└── versions/
    └── v1/
