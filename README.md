# 🚀 End-to-End ETL Data Pipeline in Databricks

A complete Data Engineering project built using **Databricks** and **PySpark**, implementing the **Medallion Architecture** (Bronze → Silver → Gold) to process and analyze customer, orders, and products data.

---

## 📌 Project Overview

This project demonstrates a full ETL (Extract, Transform, Load) pipeline that:
- Ingests raw CSV and JSON data files
- Cleans and transforms the data
- Produces business-ready analytics tables
- Runs automatically on a daily schedule

---

## 🏗️ Architecture

```
Raw Files (CSV + JSON)
        │
        ▼
┌─────────────────┐
│   BRONZE LAYER  │  ← Raw data ingestion (combined CSV + JSON)
│                 │
│ bronze_customers│
│ bronze_orders   │
│ bronze_products │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   SILVER LAYER  │  ← Cleaned & standardized data
│                 │
│ silver_customers│
│ silver_orders   │
│ silver_products │
└────────┬────────┘
         │
         ▼
┌──────────────────────┐
│      GOLD LAYER      │  ← Business-ready analytics
│                      │
│ gold_customer_summary│  ← Customer rankings & total spend
└──────────────────────┘
```

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Databricks** | Cloud data platform |
| **Apache Spark (PySpark)** | Distributed data processing |
| **Delta Lake** | Storage format for all layers |
| **Python** | Programming language |
| **SQL** | Querying Gold layer tables |
| **Databricks Workflows** | Pipeline automation & scheduling |

---

## 📁 Project Structure

```
databricks-etl-pipeline/
│
├── data/
│   ├── customerscsv.csv
│   ├── customersjson.json
│   ├── orderscsv.csv
│   ├── ordersjson.json
│   ├── productscsv.csv
│   └── productsjson.json
│
├── notebook.ipynb        ← Main ETL pipeline notebook
└── README.md
```

---

## 📊 Dataset

| Dataset | Format | Rows | Description |
|---|---|---|---|
| Customers | CSV + JSON | 5 each | Customer details (name, country, signup date) |
| Orders | CSV + JSON | 5 each | Order details (order ID, amount, date) |
| Products | CSV + JSON | 4 each | Product details (name, category, price) |

---

## ⚙️ Pipeline Steps

### 🥉 Bronze Layer — Raw Ingestion
- Read CSV and JSON files as Spark DataFrames
- Combine CSV and JSON using `unionByName`
- Add `ingested_at` timestamp column
- Save as Delta tables

### 🥈 Silver Layer — Data Cleaning
- Remove duplicate records using `dropDuplicates`
- Remove null values using `dropna`
- Standardize text fields using `trim` and `upper`
- Save cleaned data as Delta tables

### 🥇 Gold Layer — Business Analytics
- Join customers, orders, and products tables
- Aggregate total orders and total spend per customer
- Rank customers by total spend
- Save final summary as Delta table

### ✅ Data Quality Checks
- Null value checks on all critical columns
- Duplicate checks on all primary keys
- Row count validation across all layers

---

## 📈 Final Output — Customer Summary

| Rank | Customer | Total Orders | Total Spent |
|---|---|---|---|
| 1 | Alice Morgan | 2 | $330 |
| 2 | Emma Patel | 1 | $180 |
| 3 | Carla Zhao | 1 | $90 |
| 4 | Ben Singh | 1 | $45 |

---

## 🔄 Automated Workflow

The pipeline is scheduled to run automatically every day at **9:00 AM IST** using **Databricks Workflows**, ensuring data is always fresh and up to date.

---

## 🚀 How to Run This Project

1. Sign up for a free Databricks account at [databricks.com](https://www.databricks.com)
2. Upload the data files from the `/data` folder to Databricks using **Data Ingestion → Create or modify table**
3. Import the `notebook.ipynb` file into your Databricks Workspace
4. Connect the notebook to a Serverless compute
5. Run all cells using **Run All**
6. Optionally schedule it using **Jobs & Pipelines → Create job**

---

## 💡 Key Concepts Learned

- **Medallion Architecture** — organizing data into Bronze, Silver, Gold layers
- **Delta Lake** — ACID-compliant storage with time travel support
- **PySpark DataFrames** — distributed data processing at scale
- **Data Quality** — null checks, duplicate removal, schema validation
- **Pipeline Automation** — scheduling jobs with Databricks Workflows

---

## 👤 Author

**Fathima Hashim**
- 📧 fathimahashimplr2019@gmail.com

---

## 📚 Reference

- Video Tutorial: [Full End-to-End Data Engineering Project in Databricks](https://youtu.be/SSz7HiyQN1M)
- Data Source: [Alex The Analyst — DatabricksSeries GitHub](https://github.com/AlexTheAnalyst/DatabricksSeries)

---

⭐ If you found this project helpful, please give it a star on GitHub!
