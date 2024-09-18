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