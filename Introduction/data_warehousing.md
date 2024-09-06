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
- Category level separation inside data warehouse.

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


### Database vs Data Warehouse

| Metric            | Database                    | Data Warehouse                     |
| ----------------- | --------------------------- | ---------------------------------- |
| Design Purpose    | to record data              | to analyze data                    |
| Transaction Type  | OLTP                        | OLAP                               |
| Orientation       | application-oriented        | subject-oriented                   |
| Data Freshness    | data available in real-time | data must be refreshed when needed |
| Modeling Approach | relational data modeling    | dimensional data modeling          |
| Data Volume       | GB/TB (<1000M)              | TB/PB (1000M>)                     |
| Data Structure    | Normalized	              | Denormalized                       |


-----------------------------------

## Types of Data Warehouses

#### Enterprise Data Warehouse (EDW):
- Centralized data warehouse for the entire organization.
- Used to provide a consistent view of data across departments.

#### Operational Data Store (ODS):
- A system used to store current transactional data, which is usually used for operational reporting.
- Can be updated in real-time.

#### Data Mart:
- A smaller, department-specific subset of a data warehouse.
- Built for specific business lines or teams (e.g., sales, marketing).


## Data Warehouse Architecture
There are three main types of data warehouse architectures:

#### Single-Tier Architecture:
- Simplest form.
- Combines the data warehouse and operational database into one system.
- Rarely used due to performance and complexity issues.

#### Two-Tier Architecture:
- Separates the data warehouse from the source systems.
- Allows for data extraction and storage in the warehouse.
- Still, processing and performance can be a bottleneck.

#### Three-Tier Architecture (most common):
- Tier 1 (Bottom): Source systems (e.g., operational databases).
- Tier 2 (Middle): Data warehouse and data marts.
- Tier 3 (Top): BI tools and reporting layer.
- This model ensures better scalability and performance.

-------------------------------------

## Data Marts
- A data mart is a subset of a data warehouse that is focused on a specific business area, department, or subject matter.
- It contains a focused selection of data relevant to the particular needs of a business unit, such as sales, finance, or marketing, making it easier for users in that department to access and analyze data without dealing with the entire data warehouse.
- Data marts are often smaller, more manageable, and quicker to implement than a full-scale data warehouse. 
- They are optimized for specific queries, analysis, and reporting for a particular business function.

![](https://raw.githubusercontent.com/rohish-zade/data-warehousing/main/Introduction/images/warehouse-and-mart-v1.webp)