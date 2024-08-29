# Retail Data Analysis | Data Engineering project using Azure
## Introduction
This project leverages Azure's robust data engineering ecosystem to analyze retail data, utilizing Azure Data Lake Storage Gen2 (ADLS) for scalable storage , Azure SQL Database for relational data management, Amazon S3 for data ingestion, Azure Data Factory for data integration, and Azure Databricks for data transformation and analytics. The project aims to provide actionable insights from retail data, enabling informed business decisions. By integrating these Azure services, the project ensures a seamless data pipeline, from data ingestion to visualization.

## Architecture
![Project Architecture](https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/blob/main/Pipeline_Architecture.jpg)

## Technology used
1. Programming Language - Pyspark
2. Scripting Language - SQL
3. Azure Cloud Platform
   - Azure Data Lake Storage (ADLS Gen2)
   - Azure SQL Database
   - Azure Key Vault
   - Azure Data Factory
   - Azure Triggers
   - Azure Databricks
4. Amazon Web Services (AWS Cloud)
   - Amazon S3

## Datasets used
1. Customers: Represents customers who place orders. Includes information like customer ID, first and last name, username, password, address, city, state, and postal code.
2. Orders: Represents individual orders placed by customers. Includes information like order ID, order date, customer ID, and order status.
3. Order Items: Represents the individual items included within an order. Includes information like order item ID, the order ID it belongs to, the product ID, quantity, subtotal, and product price.

Here is the link to the datasets - https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/tree/main/Datasets

## Data Model
![Data Model](https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/blob/main/ER.png)


