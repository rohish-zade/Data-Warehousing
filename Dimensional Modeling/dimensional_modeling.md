## What is Dimension Modeling?

- Dimensional data modeling is a design technique used in data warehousing to structure data in a way that is optimized for querying and reporting.
- It organizes data into facts and dimensions, creating a user-friendly model that facilitates fast retrieval of data for analytical purposes. 
- This approach simplifies complex data and is particularly useful for business intelligence (BI) and decision-making processes.


## Four steps of Dimensional Modeling design process:

### 1. Gather business requirement's (usability, performance)
 - what does your business do?(retail, real estate, insurance, banking, etc)
 - what measurement you want to analyze?
 - how does your current operational data looks like?

### 2. Identify Granularity(declare the grain)
- Grain mean the level of details available with the fact table.
- Basically this means what a single record in the fact table shows.
- Designed from the lowest possible grains

- Example: Consider we have a below fact table, firt requirement is to find the sales happened on the November 20th. We can easily find out the sales for that day as fact table contains the necessary details to get that 
- ![](https://github.com/rohish-zade/data-warehousing/blob/master/Dimensional%20Modeling/images/fact-table-1.png)
- Now, the requirement is to find out which customer pruchased which products on November 20th. There is no way we can find out this as fact table doesn't contain any product details.
- Now consider the below updated fact table with more atomic grain which has product details. Now its easy to get the answer for second requirement as well.
- ![](https://github.com/rohish-zade/data-warehousing/blob/master/Dimensional%20Modeling/images/fact-table-2.png)
- The finer the granularity (i.e., more detailed the data), the more rows there will be in the fact table this increases the volume of data stored but also enables more detailed analysis as we saw in the above example.

### 3. Identify Facts
- These are typically numerical values that the business wants to analyze and measure, such as quantities, sales amounts, or counts.
- Identify the facts or metrics that will be tracked in the fact table.
- Determine which metrics are essential for reporting, based on the business questions. Facts are typically additive (can be summed across dimensions).

### 4. Identify Dimensions
- Dimensions are descriptive categories used to slice and dice the facts and can include things like time, products, locations, and customers (who, what, when where, how, etc..)
- Identify the dimensions that provide context for the facts.
- Determine which objects or entities (e.g., products, stores, customers) are important for analyzing the facts and which attributes of those entities are relevant.

------------------

## Elements of Dimensional Modeling

### Fact Table
- The primary table in a dimensional model.
- Contains key measurements facts, primary key and foreign keys of dimensions.
- Quantitative and transactional data (profit, revenue).
- Can be aggregated.

### Dimension Table
- Contain descriptive data that provides context to the facts, such as product details, customer information, time periods, etc.
- Dimension tables contain attributes that describe who, what, where, and when related to the facts.

### Measures (Facts)
- Measures are numeric values or quantities stored in fact tables. 
- These are the metrics that businesses analyze and aggregate over time. 
- Measures are generally additive (e.g., sales amount) but can also be semi-additive (e.g., account balances over time) or non-additive (e.g., percentages).
  - **Additive:** Can be summed across all dimensions (e.g., sales amount).
  - **Semi-additive:** Can be summed over some dimensions, but not all (e.g., inventory levels over time).
  - **Non-additive:** Cannot be summed across dimensions (e.g., profit margin percentage).

### Dimension Attributes
- Dimension attributes provide additional descriptive details that give context to the facts. 
- Characteristic's of the dimension.
- These attributes are used in filtering, sorting, and grouping data during analysis.
  - **Descriptive Information:** Attributes like `Customer_Age`, `Product_Category`, or `Store_Location` help in analyzing data by adding meaning to raw facts.
  - **Hierarchical Information:** Some attributes form hierarchies, like `Year > Quarter > Month > Day`, which help in drilling down or rolling up data for different levels of analysis.

---------------------

### Type of facts in Fact Table(Facts Columns)

### Additive
- Additive facts are measures that can be aggregated across all columns.
- Can add the fact along any dimension.
- This includes sales, quantity or profit.
- **Example:**
  - Total Sales: The total sales revenue can be summed across all dimensions (e.g., date, product, store).

### can be aggregated across all columns.
- Semi-additive facts can be summed across some, but not all, dimensions.
- Can add along some dimension but not all dimensions.
- This includes balance, inventory, head count.
- **Example:**
  - Account Balance: You can sum account balances across customers or branches but not across  time, as balances are typically a snapshot at a specific point in time.
  - Inventory Levels: Inventory levels can be summed by location or product but not across time  because inventory at one time cannot be added to inventory at another time.

### Non-Additive Facts
- Non-additive facts cannot be summed or aggregated across any dimension. 
- Cannot add the fact along any dimension.
- These facts often represent ratios, percentages, or other calculations that do not make sense to aggregate.
- **Example:**
  - Profit Margin: Profit margin is a percentage or ratio, and summing it across different products or time periods would not provide meaningful results.
  - Average Price: Similarly, average price cannot be summed across products or time; it must be recalculated by weighting the prices based on the quantities sold.

---------------------

## Type of Facts (Fact Tables)

### Transaction Fact Table
- The Transaction Fact Table records individual, granular events or transactions as they happen.
- Each row in this type of fact table represents a single event, such as a sale, order, or payment.
- These tables store high-volume, low-level details.
- One record per transaction.

**Example:**
- A Sales Transaction Fact Table might capture individual sales transactions at a specific time.
- | Date_Key  | Product_Key | Store_Key | Customer_Key | Quantity_Sold | Total_Sales |
  |-----------|-------------|-----------|--------------|---------------|-------------|
  | 20230901  | 1001        | 500       | 2001         | 2             | 1000        |


### Periodic Snapshot Fact Table
- The Periodic Snapshot Fact Table captures data at regular intervals (e.g., daily, weekly, monthly) to provide a snapshot of the business at a specific point in time.
- Each row summarizes data for a fixed period, rather than a specific event.

**Characteristics:**
- Used to track regular, recurring metrics over time.
- Each row represents a summary of data for a specific period.
- Allows for time-series analysis, making it ideal for tracking changes over time.

**Example:**
- A Monthly Sales Snapshot Fact Table might summarize total sales for each product at the end of every month.
- | Date_Key  | Product_Key | Store_Key | Total_Sales | Total_Quantity_Sold |
  |-----------|-------------|-----------|-------------|---------------------|
  | 20230930  | 1001        | 500       | 50,000      | 150                 |


### Accumulating Snapshot Fact Table
- The Accumulating Snapshot Fact Table is used to track the lifecycle of events or processes that have a clear beginning and end, such as orders, claims, or projects. 
- The fact table gets updated as the process progresses through different stages.

**Characteristics:**
- Tracks events with defined stages or milestones.
- Each row represents a process, and columns are updated as the process moves through stages.
- Used for tracking processes like order fulfillment, claim processing, or project management.

**Example:**
- An Order Fulfillment Fact Table might capture the stages an order goes through (e.g., placed, shipped, delivered).

- | Order_Key | Order_Date | Ship_Date  | Delivery_Date | Payment_Amount | Order_Status |
  |-----------|------------|------------|---------------|----------------|--------------|
  | 1001      | 20230901   | 20230903   | 20230905      | 1500           | Delivered    |


### Factless Fact Table
- The Factless Fact Table does not contain any numeric or measurable facts but records the occurrence of events or activities. 
- It tracks relationships between dimensions and records whether an event happened, without any associated measure.

**Characteristics:**
- Used to track events or conditions.
- Contains only foreign keys that link to dimension tables.
- No measurable facts; just records the occurrence of an event.

**Examples of Factless Fact Tables**
- 1. Attendance Tracking
  - Scenario: A school wants to track student attendance in classes.

  - Factless Fact Table: Student_Attendance
  - | Date_Key  | Student_Key | Class_Key |
    |-----------|-------------|-----------|
    | 20230901  | 2001        | 101       |
    | 20230901  | 2002        | 101       |
    | 20230902  | 2003        | 102       |

  - Date_Key: Links to the date dimension table.
  - Student_Key: Links to the student dimension table.
  - Class_Key: Links to the class dimension table.

- This factless fact table records which students attended which classes on specific dates.


### Summary of Types of Fact Tables

| Type                           | Description                                             | Use Case                           |
|--------------------------------|---------------------------------------------------------|------------------------------------|
| Transaction Fact Table         | Records individual transactions or events.             | Sales, orders, payments.           |
| Periodic Snapshot Fact Table   | Captures summary data at regular intervals.            | Monthly/weekly sales, inventory tracking. |
| Accumulating Snapshot Fact Table | Tracks the lifecycle of events or processes.          | Order fulfillment, claims processing. |
| Factless Fact Table            | Records the occurrence of events without numeric measures. | Attendance, registration, event tracking. |

-------------------------

## Types of Dimensions

### Conformed Dimensions
- Conformed Dimensions are dimensions that are shared across multiple fact tables or data marts within a data warehouse. 
- They ensure consistency in reporting and analysis by providing a unified view of the dimension attributes across different fact tables.
- Constant and shared across multiple fact tables and has the same meaning.
- Example: Date as a key, product id as a key.

### Role-Playing Dimensions
- Role-Playing Dimensions are dimensions that are used in multiple contexts or roles within the same data warehouse. 
- They share the same attributes but are used in different ways depending on the context.
- Instead of creating separate dimensions for each role, this approach minimizes duplication and simplifies the model.
- Example: Date Dimension: Can play different roles such as Order Date, Ship Date, and Invoice Date.


### Junk Dimensions
- Junk Dimensions combine several low-cardinality attributes (attributes with a limited number of distinct values) into a single dimension.
- This helps to simplify the schema by avoiding the creation of numerous small dimensions.
- Attributes like gender (M/F), status flag (active/inactive), or order status (pending/shipped/delivered).

**Example of a Junk Dimension:**
Consider a sales data warehouse where you have various small attributes like `Promo_Flag`, `Urgency_Flag`, and `Seasonality_Flag`. Instead of creating separate dimensions for each flag, you consolidate them into a single junk dimension:

**Junk Dimension Table: `Dim_Junk`**

| Junk_Dim_Key | Promo_Flag | Urgency_Flag | Seasonality_Flag |
|--------------|------------|--------------|------------------|
| 1            | Yes        | High         | Summer           |
| 2            | No         | Low          | Winter           |
| 3            | Yes        | Medium       | Fall             |

**Fact Table Example: `Fact_Sales`**

| Order_ID | Date_Key | Product_Key | Customer_Key | Junk_Dim_Key |
|----------|----------|-------------|--------------|--------------|
| 1001     | 20230901 | 2001        | 3001         | 1            |
| 1002     | 20230901 | 2002        | 3002         | 2            |
| 1003     | 20230902 | 2003        | 3003         | 3            |

In this example, the `Junk_Dim_Key` in the `Fact_Sales` table references the `Dim_Junk` table, where various flags and attributes are stored.

### Degenerate Dimensions
- Degenerate Dimensions are dimensions that do not have their own dimension table but are instead stored as attributes in the fact table. 
- hey are typically used when the dimension attributes are not significant enough to warrant a separate dimension table.

**Examples and use cases:**
- Invoice Numbers: 
 - In a sales fact table, the invoice number can serve as a degenerate dimension. It uniquely identifies a transaction but does not require additional attributes beyond the fact table.

- Transaction IDs:
 - For financial transactions, transaction IDs can be degenerate dimensions, helping to trace and analyze individual transactions.


### Slowly Changing Dimensions
[Please refer this](https://github.com/rohish-zade/Python/blob/master/working_with_databases_and_ETL/scd_types.ipynb)


-------------

Fact table: measurement => salary => 200
Dimension table: context => time, employee