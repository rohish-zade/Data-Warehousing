## What is Data Modeling?
- Data modeling is the process of creating a visual representation of an organization's data, including how it's collected, stored, and analyzed.
- It defines how data is organized, the relationships between different data entities, and how it flows through the system.
- Data modeling is a critical step in building a data warehouse because it defines how data will be stored, integrated, and accessed across the entire system.

### Why is data modeling important?
Organizations today collect a large amount of data from many different sources. However, raw data is not enough. You need to analyze data for actionable insights that can guide you to make profitable business decisions. Accurate data analysis needs efficient data collection, storage, and processing. There are several database technologies and data processing tools, and different datasets require different tools for efficient analysis.

Data modeling gives you a chance to understand your data and make the right technology choices to store and manage this data.
In the same way an architect designs a blueprint before constructing a house, business stakeholders design a data model before they engineer database solutions for their organization.

#### Data modeling brings the following benefits:
- Reduces errors in database software development.
- Facilitates speed and efficiency of database design and creation.
- Creates consistency in data documentation and system design across the organization.
- Facilitates communication between data engineers and business intelligence teams.

-------------------------------

## Types of Data Models

### Conceptual Data Model:
- Provides a high-level view of the overall data structure.
- It defines what data will be stored in the warehouse but doesn’t include details like specific fields or data types.
- Focus on entities and their relationships without getting into technical details.

![](https://github.com/rohish-zade/data-warehousing/blob/master/Data%20Modeling/images/conceptual-model-order-system.png)

- **Example:** In a retail business, a conceptual model may define entities like Customer, Product, Order, and Store without specifying the actual columns.


### Logical Data Model:
- A more detailed representation of the data structure, defining the relationships between entities, attributes, and keys.
- Less abstract, translate the conceptual model into more detailed structure.
- The logical model doesn’t concern itself with the physical storage details, but it does define how data is logically organized.
- Involves normalization for data integrity.

![](https://github.com/rohish-zade/data-warehousing/blob/master/Data%20Modeling/images/logical-data-model.png)

- **Example:** The Customer entity may have attributes like Customer ID, Customer Name, Email, and Phone Number. Relationships between entities, such as "each Order belongs to one Customer" and "each Order contains multiple Products," are also defined.


### Physical Data Model:
- Describes how the data will be physically stored in the database. 
- It specifies data types, indexes, partitions, and other details for optimizing storage and retrieval performance.

![](https://github.com/rohish-zade/data-warehousing/blob/master/Data%20Modeling/images/physical-data-model.png)

- **Example:** The Customer table will have columns with specific data types such as Customer ID (integer), Customer Name (varchar), and Email (varchar). It might also define indexes on Customer ID for faster lookup.

------------------

## Key Components of Data Modeling

1. **Entities:**
- Entities represent objects or concepts that store data. In data warehousing, these are typically tables.
- Example: Common entities in a retail data warehouse include Customer, Product, Order, and Store.

2. **Attributes:**
- Attributes represent the data fields or properties within an entity.
- Example: For the Customer entity, attributes might include Customer ID, Name, Email, and Address.

3. **Relationships:**
- Relationships define how entities are related to each other. In data warehousing, this typically manifests as foreign key relationships.
- Example: A Customer can place multiple Orders (1-to-many relationship), and each Order can contain multiple Products (many-to-many relationship, often handled via a junction table).

4. **Keys:**
- Keys are used to uniquely identify records and establish relationships between tables.
  - **Primary Key (PK):** Uniquely identifies each record in a table.
  - **Foreign Key (FK):** Links one table to another by referencing the primary key of the related table.
- Example: The Customer ID in the Customer table is a primary key. In the Order table, the Customer ID is a foreign key linking orders to customers.

-------------------

## Steps in Data Modeling for Data Warehousing

#### Requirement Gathering:
- Understand the business needs, the questions to be answered, and the data sources available. - This step involves consulting with business stakeholders to define the scope of the data warehouse.

#### Identify Entities and Relationships:
- Define the key entities (like customer, product, sales) and how they relate to each other. - This involves identifying fact tables (quantitative data) and dimension tables (descriptive data).

#### Design the Logical Data Model:
- Create a detailed logical data model, including the entities, their attributes, relationships, and keys. Ensure that the design supports the required queries and reporting.

#### Define the Physical Data Model:
- Translate the logical model into a physical model. 
- This involves selecting appropriate data types, indexing strategies, partitioning large tables, and optimizing for performance.

#### Build ETL Processes:
- Design the Extract, Transform, Load (ETL) processes to populate the data warehouse.
- The ETL processes need to move data from source systems to the warehouse while maintaining consistency and accuracy.

#### Optimize and Test:
- Test the data model with actual queries to ensure it performs as expected. Optimization might include indexing frequently queried columns or partitioning large tables.