## Types of keys in DBMS and Data Warehouse
In databases and data warehousing, keys play a critical role in ensuring data integrity, relationships, and efficient querying.


### Primary Key (PK)
- A column (or a set of columns) that uniquely identifies each row in a table.
- Must contain unique values.
- Cannot contain `NULL` values.
- Ensures that each record in the table is unique.
- **Example:** In a `Customer` table, `CustomerID` can be the primary key.


### Foreign Key (FK)
- A column (or a set of columns) that creates a relationship between two tables by referencing the primary key in another table.
- Links two tables by enforcing referential integrity.
- Can contain `NULL` values if the relationship is optional.
- Establishes relationships between tables (one-to-one, one-to-many).
- **Example:** In an `Orders` table, `CustomerID` can be a foreign key that references the `CustomerID` in the `Customer` table.


### Unique Key
- A column (or set of columns) that ensures all values are unique, but unlike the primary key, it can contain `NULL` values.
- Enforces uniqueness of the column’s values.
- Can be used as an alternate key if required.
- Helps avoid duplicate values in certain columns.
- **Example:** An email column in a `Users` table might have a unique constraint to prevent duplicate email addresses.


### Candidate Key
- Any other column which can work like a primary key apart from original primary key.
- A table can have multiple candidate keys.
- A primary key is chosen from the set of candidate keys.
- **Example:** If a `Customer` table has both `CustomerID` and `Email` that can uniquely identify a customer, both are candidate keys.


### Composite Key
- A combination of two or more columns used together as a primary or unique key to uniquely identify a row.
- Both columns together must be unique.
- Common in many-to-many relationship tables.
- Used when no single column can uniquely identify a row.
- **Example:** In an `Enrollment` table for a course, the combination of `StudentID` and `CourseID` can act as a composite key.


### Alternate Key
- Any candidate key that is not chosen as the primary key.
- Can still be enforced with a UNIQUE constraint.
- Can still be enforced with a UNIQUE constraint.
- **Example:** In a `Product` table, `ProductID` is the primary key, and `SKU` (Stock Keeping Unit) is an alternate key.


## Data Warehousing-Specific Keys:

### Natural Key
- A key based on real-world, business-related data (like email or Social Security Number).
- Natural keys are columns in a table that naturally and uniquely identify each record based on the characteristics of the data. 
- They are derived from real-world attributes and may include values like social security numbers, email addresses, or product SKUs.
- Comes from existing data.
- Can be volatile and subject to change.
- Less common in data warehouses, where surrogate keys are often preferred for performance reasons.

**Example:**
- In a `Customers` table, the `Social Security Number (SSN)` of a customer in the U.S. can be considered a natural key because it is a unique identifier assigned by a government entity.
- In an `Employee` table, the `Employee Email` could serve as a natural key, assuming each email is unique

### Business Key
-  A business key is a column or set of columns that uniquely identifies a business entity within a specific context.
- Similar to a natural key but specifically emphasizes its relevance to business processes.
- Used in dimensions as attributes, but a surrogate key might still be used as the primary key in a fact table.

**Example:**
- In a `Products` table, a `Stock Keeping Unit (SKU) `can be a business key. It is assigned by the business to track products in inventory.

### Surrogate Key (in Data Warehousing)
- An artificial key used in data warehousing to ensure each row in dimension tables has a unique identifier.
- Helps maintain historical records and manages slowly changing dimensions (SCD).
- **Example:** A `ProductKey` that uniquely identifies each product version in a dimension table.
