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
- Qualitative and transactional data (profit, revenue).
- Can be aggregated.

### Dimension Table
- Contain descriptive data that provides context to the facts, such as product details, customer information, time periods, etc.

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



Fact table: measurement => salary => 200
Dimension table: context => time, employee