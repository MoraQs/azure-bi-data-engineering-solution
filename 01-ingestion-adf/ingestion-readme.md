# 🚀 Data Ingestion Pipeline

## 📌 Overview

This project handles the **ingestion layer** of the Azure BI/Data Engineering solution.

It extracts data from **Microsoft Fabric SQL Database**, loads it into **Azure Data Lake Storage (ADLS)**, and makes it available for downstream processing in **Azure Databricks Unity Catalog**.

## 🏗️ Architecture

**Flow:**
Fabric SQL DB ➝ Azure Data Factory (ADF) ➝ ADLS (Parquet Partitioned) ➝
Databricks Autoloader ➝ Unity Catalog (Bronze Layer)

- **Fabric SQL Database**: Source system.
- **Azure Data Factory (ADF)**: Orchestrates ingestion pipelines.
- **Azure Data Lake Storage (ADLS Gen2)**: Stores ingested data in **partitioned Parquet** format.
- **Databricks Autoloader**: Streams/micro-batches data into the **Bronze layer** of Unity Catalog.
- **Unity Catalog**: Provides governance and schema management.

## 🔐 Dev/Prod Setup & Security

- **Resource Groups**: Separate Dev and Prod RGs.
- **ADF Instances**: Dev ADF + Prod ADF.
- **Storage Accounts**: Dev SA + Prod SA.
- **Authentication**: Managed Identities + Azure Key Vault for secrets.
- **Parameterization**: Pipelines parameterized to ensure environment reusability.
- **Triggers**: Scheduled & parameterized at the trigger level to avoid hardcoding credentials.

## ⚙️ CI/CD (Azure DevOps)

- Dev pipelines are integrated with **Git (Azure Repos)**.
- **Azure DevOps Pipelines** push code from Dev ➝ Prod.
- **Parameter overrides** handled via YAML at deployment time.

## ⏰ Scheduling

- Ingestion pipelines run on **scheduled triggers** (configurable).
- Supports both **batch** and **micro-batch** ingestion.

## 👤 Author

*Tunde Morakinyo*