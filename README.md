# E-commerce Databricks Project

This project demonstrates an end-to-end data pipeline for e-commerce analytics using Databricks. 
It implements the **Bronze → Silver → Gold architecture** with Delta Lake and PySpark, 
processing raw orders, customer, and product data into clean, analytics-ready tables.

Key features:
- Bronze layer: raw ingestion from CSV / Delta tables
- Silver layer: data cleaning, deduplication, enrichment
- Gold layer: aggregated business metrics (total revenue, top customers, daily sales)
- Automated workflow with Databricks Jobs
- Data lineage tracking and conceptual governance
- Visualizations for business insights

# E-commerce Databricks Project

**End-to-end e-commerce data pipeline using Databricks, Delta Lake, and PySpark**

## Project Overview

This project demonstrates a **full end-to-end data pipeline** for e-commerce analytics.  
It implements the **Medallion Architecture** (Bronze → Silver → Gold) using Databricks, enabling the ingestion, cleaning, transformation, and analysis of raw e-commerce data.

The pipeline processes:

- **Orders data**: transactional information for each purchase
- **Customer data**: details about the buyers
- **Product data**: catalog information


## Architecture
```mermaid
flowchart TD
    A["Orders / Customers / Products CSV"] --> B["01_Bronze_Ingestion Notebook"]
    B --> C["Bronze Layer - Raw Delta Tables (default.orders, default.customers, default.products)"]
    C --> D["02_Silver_Transformation Notebook"]
    D --> E["Silver Layer - Cleaned & Enriched Delta Table (default.orders_silver)"]
    E --> F["03_Gold_Analytics Notebook"]
    F --> G["Gold Layer - Aggregated Analytics Table (default.sales_gold)"]

    subgraph ORCH["Databricks Workflows / Jobs"]
        B
        D
        F
    end

    subgraph GC["Unity Catalog / Delta Lake"]
        C
        E
        G
    end
```

- **Bronze Layer**: Stores raw data exactly as ingested. Ensures traceability and allows reprocessing.  
- **Silver Layer**: Cleans and enriches the data: removes duplicates, fills nulls, standardizes timestamps, and joins with customers/products.  
- **Gold Layer**: Aggregated tables for business insights like total revenue per product, revenue per day, and top customers.



