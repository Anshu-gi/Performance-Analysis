# 📊 E-Commerce Sales Performance & Customer Analysis Dashboard

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> An end-to-end data analytics and business intelligence solution analyzing transactional retail data. Features rigorous data cleaning and feature engineering in Python/Pandas, exploratory data analysis, and an executive-level interactive Power BI performance dashboard.

---

## 📑 Table of Contents
- [Project Overview](#-project-overview)
- [Executive Dashboard Preview](#-executive-dashboard-preview)
- [Key Performance Indicators (KPIs)](#-key-performance-indicators-kpis)
- [Core Business Insights](#-core-business-insights)
- [Data Pipeline & Engineering](#-data-pipeline--engineering)
- [Dataset Architecture](#-dataset-architecture)
- [Interactive Dashboard Features](#-interactive-dashboard-features)
- [Actionable Business Recommendations](#-actionable-business-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Reproduce](#-how-to-reproduce)
- [Tech Stack](#-tech-stack)
- [License](#-license)

---

## 📌 Project Overview

In competitive e-commerce and wholesale retail markets, understanding revenue seasonality, international market penetration, customer lifetime value, and inventory demand is vital for sustainable growth. 

This project processes raw transactional data spanning over **541,000+ purchase records**, addresses data hygiene challenges (missing customer identifiers, cancelled orders, zero-priced anomalies), performs feature engineering, and delivers an interactive **Performance Analysis Dashboard** tailored for executive decision-makers.

### 🎯 Key Objectives:
1. **Cleanse & Standardize Data:** Isolate verified transactions by filtering out cancelled orders, returns, and missing customer identities.
2. **Feature Engineering:** Derive calculated metrics such as line-item `TotalSales` and temporal cohorts (`MonthYear`).
3. **Trend & Geographic Analysis:** Uncover seasonal sales velocity and assess domestic (UK) vs. international revenue contributions.
4. **Pareto & VIP Segmentation:** Identify top-performing SKUs and high-net-worth customer segments driving bulk revenue.
5. **Interactive Business Intelligence:** Build a dynamic reporting dashboard with cross-filtering capabilities by month, geography, and SKU catalog.

---

## 🖥️ Executive Dashboard Preview

![Performance Analysis Dashboard](assets/dashboard.png)

*The dashboard provides real-time cross-filtering across three slicers: **Month**, **Country**, and **Products**, giving leadership instant visibility into micro and macro performance drivers.*

---

## 📈 Key Performance Indicators (KPIs)

| Metric | Value | Description |
| :--- | :---: | :--- |
| **Total Net Sales** | **$8.91M** | Cumulative gross merchandise revenue across all verified transactions |
| **Total Units / Volume** | **5.00M** | Total quantity of product units sold and fulfilled |
| **Average Order Value (AOV)** | **$1.72** | Mean item price point per order line item across catalog transactions |
| **Total Clean Transactions** | **397,884** | Final cleansed record count after pruning returns, anomalies, and null IDs |

---

## 🔍 Core Business Insights

### 1. 🗓️ Pronounced Q4 Holiday Seasonality
- **Steady Baseline (Jan – Aug):** Monthly sales maintained consistent performance ranging between **$450K and $680K**.
- **Q4 Surge (Sep – Nov):** Demand rapidly accelerated in late Q3, scaling from **$952.8K** in September to **$1.04M** in October, peaking in November at **$1.16M** (driven by Black Friday, Cyber Week, and holiday stock replenishment).
- **December Deceleration:** December reflects partial month data up to cutoff (**$518.2K**), consistent with mid-month shipping cutoffs for holiday delivery.

### 2. 🌍 Geographic Dominance & Export Potential
- **Domestic Engine (United Kingdom):** The UK accounts for the overwhelming majority of total business volume, generating **$7.31M+** (~82% of aggregate net revenue).
- **Top International Markets:**
  - **Netherlands:** $285.4K
  - **EIRE (Ireland):** $265.5K
  - **Germany:** $228.9K
  - **France:** $209.0K
  - **Australia:** $138.5K
- *Takeaway:* Western Europe represents the most viable expansion corridor for localized fulfillment hubs.

### 3. 🏆 Best-Selling Products (Pareto Distribution)
Top revenue-generating catalog items identified:
1. **PAPER CRAFT , LITTLE BIRDIE:** `$168,469.60`
2. **REGENCY CAKESTAND 3 TIER:** `$142,592.95`
3. **WHITE HANGING HEART T-LIGHT HOLDER:** `$100,448.15`
4. **JUMBO BAG RED RETROSPOT:** `$85,220.78`
5. **MEDIUM CERAMIC TOP STORAGE JAR:** `$81,416.73`

### 4. 👥 Customer Segmentation & VIP Wholesale Accounts
The customer base features high-volume wholesale/B2B clients contributing outsized portions of total revenue:
- **Customer #14646:** `$197,000` (Top Account)
- **Customer #16446:** `$81,000`
- **Customer #14911:** `$80,000`
- **Customer #12415:** `$77,000`
- **Customer #12346:** `$74,000`
- *Takeaway:* The top 5 customers alone represent nearly **$509,000+** in sales. Personalized account management and bespoke wholesale discounting are paramount to retain these accounts.

---

## ⚙️ Data Pipeline & Engineering

The Python workflow (`notebooks/ecommerce_analysis.ipynb`) transforms uncleaned raw data into a structured business-ready dataset:

```mermaid
flowchart LR
    A["Raw Data (online_retail.csv)<br/>541,909 rows"] --> B["Data Cleaning<br/>Drop null CustomerID<br/>(-135k rows)"]
    B --> C["Filter Anomalies<br/>Quantity > 0 & UnitPrice > 0<br/>(Exclude returns/voids)"]
    C --> D["Feature Engineering<br/>• TotalSales = Qty * Price<br/>• MonthYear Period"]
    D --> E["Clean Dataset<br/>397,884 verified rows"]
    E --> F["Data Export<br/>Ecommerce_finance_data.csv"]
    F --> G["Power BI Dashboard<br/>DAX Metrics & Visuals"]
```

### Python Data Cleansing Snippet:
```python
import pandas as pd

# 1. Load transactional raw records
df = pd.read_csv("online_retail.csv")

# 2. Filter out non-registered guest checkout / null customer records
df = df.dropna(subset=["CustomerID"])

# 3. Filter out cancellations, returns, credit adjustments, and zero prices
df = df[(df["Quantity"] > 0) & (df["UnitPrice"] > 0)]

# 4. Feature engineering: Total line sales and monthly timestamp
df["TotalSales"] = df["Quantity"] * df["UnitPrice"]
df["InvoiceDate"] = pd.to_datetime(df["InvoiceDate"])
df["MonthYear"] = df["InvoiceDate"].dt.to_period("M")

# 5. Export cleansed dataset for BI consumption
df.to_csv("Ecommerce_finance_data.csv", index=False)
```

---

## 🗄️ Dataset Architecture

### Schema Breakdown:
| Column Name | Data Type | Cleansing Treatment / Description |
| :--- | :--- | :--- |
| `InvoiceNo` | `object` / `string` | 6-digit transaction ID. Negative transactions ('C') filtered out. |
| `StockCode` | `object` / `string` | Unique product code identifier. |
| `Description` | `object` / `string` | Catalog product name. |
| `Quantity` | `integer` | Count of units ordered per line item (strictly `> 0`). |
| `InvoiceDate` | `datetime64[ns]` | Date and time when the order was completed. |
| `UnitPrice` | `float64` | Unit retail price in currency units (strictly `> 0`). |
| `CustomerID` | `float64` | Unique registered customer identifier (non-null). |
| `Country` | `object` / `string` | Customer billing/shipping country. |
| `TotalSales` *(Engineered)* | `float64` | Calculated line revenue (`Quantity * UnitPrice`). |
| `MonthYear` *(Engineered)* | `period[M]` | Year-Month extraction for temporal and cohort tracking. |

---

## 📊 Interactive Dashboard Features

The dashboard is structured into five distinct analytical zones:

1. **KPI Header Cards:**
   - Instant executive snapshot displaying **Total Sales ($8.91M)**, **Total Orders/Units (5M)**, and **AOV ($1.72)**.
2. **Top Products Bar Chart:**
   - Highlights top 5 revenue-driving SKUs, providing merchandising teams with clear restock priorities.
3. **Monthly Sales Trajectory (Line Chart):**
   - Displays 12-month cyclical velocity with spline interpolation to highlight seasonal peaks and dips.
4. **Top Performing Countries (Horizontal Bar Chart):**
   - Ranks the top 10 international markets, highlighting regional growth potential outside the UK.
5. **Customer Segmentation Donut Chart:**
   - Details revenue breakdown across the top high-net-worth VIP accounts.
6. **Global Interactive Slicers:**
   - Multi-select dropdown filters for `Month`, `Country`, and `Products` allowing dynamic drill-downs.

---

## 💡 Actionable Business Recommendations

1. **Procurement & Inventory Ramp-Up for Q3/Q4:**
   - Align supply chain orders with suppliers by July/August to prevent stockouts of hero products (`Paper Craft`, `Regency Cakestand`) ahead of the September–November holiday rush.
2. **Dedicated B2B Account Management:**
   - Establish dedicated Key Account Managers for the top 5 clients (e.g., ID `14646` who accounts for $197K) with volume tier pricing, early access to new lines, and scheduled bulk reorders.
3. **International Expansion Strategy:**
   - Netherlands ($285K), Ireland ($265K), and Germany ($228K) show proven organic traction. Localizing currency checkout, optimizing shipping rates, and partnering with regional 3PL providers could accelerate European revenues by 20–30%.
4. **Cross-Selling & Basket Optimization:**
   - Leverage top-performing kitchen and giftware SKUs to create bundled gift sets during spring/wedding seasons to increase the Average Order Value (AOV).

---

## 📁 Repository Structure

```text
ecommerce-sales-analysis/
│
├── assets/
│   └── dashboard.png               # High-resolution dashboard screenshot
│
├── data/
│   ├── online_retail.csv           # Raw transactional dataset (541k+ rows)
│   └── Ecommerce_finance_data.csv  # Cleansed, transformed output dataset
│
├── notebooks/
│   └── ecommerce_analysis.ipynb    # Python notebook with data cleaning & EDA
│
├── .gitignore                      # Git ignore file for temp & virtual environment files
├── requirements.txt                # Python environment dependencies
└── README.md                       # Comprehensive project documentation
```

---

## 🚀 How to Reproduce

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/ecommerce-sales-analysis.git
cd ecommerce-sales-analysis
```

### 2. Set Up Python Environment
```bash
# Create a virtual environment (optional but recommended)
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install required dependencies
pip install -r requirements.txt
```

### 3. Run the Data Pipeline
Open and execute the Jupyter notebook:
```bash
jupyter notebook notebooks/ecommerce_analysis.ipynb
```
The notebook will process the raw data and produce `Ecommerce_finance_data.csv`.

### 4. Open in Power BI
1. Launch **Power BI Desktop**.
2. Connect to `Ecommerce_finance_data.csv`.
3. Load the provided report visuals or explore custom DAX measures.

---

## 🛠️ Tech Stack

- **Data Processing:** Python 3.9+, [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/)
- **Analysis Environment:** [Jupyter Notebook](https://jupyter.org/)
- **Business Intelligence & Visualization:** Microsoft Power BI / DAX
- **Version Control:** Git & GitHub

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) - feel free to use, modify, and distribute for portfolio and educational purposes.
