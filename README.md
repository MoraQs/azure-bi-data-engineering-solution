# End-to-End Data Platform Solution

This repository contains an end-to-end data solution that demonstrates
both **data ingestion** and **data transformation** workflows using Azure services and dbt Core. It is divided into two main projects with supporting documentation.

## 📂 Repository Structure

    01-ingestion-adf/        # Azure Data Factory pipelines for ingestion
    02-transformation-dbt/   # dbt Core transformations containerized with Docker
    03-docs/                 # Additional documentation and architecture diagrams

## 🚀 Solution Overview

- **Source System:** Microsoft Fabric SQL Database
- **Ingestion Layer:** Azure Data Factory (ADF) pipelines
  - Parameterized for Dev and Prod environments
  - Uses Managed Identity and Azure Key Vault for authentication
  - CI/CD via Azure DevOps to promote from Dev to Prod
  - Data partitioned into Parquet files in Azure Data Lake Storage Gen2

- **Transformation Layer:** Databricks + dbt Core
  - Databricks Autoloader with micro-batching to Unity Catalog (SQL Warehouse)
  - dbt Core models containerized with Docker
  - Deployment via GitHub Actions → Azure Container Registry → Azure Container Apps Job
  - Orchestrated by Azure Data Factory pipelines in Prod
- **Observability:**
  - Log Analytics for monitoring Container Apps jobs
  - Triggers scheduled at defined intervals
- **Consumption Layer:** Power BI
  - Consumes curated semantic models from Databricks SQL Warehouse
  - Includes reports and paginated reports

## 🔑 Key Features

- Separation of **Dev** and **Prod** environments
- Secure authentication with **Service Principal**, **Managed Identity**, and **Key Vault**
- Full CI/CD setup using **Azure DevOps** and **GitHub Actions**
- Clear distinction between **data plane (data movement)** and **control plane (orchestration & jobs)**
- Reproducible dbt Core transformations via **Docker containers**

## 📊 Architecture Diagram

Refer to `/03-docs/architecture-diagram.png` for the high-level solution
architecture.

## 📌 How to Navigate

1. Start with **01-ingestion-adf** to understand the raw ingestion process.
2. Continue with **02-transformation-dbt** for transformations and containerization.
3. Use **03-docs** for reference materials and architecture diagrams.

## 👤 Author

*Created as part of Azure-based BI/Data Engineering solution.*
