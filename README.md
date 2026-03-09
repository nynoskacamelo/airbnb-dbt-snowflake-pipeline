# Airbnb Data Pipeline using Snowflake + dbt

## Project Overview

This project demonstrates a modern data engineering pipeline built using **Snowflake and dbt**, with raw data sourced from **AWS S3**. The pipeline follows a layered architecture to transform raw Airbnb data into a structured **analytics-ready star schema**.

The goal of this project is to simulate how a real-world data engineering team would ingest, transform, and model data for analytical reporting.

---

## Tech Stack

- Snowflake (Cloud Data Warehouse)
- dbt Core (Data Transformations)
- AWS S3 (Raw Data Storage)
- SQL
- Jinja Macros
- Git & GitHub
- VS Code

---

## Data Pipeline Architecture

The pipeline follows a **multi-layer data architecture**.


---

## Data Layers Explained

### Staging Layer
Raw data from **AWS S3** is first loaded into Snowflake staging tables.  
These tables represent the initial landing zone for ingestion.

Tables ingested:
- bookings
- listings
- hosts

---

### Bronze Layer
The Bronze layer stores the **raw structured data** copied from staging.  
Minimal transformations are applied at this stage.

Purpose:
- Preserve original data
- Maintain ingestion traceability

---

### Silver Layer
The Silver layer applies **data cleaning and transformation** logic.

Transformations include:
- Standardizing columns
- Removing duplicates
- Data type adjustments
- Preparing datasets for modeling

Tables processed:
- bookings
- listings
- hosts

---

### Gold Layer (Analytics Layer)

In the Gold layer, the data is modeled into a **star schema** for analytics.

First, an **OBT (One Big Table)** was created by combining:

- bookings
- listings
- hosts

This consolidated dataset was then transformed into an **analytical star schema**.

---

## Star Schema Design

The final model includes:

### Fact Table

**fact_bookings**

Contains numeric business metrics such as:
- booking amount
- number of nights
- service fees
- cleaning fees

---

### Dimension Tables

**dim_bookings**

Booking attributes such as:
- booking_id
- booking status
- booking date

**dim_listings**

Listing attributes such as:
- listing_id
- location
- property type

**dim_hosts**

Host information such as:
- host_id
- host name
- host details

---

## Project Goal

The objective of this project was to demonstrate:

- Modern **ELT architecture**
- Data transformation using **dbt**
- Layered data modeling
- **Star schema design for analytics**

This structure allows downstream tools such as **Power BI, Tableau, or Looker** to easily consume the data for reporting and dashboards.

---

## Future Improvements

Possible enhancements include:

- Adding dbt tests for data quality
- Creating incremental models
- Building dashboards in Power BI
- Adding CI/CD using GitHub Actions
- Implementing dbt documentation

---

## Author

**Nynoska Camelo**  
Data Engineer | SQL | Snowflake | dbt | Azure