# Home_Sales

# Calculation of Key metrics and Runtime Comparison - Home Sales data 

The Home Sales project involves finding 4 key mertics using queries on a Temp table of the original data due to use of spark and recording the runtime for the last qyery and then calculating and recording the runtime for the last key metrics query after using optimization techniques like caching, partitioning and parquetting. The performance based on the  uncached and cached runtimes was compared and summarized.


## Acknowledgements

 - Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.


## Key Metrics calculation using SparkSQL on the Temporary Table, home_sales:

- Average price for a four-bedroom house sold for each year.
The query returned 4 records for the years 2019 to 2022. Results were rounded to two decimal places.

- Average price of a home for each year the home was built.
The query returned 8 records for the date_built from 2010 to 2017. Results were rounded to two decimal places.

- Average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet.
The query returned 8 records for the date_built from 2010 to 2017. Results were rounded to two decimal places.

- Average price of a home per "view" rating having an average home price greater than or equal to $350,000? 
The query returned the qualifying records based on the view ratings in descending order. Results were rounded to two decimal places.

Additionally, the run time for this last query on the uncached table was recorded: uncached runtime = 1.2288596630096436 seconds


## Key Metric calculation after using Optimization Techniques

### Cached and verified temporary table home_sales.

- Used the last query to calculate the key metric of the average price of a home per "view" rating having an average home price greater than or equal to $350,000. Results were rounded to two decimal places and in descending order of the view ratings.

Additionally, the runtime of this cached run was calculated: cached runtime = 0.6402144432067871 seconds.

#### Runtime Comparison
uncached runtime = 1.2288596630096436 seconds

cached runtime = 0.6402144432067871 seconds

### Partitioned by the "date_built" field on the formatted parquet home sales data and created a temporary table for the parquet data.

- Used the last query to calculate the key metric of the average price of a home per "view" rating having an average home price greater than or equal to $350,000. Results were rounded to two decimal places and in descending order of the view ratings.
Additionally, the runtime of this cached run was calculated: cached runtime = 0.9457533359527588 seconds.

#### Runtime Comparison Post Partitioning
uncached runtime = 1.2288596630096436 seconds

cached runtime = 0.9457533359527588 seconds


## Summary of Runtime Performance Comparison:

- Caching significantly reduces the query runtime from 1.2289 seconds (uncached) to 0.6402 seconds, improving query performance by roughly 48%.
- Partitioning by date_built did not significantly improve the runtime for the uncached query. However, after partitioning, the cached query runtime slightly increased to 0.9458 seconds, which may indicate some additional overhead related to partitioning the data, but this overhead is minimal and still represents an improvement over the uncached runtime.  

