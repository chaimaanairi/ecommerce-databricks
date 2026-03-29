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
