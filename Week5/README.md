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
    1. 

#### Data Exploration:
What day of the week is used for each week_date value?
What range of week numbers are missing from the dataset?
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