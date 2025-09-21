# 🔄 Data Transformation Pipeline

## 📌 Overview

This project handles the **transformation layer** of the BI/Data Engineering solution. It uses **dbt Core**, containerized with Docker, and orchestrates execution via **Azure Container Apps Jobs** and **Azure Data Factory**.

## 🏗️ Architecture

**Flow:**
Databricks SQL Warehouse ⇆ dbt Core (Docker) ➝ Azure Container Registry ➝ Azure Container Apps Job ➝ Orchestrated by Prod ADF ➝ Databricks SQL
Warehouse ➝ Power BI

- **dbt Core**: Defines and runs SQL-based transformations.
- **Docker**: Local development and reproducibility.
- **Azure Container Registry (ACR)**: Stores dbt Docker images.
- **Azure Container Apps Jobs**: Runs containerized dbt transformations.
- **Azure Data Factory (ADF)**: Orchestrates job execution (POST + GET APIs).
- **Databricks SQL Warehouse (Unity Catalog)**: Transformation target.
- **Power BI**: Consumes curated datasets for reporting.

## 🔐 Dev/Prod Setup & Security

- **Docker-based local dev** environment for dbt Core
- **GitHub Actions** for CI/CD to build & push dbt images into ACR
- **Azure Key Vault** for secret storage.
- **Managed Identity** for ACA ↔ ADF ↔ Databricks authentication.
- **Log Analytics** integrated with ACA for monitoring job runs.

## ⚙️ CI/CD (GitHub Actions)

- On code push, GitHub Actions build dbt Docker images.
- Images pushed to **Azure Container Registry (ACR)**.
- Deployed to **Azure Container Apps Jobs**.

## 📊 Monitoring

- **Log Analytics** workspace configured to track ACA job runs.
- Orchestration retries managed in ADF Until loop.

## 👤 Author

*Tunde Morakinyo*
