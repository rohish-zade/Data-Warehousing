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


## Data Warehouse vs Data Lake
A data lake is a centralized repository that allows organizations to store all their structured and unstructured data at any scale.

| Metric          | Data Warehouse          | Data Lakes                                     |
| --------------- | ----------------------- | ---------------------------------------------- |
| Data Type       | structured data         | structured, semi-structured, unstructured data |
| Data Processing | ETL data pre-proccesing | ELT data pre-proccesing                        |
| Schema          | predefined schema       | ad-hoc schema                                  |
| Data Quality    | high data quality       | low data quality                               |
| Scalability     | vertical scalable       | horizontal scalable                            |

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

### Types of Data Marts

#### Dependent Data Mart:
- A dependent data mart draws data from a centralized data warehouse. It relies on the organization’s primary data warehouse as the source of cleaned, processed data.
- Example: A company-wide data warehouse containing data from all departments could feed a dependent data mart that is specific to the finance team.

#### Independent Data Mart:
- An independent data mart is a stand-alone system that collects data directly from sources without the use of a centralized data warehouse. It functions as a mini data warehouse for a particular business unit or department.
- Example: A marketing department could have its own data mart that gathers data from campaign management tools and customer feedback systems without using a larger, central data warehouse.

#### Hybrid Data Mart:
- A hybrid data mart combines data from both a centralized data warehouse and external sources. 
- It integrates data from the warehouse as well as from real-time external systems to create a more flexible and responsive environment for specific needs.
- Example: A sales data mart may pull daily sales performance from the main warehouse, while integrating live market data from external systems.

### Why Use a Data Mart?
- **Departmental Focus:** Data marts allow specific departments to focus on data that is relevant to them.
- **Faster Query Performance:** Since a data mart contains only a small, subject-specific subset of data, queries run faster compared to querying a full-scale data warehouse.
- **Cost-Effective:** Building a full data warehouse can be time-consuming and expensive. Data marts provide a faster and cheaper solution for departments that need immediate access to analytics.
- **Flexibility:** Data marts can be tailored to meet the specific needs of a department without interfering with other parts of the organization.
- **Simplified Access:** Non-technical users can access the data they need through pre-built dashboards or reports, reducing the complexity associated with retrieving data from a large warehouse.


### Disadvantages of Data Marts
- **Data Silos:** If multiple independent data marts are created for different departments, this can lead to data silos, where different departments have different views of the same data, causing inconsistencies.
- **Limited Scope:** Data marts focus on specific business areas, so they may not provide a holistic view of the organization’s data like a data warehouse.
- **Duplication of Data:** Multiple data marts can lead to redundancy, as the same data may be duplicated in different marts, increasing storage costs.
- **Maintenance Complexity:** If data marts grow in size or complexity, maintaining them can become challenging. It may lead to higher costs and overhead in managing multiple marts.

### Data Mart vs. Data Warehouse
| Feature            | Data Mart                          | Data Warehouse                     |
|--------------------|------------------------------------|------------------------------------|
| **Scope**          | Department-specific (narrow focus) | Enterprise-wide (broad focus)      |
| **Size**           | Small subset of data               | Large volume of data               |
| **Data Sources**   | Limited to specific business areas | Integrates data from all business units |
| **Implementation** | Faster and simpler                 | More time-consuming and complex    |
| **Maintenance**    | Easier to maintain                 | Requires more resources            |
| **Query Performance** | Faster due to smaller size     | May be slower for complex queries  |


------------------------------

## Multi-Temperature Data Management Model

The Multi-Temperature Data Management model refers to a strategy used in data warehousing and data management to handle different types of data based on its usage frequency and importance.

The model categorizes data into various "temperature zones" like hot, warm, and cold based on how often it is accessed and how critical it is for operational and analytical purposes.

### Types of Data in the Multi-Temperature Model

#### Hot Data
-  Frequently accessed, mission-critical data that requires high-performance storage and fast access times.
- Examples: Current transactional data, customer interactions, real-time analytics.

#### Warm Data 
- Moderately accessed data that may not require real-time access but still needs to be readily available for analysis or operational purposes.
- Examples: Monthly sales reports, aggregated data from the last few quarters.

#### Cold Data 
- Infrequently accessed or dormant data that is kept for compliance, regulatory, or long-term archival purposes.
- Examples: Archived transaction records, older financial data, logs.

### Benefits of the Multi-Temperature Model
- **Cost Optimization:** By storing data based on its temperature, organizations can save on storage costs. Hot
- **Improved Performance:** Frequently accessed hot data is stored in fast, low-latency storage, ensuring quick query responses and real-time processing.
- **Efficient Resource Utilization:** It ensures that high-performance resources are allocated to critical data, while less frequently used data is stored on lower-cost storage.
- **Scalability:** As data grows over time, a multi-temperature approach allows the data warehouse to scale efficiently by offloading older or less critical data to cheaper storage solutions without compromising performance.

### Implementation Process 
- Frequency of access 
- Data change rate 
- Identify which storage type is suitable for the project