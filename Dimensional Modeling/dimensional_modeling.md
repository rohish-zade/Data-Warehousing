## what is Dimension Modeling?

- Dimensional data modeling is a design technique used in data warehousing to structure data in a way that is optimized for querying and reporting.
- It organizes data into facts and dimensions, creating a user-friendly model that facilitates fast retrieval of data for analytical purposes. 
- This approach simplifies complex data and is particularly useful for business intelligence (BI) and decision-making processes.


### Four steps of Dimensional Modeling design process:

1. Gather business requirement's (usability, performance):
 - what does your business do?(retail, real estate, insurance, banking, etc)
 - what measurement you want to analyze?
 - how does your current operational data looks like?

2. Identify Granularity(declare the grain)
- Grain mean the level of details available with the fact table.
- Basically this means what a single record in the fact table shows.
- Designed from the lowest possible grains

- Example: Consider we have a below fact table, firt requirement is to find the sales happened on the November 20th. We can easily find out the sales for that day the as fact table contains the necessary details to get that 
- ![](https://github.com/rohish-zade/data-warehousing/blob/master/Dimensional%20Modeling/images/fact-table-1.png)
- Now, the requirement is to find out the which customer pruchased which products on 20th November 20th. there is no way we can find out this as fact table doesn't contain any product details.
- Now consider the below updated fact table with more atomic grain which has product details. Not its easy to get the answer for second requirement as well.
- ![](https://github.com/rohish-zade/data-warehousing/blob/master/Dimensional%20Modeling/images/fact-table-2.png)



3. 

Fact table: measurement => salary => 200
Dimension table: context => time, employee