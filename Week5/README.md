# Week 5 Challenge!

<img src='data-mart.png' alt="Mart Logo" width=auto height="700">
For more information about the <a href="https://8weeksqlchallenge.com/case-study-5/">week 5</a> challenge. 

### Introduction
In June, large scale supply changes were made at Data Mart. All products now use sustainable packaging methods in every single step from the farm to customer. Danny needs help to quantify the impacts of this change on the sales performance.

### Problem Statement
Danny has 3 key questions he wants us to help solve.
    - What was the quantifiable impact of the changes introduced?
    - Which platform, region, segment and customer types were the most impacted by this change?
    - What can we do about future introductions of similar sustainability updates to the business to minimize impact on sales?

### Data
The data in this study also needs cleaning prior to being able to analyze the data.
Steps taken to clean the data:
    1. Convert the week_date to a DATE format
    2. Add a week_number as the second column for each week_date value
    3. Add a month_number with the calendar month for each week_date value as the 3rd column
    4. Add a calendar_year column as the 4th coulmn containing either 2018,2019,2020
    5. Add a column called age_band after the original segment using the following
        - 1 -> Young Adult
        - 2 -> Middle Aged
        - 3 or 4 -> Retirees
    6. Add a demographic column using the following segment values
        - C -> Couples
        - F -> Families
    7. Ensure all null string values with an "Unknown" string in the original segment column as well as the new age_band and demographics
    8. Generate a new avg_transaction column as the sales value divided by transactions rounded to 2 decimal places.

```sql
DROP TABLE IF EXISTS data_mart.clean_weekly_sales;
CREATE TABLE data_mart.clean_weekly_sales AS
SELECT 
  TO_DATE(week_date, 'DD/MM/YY') AS week_date,
  DATE_PART('week', TO_DATE(week_date, 'DD/MM/YY')) AS week_number,
  DATE_PART('mon', TO_DATE(week_date, 'DD/MM/YY')) AS month_number,
  DATE_PART('year', TO_DATE(week_date, 'DD/MM/YY')) AS year,
  region,
  platform,
  CASE 
    WHEN left(segment, 1) = '1' THEN 'Young Adult'
    WHEN left(segment, 1) = '2' THEN 'Middle Aged'
    WHEN left(segment, 1) IN('3','4') THEN 'Retirees'
    ELSE 'Unknown'
  END AS age_band,
  CASE
    WHEN left(segment, 1) = 'C' THEN 'Couples'
    WHEN left(segment, 1) = 'F' THEN 'Families'
    ELSE 'Unknown'
  END AS demographics,
  customer_type,
  transactions,
  sales,
  ROUND(sales / transactions, 2) as avg_transaction
FROM data_mart.weekly_sales;
```

I will be using the newly constructed cleaned table for the following analysis
#### Data Exploration:
1. What day of the week is used for each week_date value?
```sql
SELECT 
  TO_CHAR(week_date,'Day') AS day_of_week
FROM data_mart.clean_weekly_sales
LIMIT 1
```
| day\_of\_week |
| ------------- |
| Monday        |

2. What range of week numbers are missing from the dataset?
How many total transactions were there for each year in the dataset?
What is the total sales for each region for each month?
What is the total count of transactions for each platform
What is the percentage of sales for Retail vs Shopify for each month?
What is the percentage of sales by demographic for each year in the dataset?
Which age_band and demographic values contribute the most to Retail sales?
Can we use the avg_transaction column to find the average transaction size for each year for Retail vs Shopify? If not - how would you calculate it instead?

#### Before & After Analysis
This technique is usually used when we inspect an important event and want to inspect the impact before and after a certain point in time.

Taking the week_date value of 2020-06-15 as the baseline week where the Data Mart sustainable packaging changes came into effect.

We would include all week_date values for 2020-06-15 as the start of the period after the change and the previous week_date values would be before

Using this analysis approach - answer the following questions:

What is the total sales for the 4 weeks before and after 2020-06-15? What is the growth or reduction rate in actual values and percentage of sales?
What about the entire 12 weeks before and after?
How do the sale metrics for these 2 periods before and after compare with the previous years in 2018 and 2019?