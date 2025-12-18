
[![Code Institute](image/code_institute_logo.png)](https://codeinstitute.net/)

# Online Retail Transaction Analysis
**Data Analytics & Python for Data Preparation – Capstone Project**

---

## Project Purpose

This project demonstrates how data analytics and Python-based ETL can support **evidence-based decision-making** in an online retail business.  
By analysing transactional data from **Online Retail.csv**, the project uncovers patterns in customer behaviour, product performance, and sales trends, showing how analytics delivers real business value.

The project has been designed and implemented to meet all **Learning Outcomes (LO1–LO4)** for the Data Analytics and Python for Data Preparation capstone assessment.

---

## Business Case

An online retailer wants to improve profitability and operational efficiency by understanding:

- Which products drive the most revenue  
- What customer groups purchase the most  
- How revenue varies by country  
- When sales peak throughout the year  

Insights from this analysis support decisions in:

- Inventory management  
- Pricing and promotion strategies  
- Marketing and customer retention  
- Geographic market prioritisation  

---

## Project Objectives

1. Build a robust **ETL (Extract, Transform, Load)** pipeline using Python.
2. Clean and prepare raw transactional data for reliable analysis.
3. Perform exploratory data analysis (EDA) to uncover trends and patterns.
4. Create multiple visualisation types to answer business questions.
5. Segment customers using **RFM (Recency, Frequency, Monetary)** analysis.
6. Validate business hypotheses using evidence-based insights.
7. Demonstrate effective data management, documentation, and version control.

---

## Dataset

**Raw source file:**  
`data/raw/Online_Retail.csv`

**Columns:**

- `InvoiceNo` – Invoice number  
- `StockCode` – Product code  
- `Description` – Product description  
- `Quantity` – Quantity of product per transaction  
- `InvoiceDate` – Date and time of invoice  
- `UnitPrice` – Price per unit  
- `CustomerID` – Anonymised customer identifier  
- `Country` – Country of the customer  

The dataset contains several hundred thousand transactions across multiple months and contains no personally identifiable information (PII).

---

## Hypotheses

1. **H1:** A small number of products generate the majority of revenue.  
2. **H2:** Approximately 20% of customers contribute around 80% of total revenue (Pareto principle).  
3. **H3:** Sales show clear monthly or seasonal patterns.  
4. **H4:** Revenue varies significantly between countries.

All hypotheses are tested and validated in the Jupyter Notebook.

---

## ETL Summary

### Extract

- Loaded the raw dataset from `data/raw/Online_Retail.csv` using:  
  `pandas.read_csv(..., encoding="latin1")` to correctly handle special characters.

### Transform

The following cleaning and transformation steps were applied:

- Removed duplicate rows  
- Removed rows with missing `Description` values  
- Converted `InvoiceDate` to datetime format  
- Removed invalid transactions:
  - `Quantity <= 0`  
  - `UnitPrice <= 0`  
- Created a new feature:
  - `TotalValue = Quantity * UnitPrice`  
- Extracted time-based features:
  - `Year`, `Month`, `Day`, `Hour`  

These steps ensure the dataset is clean, consistent, and suitable for reliable analysis.

### Load

- Saved the cleaned dataset to:  
  `data/clean/online_retail_clean.csv`

All analysis is performed on this cleaned dataset.

---

## Analysis & Methods

The Jupyter Notebook (`Online_Retail_Analysis.ipynb`) includes:

- Data inspection and descriptive statistics  
- Key business KPIs:
  - Total revenue  
  - Unique customers  
  - Unique products  
  - Countries represented  
- Monthly revenue time-series analysis  
- Product and country performance analysis  
- Customer segmentation using RFM analysis  
- Baseline revenue forecasting using rolling averages  

---

## Visualisations Summary (Executive Perspective)

Each visualisation directly answers a business question:

1. **Monthly Revenue Trend (Line Plot)**  
   Identifies seasonal patterns and revenue volatility to support forecasting and planning.

2. **Top 10 Products by Revenue (Bar Chart)**  
   Highlights key revenue drivers for inventory and marketing prioritisation.

3. **Top 10 Countries by Revenue (Bar Chart)**  
   Reveals geographic performance differences to guide international strategy.

4. **Correlation Heatmap**  
   Explores relationships between quantity, price, and revenue to support pricing decisions.

5. **Order Value Distribution (Boxplot)**  
   Highlights variability and outliers in transaction values.

6. **Pareto Curve & RFM Distributions**  
   Confirms customer value concentration and supports targeted retention strategies.

---

## Tools & Technologies

### Main Data Analysis Libraries

- **pandas** – Data loading, cleaning, transformation  
  *Example:* `df = pd.read_csv('data/raw/Online_Retail.csv')`

- **numpy** – Numerical operations  
  *Example:* `np.isclose(df['TotalValue'], df['Quantity'] * df['UnitPrice'])`

- **matplotlib** – Line charts, bar charts, histograms  
  *Example:* `plt.plot(monthly_sales.index, monthly_sales.values)`

- **seaborn** – Statistical visualisations  
  *Example:* `sns.boxplot(x=df['TotalValue'])`


---

## AI Integration

AI tools were responsibly integrated to:

- Assist with ETL pipeline structuring
- Suggest analytical techniques such as RFM segmentation
- Refine visualisation choices and insight narratives

All AI-assisted outputs were reviewed and implemented manually to ensure originality.

---

## Ethical & Data Handling Considerations

- Customer identifiers are anonymised.
- Invalid or misleading records were removed to improve accuracy.
- The dataset is used solely for educational and analytical purposes.

---

## Limitations

- Missing `CustomerID` values reduce segmentation coverage.
- Refunds and cancellations were excluded rather than analysed separately.
- Single-period data limits long-term forecasting accuracy.

Results should be interpreted as indicative patterns rather than precise predictions.

---

## Future Work

Potential enhancements include:

- Advanced forecasting models (ARIMA, Prophet)
- Machine learning-based customer clustering
- Separate refund and cancellation analysis
- Interactive dashboard development

---

## Project Structure

```text
online_retail_project/
│
│
├── data/
│   ├── raw/
│   │   └── Online_Retail.csv
│   └── clean/
│       └── online_retail_clean.csv
│
├── image/
│
├── versions/
│    └── v1/
│
├── .gitignore/
│
│
├── Online_Retail_Analysis.ipynb
├── README.md
└── requirements.txt
```

---

## Credits

- Code Institute LMS  
- GitHub Copilot  
- ChatGPT (OpenAI)

---

## Acknowledgements

Special thanks to:
- **Vasi** for guidance on project structure and execution
- **Can and Mo** for delivering valuable masterclasses
- **CI Team** for the help and support 