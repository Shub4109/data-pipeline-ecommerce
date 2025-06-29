# 📦 data-pipeline-ecommerce

> **Author:** Shubham Nagula (shubham07nagula.com)  
> **Repo:** [data-pipeline-ecommerce](https://github.com/Shub4109/data-pipeline-ecommerce)  
> **Stack:** Python, Airflow, MySQL, Docker, Metabase, Pandas

---

## 🌐 Project Overview

This repository builds an **end-to-end data engineering pipeline** for the **Brazilian E-Commerce Public Dataset (Olist)**. The pipeline processes raw CSV data and loads it into a MySQL database for further analysis and visualization via Metabase and Airflow.

---

## ✅ Environment Setup

### Hardware & OS

- OS: Windows 11
- RAM: ≥ 16GB recommended
- Disk: ≥ 5GB free
- CPU: multi-core (recommended for Docker)

---

### Core Tools

| Tool | Version |
|------|---------|
| Python | 3.12 |
| MySQL | 8.0 |
| Docker Desktop | Latest |
| Airflow | 2.9.1 |
| Metabase | Latest |
| Git | 2.49.0.windows.1 |
| PyCharm | Community Edition |

---

### Python Virtual Environment

\\\powershell
# Create venv
python -m venv venv

# Activate venv
.\venv\Scripts\activate
\\\

---

### Python Packages

Install core libraries:

\\\powershell
pip install pymysql pandas mysql-connector-python
\\\

---

## 🚀 Data Pipeline Overview

The pipeline loads the following Olist datasets:

| Table | Status |
|-------|--------|
| olist_orders | ✅ Loaded |
| olist_order_items | ✅ Loaded |
| olist_order_payments | ✅ Loaded |
| olist_order_reviews | ✅ Loaded (duplicate handling required) |
| olist_products | ✅ Loaded |
| olist_sellers | ✅ Loaded |
| product_category_translation | ⏳ Pending re-run after table creation |
| olist_geolocation | ⏳ Pending |

---

## 🗂️ Folder Structure

\\\
data-pipeline-ecommerce/
├── dags/
├── data_sample/
│   └── olist/
├── notebooks/
├── scripts/
│   └── load_data/
│       ├── mysql_connect_test.py
│       ├── load_olist_orders.py
│       ├── load_olist_order_items.py
│       ├── load_olist_order_payments.py
│       ├── load_olist_order_reviews.py
│       ├── load_olist_products.py
│       ├── load_olist_sellers.py
│       └── load_product_category_translation.py
├── sql/
├── venv/
├── docker-compose.yml
└── README.md
\\\

---

## 🐳 Docker Services

### Airflow

Pulled & configured with:

\\\
docker pull apache/airflow:2.9.1
\\\

Running on:

\\\
http://localhost:8080
\\\

Default credentials:

- Username: airflow
- Password: airflow

---

### Metabase

Pulled via:

\\\
docker pull metabase/metabase
\\\

Running on:

\\\
http://localhost:3000
\\\

---

## 🗄️ MySQL Database

### Database Setup

\\\sql
CREATE DATABASE ecom_db;
USE ecom_db;
\\\

All tables were created via SQL DDL scripts matching the Olist schema.

---

## 📝 Loading Data into MySQL

Each table has a dedicated Python ETL script under:

\\\
scripts/load_data/
\\\

Run any loader like so:

\\\powershell
python scripts/load_data/load_olist_orders.py
\\\

---

## ⚠️ Known Issues & Next Steps

✅ Duplicate handling required in **olist_order_reviews**.  
✅ Finish loading:
- \product_category_translation\
- \olist_geolocation\

✅ Next pipeline steps:
- Create Airflow DAGs for automated loading
- Connect Metabase to MySQL for analytics dashboards

---

## 📊 Data Sources

- [Brazilian E-Commerce Public Dataset (Olist) on Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🤝 Contributing

Pull requests welcome!

---

# 🎯 Final Note

This pipeline will serve as the foundation for advanced ETL workflows, data quality checks, and analytics in the Brazilian e-commerce domain.

**Stay tuned for Airflow orchestration and Metabase dashboards!**
