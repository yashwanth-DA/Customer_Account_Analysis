# Customer_Account_Analysis

## 📌 Project Overview

This project demonstrates a full data engineering pipeline using **Azure Data Factory** to move and transform data through a medallion architecture (Bronze → Silver → Gold). The pipeline extracts data from a **Local Machine**, lands it in **Azure Data Lake Storage (ADLS)**, applies necessary transformations,scdtype1 and scdtype2 and then loads the refined data into **Azure SQL Database**.

## 🗂️ Project Architecture

![project architecture](https://github.com/user-attachments/assets/cd59a2b4-600f-4d91-9f80-aa74af104ff4)

1. **Bronze Layer (Raw Layer)**
   - **Source**: Data is initially extracted from a Virtual Machine.
   - **Target**: Raw data is copied as-is to the Bronze layer in ADLS.
   - **Files Included**: 
     - `accounts.csv`
     - `customers.csv`
     - `loans.csv`
     - `loan_payments.csv`
     - `transactions.csv`

2. **Silver Layer (Cleaned/Transformed Layer)**
   - **Process**: Data in the Bronze layer is transformed to address data quality issues such as:
     - Removing nulls
     - Removing duplicates
     - Joining relevant tables (if needed)
   - **Target**: Cleaned and structured data is saved in the Silver layer of ADLS in delta files.

3. **Gold Layer (Business-Ready Layer)**
   - **Target**: Transformed data from the Silver layer is loaded into **Azure SQL Database** for analytics, reporting, or further downstream consumption.

## 🛠️ Tools & Technologies Used

- **Azure Data Factory**: Orchestration and transformation tool.
- **Azure Data Lake Storage Gen2**: Data storage for Bronze and Silver layers.
- **Azure SQL Database**: Final destination (Gold layer) for refined data.
- **Azure Virtual Machine**: Source for initial raw files.
- **Azure Key Vault**: Storing secrets.

## 📁 File Descriptions

- `accounts.csv`: Contains account-level details.
- `customers.csv`: Contains customer profile information.
- `loans.csv`: Contains loan application and approval data.
- `loan_payments.csv`: Contains details of payments made on loans.
- `transactions.csv`: Contains transaction records related to accounts.

## 🚀 Pipeline Overview

1. **Copy Activity** from VM to ADLS (Bronze)
2. **Data Flow** transformations from Bronze to Silver in ADLS (Silver)
3. **Data Flow** to apply SCDTYPE 1 and SCDTYPE2 and load data from Silver to Azure SQL DB (Gold)

## ✅ Outcome

This layered approach ensures:
- Scalability
- Maintainability
- Separation of concerns between raw and transformed data
- Efficient querying for analytics at the Gold layer
