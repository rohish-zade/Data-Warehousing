## Normalization
Data normalization is a database design technique that helps organize data in a relational database to reduce redundancy and dependency.
Used to organize data efficiently, minimize redundancy, and eliminate undesirable characteristics like insertion, update, and deletion anomalies.
It involves dividing a database into smaller tables and defining relationships between them, ensuring data integrity and consistency.

The concept of normalization is based on normal forms (NF), which are levels of database organization. Each normal form builds upon the previous one, with higher normal forms reducing data redundancy and complexity.

**Goals of Normalization:**
- Reduce Data Redundancy: Avoid storing the same data in multiple places.
- Improve Data Integrity: Ensure that data remains accurate, consistent, and up to date.
- Minimize Anomalies: Prevent issues like insertion, update, and deletion anomalies.

**Data modification anomalies can be categorized into three types:**
- **Insertion Anomaly:** Insertion Anomaly refers to when one cannot insert a new tuple into a relationship due to lack of data.
- **Deletion Anomaly:** The delete anomaly refers to the situation where the deletion of data results in the unintended loss of some other important data.
- **Updatation Anomaly:** The update anomaly is when an update of a single data value requires multiple rows of data to be updated.

## Types of Normal Forms

### 1. First Normal Form (1NF)
- Every column/attribute need to have a single value.
- It states that an attribute of a table cannot hold multiple values. It must hold only single-valued attribute.
- Each row should be unique. Either through a single or multiple columns. Not mandartory have a primary key.

**Example:** 

- Relation `EMPLOYEE` is not in 1NF because of multi-valued attribute `EMP_PHONE`.

  ![](https://github.com/rohish-zade/data-warehousing/blob/master/Introduction/images/1NF_1.png)

- The decomposition of the EMPLOYEE table into 1NF has been shown below:

  ![](https://github.com/rohish-zade/data-warehousing/blob/master/Introduction/images/1NF_2.png)


### 2. Second Normal Form (2NF)
- Must be in 1NF
- All non key attributes must be fully dependent on candidate key.
  i.e If a non key column is partially dependent on candidate key(subset of columns forming the candidate key) then split them into separate tables.
  
- Every table should have primary key and relationship between the tables should be formed using a foreign key.

**Candidate key:** Set of columns which uniquely identify a record. A table can have multiple candidate keys.
**Non-key columns:** Columns which are not part of the canditate key or primary key.
**Partial Dependency:** 
 - If your candidate key is a combination of 2 columns(or multiple columns) then every non key columns(columns which are not part of candidate key) should be fully dependent on all the columns
 - If there is any non key column which depends only on one of the candidate key columns then this results in partial dependency.

- When a table has a primary key that is made up of two or more columns, then all the columns(not included in the primary key) in that table should depend on the entire primary key and not on a part of it. If any column(which is not in the primary key) depends on a part of the primary key then we say we have Partial dependency in the table.



**Example:** 
- There is a table with information about customers of an insurance agency and the plans they have subscribed to. 
- The following is the sample table:

  | Customer ID | Plan ID | Customer Name | Plan Name               |
  |-------------|---------|---------------|-------------------------|
  | 101         | A1      | Rahul         | Health Benefit Plan      |
  | 102         | A2      | Seema         | Life Insurance Plan      |
  | 103         | A3      | Neha          | Vehicle Insurance Plan   |

- In the above table, the prime attributes are `Customer ID` and `Plan ID`. Because `Customer Name` can be determined by the `Customer ID` and `Plan Name` by `Plan ID`, there is partial dependency in the table. 

- To remove the dependency and convert it into a second normal form, we can divide this table into smaller tables. 
- The following will be the result:

  *CustomerInfo*

  | Customer ID | Customer Name |
  |-------------|---------------|
  | 101         | Rahul         |
  | 102         | Seema         |
  | 103         | Neha          |


  *CustomerPlan*

  | Customer ID | Plan ID |
  |-------------|---------|
  | 101         | A1      |
  | 102         | A2      |
  | 103         | A3      |


  *PlanDetail*

  | Plan ID | Plan Name              |
  |---------|------------------------|
  | A1      | Health Benefit Plan     |
  | A2      | Life Insurance Plan     |
  | A3      | Vehicle Insurance Plan  |



### 3. Third Normal Form (3NF)
- Must be in 2NF
- Avoid Transitive Depedencies

- **Transitive Dependency:**
  - Lets say have a table T which has 3 coumns namely A, B and C
  - If A is functionally dependent on B and B is functionally dependent on C then we can say that A is functinally dependent on C.


**Example:**
- The following example showcases the table `WarehouseDetail` and we will normalize it to the third normal form. 

  | Warehouse Code | Warehouse Name | Warehouse Pincode | Warehouse City |
  |----------------|----------------|-------------------|----------------|
  | 101            | JC Warehouse   | 462001            | Bhopal         |
  | 102            | AD Warehouse   | 320008            | Ahmedabad      |
  | 103            | HG Warehouse   | 600005            | Chennai        |

- In the above table, there is a transitive dependency because of two conditions:
  - Warehouse Code-> Warehouse Pincode
  - Warehouse Pincode-> Warehouse City

- To convert it into the third normal form, we will divide the table into two. The following will be the result:

  *WarehouseDetail*
  
  | Warehouse Code | Warehouse Name | Warehouse Pincode |
  |----------------|----------------|-------------------|
  | 101            | JC Warehouse   | 462001            |
  | 102            | AD Warehouse   | 320008            |
  | 103            | HG Warehouse   | 600005            |
  
  *WarehouseLocation*
  
  | Warehouse Pincode | Warehouse City |
  |-------------------|----------------|
  | 462001            | Bhopal         |
  | 320008            | Ahmedabad      |
  | 600005            | Chennai        |
