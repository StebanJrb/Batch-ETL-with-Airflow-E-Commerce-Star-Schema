# Batch ETL with Airflow — E-Commerce Star Schema

## Overview
A classic batch ETL pipeline that processes daily e-commerce data (orders, products, customers) into a star schema data warehouse. Demonstrates production Airflow patterns including TaskGroups, XComs, SLAs, and failure recovery.

## Architecture
- **Extract**: File-based ingestion from CSV/JSON landing zone (simulating daily data drops)
- **Transform**: Dimensional modeling — fact_orders (quantity, revenue, discount), dim_customers, dim_products, dim_dates, dim_stores
- **Load**: Incremental loads with SCD Type 2 for slowly changing dimensions
- **Orchestration**: Airflow DAG with TaskGroups per stage, XComs for row count validation, SLA monitoring
- **Infrastructure**: Docker Compose (Airflow + PostgreSQL/DuckDB), MinIO for file landing zone

## Tech Stack
- Python 3.11+, Pandas
- PostgreSQL 15 or DuckDB (warehouse)
- Apache Airflow 2.x (TaskGroups, XComs, SLAs)
- Docker & Docker Compose
- AWS S3 / MinIO

## What This Demonstrates
- Star schema dimensional modeling
- SCD Type 2 implementation for historical tracking
- Airflow advanced patterns (TaskGroups, XComs, branching, SLAs)
- Incremental vs full load strategies
- File-based ingestion with landing zone pattern

## Status
🚧 In Development

## Project Structure
├── dags/
│   └── ecommerce_etl_dag.py
├── src/
│   ├── extract/
│   ├── transform/
│   │   ├── dimensions/
│   │   └── facts/
│   └── load/
├── sql/
│   └── ddl/
├── tests/
├── docker-compose.yml
└── README.md
