## What is Data Warehousing

A data warehouse is a centralized repository that stores large amounts of structured data from various sources for analysis and reporting.

- Central repository of integrated data from one or more different sources.
- Stores current and historical data in a single place.

### Key Features of a Data Warehouse:

#### 1. Integrated:
  - Combines data from multiple sources (e.g., databases, spreadsheets, and external systems) into a unified format.
#### 2. Subject-Oriented:
  - Focuses on specific areas like sales, finance, or marketing, allowing users to analyze data from different business functions.
#### 3. Non-Volatile:
  - Once data is stored in a data warehouse, it is stable and typically not altered. Updates to data are done through new records (e.g., adding historical records or new periods).
#### 4. Time-Variant:** 
  - Tracks changes over time, helping in trend analysis, forecasting, and decision-making.

### Why Do We Need a Data Warehouse?

By using a data warehouse, organizations can transform raw data into valuable insights, supporting strategic planning and improving overall business efficiency.

#### 1. Centralized Data Management:
  - Data warehouses provide a single source of truth by integrating data from various systems, making it easier to analyze and generate reports.
#### 2. Improved Data Quality:
  - Data warehouses often include processes for cleaning, transforming, and validating data, ensuring consistency and accuracy.
#### 3. Historical Analysis:
  - Data warehouses store historical data, enabling users to track changes over time and make data-driven decisions based on past performance.
#### 4. Business Intelligence (BI):
  - They support BI tools, enabling advanced reporting, dashboards, and data visualization for better decision-making.
#### 5. Scalability:
  - A data warehouse can handle large volumes of data and adapt as the organization grows.

-------------------------

## Components of a Data Warehouse

![](https://github.com/rohish-zade/data-warehousing/blob/main/Introduction/images/components%20of%20data%20Datawarehouse.png)

#### Source Systems:
  - These are operational databases, applications, or external sources where data originates (e.g., CRM, ERP, sales systems).
##### ETL Process (Extract, Transform, Load):
  - **Extract:** Retrieve data from source systems.
  - **Transform:** Cleanse, reformat, and prepare the data for storage.
  - **Load:** Insert the transformed data into the data warehouse.
#### Data Staging Area: 
  - A temporary storage area where data is cleaned and transformed before loading into the warehouse.
#### Data Warehouse Database: 
  - The central repository where the integrated, cleaned, and organized data is stored.
#### Data Marts: 
  - Subsets of the data warehouse tailored to specific departments or business areas (e.g., finance, marketing).
  - Category level separation inside data warehouse
#### BI Tools and Applications: 
  - Tools for querying, reporting, and analyzing the data stored in the warehouse (e.g., Tableau, Power BI).


### ETL vs ELT:
- ELT is the same process as ELT but we switch the order of loading and transforming the data.

| Metric          | ETL                                                                                              | ELT                                                                                                                              |
| --------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Data Processing | Data is processed before loading into the target system.                                         | Data is loaded into the target system first and then transformed within the system.                                              |
| Transformations | Transformation occurs outside of the target system.                                              | Transformation occurs within the target system, leveraging its processing capabilities.                                          |
| Performance     | Can be slower for large datasets due to transformation before loading                            | Generally faster for large datasets as transformation happens in the target system                                               |
| Data Storage    | Requires staging area for transformed data                                                       | Requires less staging area as raw data is loaded first                                                                           |
| Data Quality    | Higher data quality as data is cleansed before loading                                           | Lower initial data quality as raw data is loaded first                                                                           |
| Maturity        | Has been the traditional approach to data integration and has been extensively used for decades. | Relatively newer concept compared to ETL but gaining popularity rapidly, especially with the rise of cloud-based data platforms. |
| Examples        | Informatica, IBM DataStage, Talend.                                                              | Apache Spark, Google BigQuery, Amazon Redshift.                                                                                  |
| Ideal for       | Well defined data models as data quality is critical.                                            | Agile environment's, on-the-go schema.                                                                                           |
| Business Value  | Reporting and Analytics.                                                                         | ML and Data Science.             