# 🏗️ Enterprise Analytics Engineering with dbt & BigQuery

**Tech Stack:** dbt Core, Google BigQuery, SQL  
**Architecture:** Medallion Architecture (Bronze, Silver, Gold)

## 📌 Executive Summary
This project demonstrates an enterprise-grade data transformation pipeline built with **dbt (data build tool)** and **Google BigQuery**. It implements a scalable Medallion Architecture to process raw ingested data into analytics-ready models for downstream business intelligence and executive reporting.

## 📐 Medallion Architecture

The data models are structured across three distinct layers, ensuring data quality, lineage, and modularity:

1. **🥉 Bronze (Raw / Staging):**
   - Source data is ingested directly into BigQuery.
   - Initial dbt models perform light transformations, such as standardizing column names, casting data types, and implementing basic deduplication.

2. **🥈 Silver (Integration / Cleansed):**
   - Data from various staging models is joined and enriched.
   - Business logic is applied to create cohesive, conformed dimensions and factual event streams.
   - Data quality tests (null checks, uniqueness, accepted values) are enforced here.

3. **🥇 Gold (Business / Aggregation):**
   - Final layer designed specifically for BI consumption.
   - Highly aggregated models, materialized as tables or incremental models to ensure low-latency query performance for executive dashboards.

## 🛠️ Key dbt Features Utilized
- **Materializations:** Strategic use of `view`, `table`, and `incremental` materializations to optimize BigQuery compute costs and query performance.
- **Testing:** Automated data quality testing using built-in dbt tests (`unique`, `not_null`, `relationships`) to guarantee data integrity.
- **Documentation:** Auto-generated data lineage graphs and column-level documentation.
- **Macros:** Reusable SQL snippets for standardized transformations across the pipeline.

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- dbt-bigquery (`pip install dbt-bigquery`)
- A Google Cloud Platform (GCP) project with BigQuery enabled.
- A `profiles.yml` configured with your GCP credentials.

### Execution
1. Install dependencies:
   ```bash
   dbt deps
   ```
2. Run data quality tests on sources:
   ```bash
   dbt test --select source:*
   ```
3. Execute the transformation pipeline:
   ```bash
   dbt run
   ```
4. Generate and serve documentation:
   ```bash
   dbt docs generate
   dbt docs serve
   ```
