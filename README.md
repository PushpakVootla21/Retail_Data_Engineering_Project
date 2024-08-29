# Retail Data Analysis | Data Engineering project using Azure
## Introduction
This project leverages Azure's robust data engineering ecosystem to analyze retail data, utilizing Azure Data Lake Storage Gen2 (ADLS) for scalable storage , Azure SQL Database for relational data management, Amazon S3 for data ingestion, Azure Data Factory for data integration, and Azure Databricks for data transformation and analytics. The project aims to provide actionable insights from retail data, enabling informed business decisions. By integrating these Azure services, the project ensures a seamless data pipeline, from data ingestion to visualization.

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

## Architecture
![Project Architecture](https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/blob/main/Pipeline_Architecture.jpg)

The diagram depicts a retail customer data pipeline architecture. This pipeline is responsible for processing orders data, order items data and customer data to ultimately load it into an Azure SQL database. Here's a breakdown of the components and how they work together:

### Data Sources & Storage:

1. Orders Data:  The pipeline starts with order data coming from an external source to ADLS Gen2. This represents the raw, initial data about customer orders. Data will be CSV format
2. Customers Data: This data comes from a pre-existing database, in this case, an Azure SQL database.
3. Order Items Data: The data is coming from external cloud storage service S3 (from AWS) holds the order_items data and landing into ADLS Gen2. Data will be in JSON fromat

### Data Transformation and Processing:

1. Azure Data Factory: This is a cloud-based data integration service that orchestrates data movement and transformation. In this pipeline, it plays a crucial role in:
   - Copying Order Items Data: The data factory is configured to copy order_items data from the S3 bucket to the ADLS Gen2 container. This involves setting up a connection to S3, defining the copy operation, and specifying the destination location in ADLS Gen2.

2. Data Bricks: This is a cloud-based platform for data engineering and analytics. It uses Apache Spark for processing data at scale. Here's how it's used in the pipeline:
   - Data Processing: Data Bricks processes the raw order data and customer data. This involves:
     1.  Data cleaning and transformation.
     2.  Applying business logic (e.g., calculating total order value, grouping items by category).
     3.  Joining order data with customer data for a more comprehensive view.
3. Data Loading: Once the data is processed, it's loaded into the Azure SQL database.

### Data Destination for serving layer: 

1. Azure SQL DB: This is the final destination for the processed data. It's a fully managed relational database service offered by Azure. By
   storing the data in an SQL database, it becomes easily queryable and accessible for reporting and analytics purposes.
   
### Key Points:
1. Data Pipeline: The entire process from data ingestion to loading into the SQL database is orchestrated as a data pipeline. This ensures consistent data flow, handling of changes, and data quality.
   
2. Data Security: Security measures are likely implemented throughout the pipeline, including secure access control to ADLS Gen2 and the Azure SQL database, encryption in transit and at rest, and data masking or anonymization where necessary.
   
   - Databricks Access Token: Instead of hardcoding the Databricks access token within the Data Factory pipeline or other components, store it securely in Azure Key Vault. The pipeline can then retrieve this token during execution using the Key Vault API.
     
   - Database Credentials: Similarly, store the database connection information (username, password) for the Azure SQL DB in Key Vault. This prevents exposing these sensitive credentials directly in your code.
     
   - Secure Access Credentials: The solution utilizes Azure Key Vault to securely store sensitive credentials such as AWS access keys for accessing the S3 bucket. This eliminates the need to hardcode credentials directly into the code, ensuring a more robust and secure environment.
     
4. Scalability: The pipeline utilizes cloud services like Azure Data Lake Storage and Azure Data Factory, making it highly scalable to handle large volumes of data.
   
6. Orchestration: Azure Data Factory simplifies the orchestration of the entire data pipeline, ensuring that the transformation and loading processes happen in a defined sequence.
   
7. Transformation: Data Bricks allows for sophisticated data transformation logic, enabling data cleaning, aggregation, and feature engineering.
   
8. Monitoring: The Azure Data Factory can be configured to monitor the pipeline activities, including trigger executions, transformation performance, and data loading.

The architecture illustrates a typical process for ingesting raw customer data, transforming it for analysis, and storing it in a database. This approach provides the flexibility and scalability needed for a modern retail analytics pipeline.

## Datasets used
1. Customers: Represents customers who place orders.
2. Orders: Represents individual orders placed by customers.
3. Order Items: Represents the individual items included within an order.

Here is the link to the datasets - https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/tree/main/Datasets

## Data Model
![Data Model](https://github.com/PushpakVootla21/Retail_Data_Engineering_Project/blob/main/ER.png)

This diagram shows a database schema, which describes the structure of a database. The database is about orders, customers, and the items in those orders. Here's a breakdown of the entities and their relationships:

### Entities:

1. Customers: Represents customers who place orders. Includes information like customer ID, first and last name, username, password, address, city, state, and postal code.
   
3. Orders: Represents individual orders placed by customers. Includes information like order ID, order date, customer ID, and order status.
   
4. Order Items: Represents the individual items included within an order. Includes information like order item ID, the order ID it belongs to, the product ID, quantity, subtotal, and product price.
   
### Relationships:

1. Customers and Orders: A customer can place multiple orders (1-to-many relationship). Each order is associated with a single customer.
2. Orders and Order Items: Each order can have multiple items (1-to-many relationship). Each item belongs to a single order.


