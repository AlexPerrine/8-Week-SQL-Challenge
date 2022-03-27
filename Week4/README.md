# Week 4 Challenge!

<img src='bank.png' alt="Bank Logo" width=auto height="700">
For more information about the <a href="https://8weeksqlchallenge.com/case-study-4/">week 4</a> challenge. 

### Introduction
There is a new wave in the financial industry called Neo-Banks, new aged digital only banks. Data Bank runs just like any other digital bank, but it isn't only for banking activities, they also have the world's most secture distributed data storage platform.

### Problem Statement
Danny has asked us to calculate different metrics, growth and helping the business analyze their data in a smarter way to better forecast and plan their future developments.

### Data
#### Table 1: Regions
The data runs off a network of nodes where both money and data is stored across the globe. Think if these nodes as a bank branch/store that exists around the world.
#### Table 2: Customer Nodes
Customers are randomly distributed across the nodes according to their region. The distribution changes frequently to reduce the risk of hackers.
#### Table 3: Customer Transactions
This stores all customer deposits, withdrawls and purchases made using their Data Bank debit card.

Along with an ERD.

<img src='week4-ERD.png' alt="Entity Relationship Diagram for Week 4" width=auto height="400">

### Questions

#### Customer Nodes Exploration
How many unique nodes are there on the Data Bank system?
What is the number of nodes per region?
How many customers are allocated to each region?
How many days on average are customers reallocated to a different node?
What is the median, 80th and 95th percentile for this same reallocation days metric for each region?

#### Customer Transactions
What is the unique count and total amount for each transaction type?
What is the average total historical deposit counts and amounts for all customers?
For each month - how many Data Bank customers make more than 1 deposit and either 1 purchase or 1 withdrawal in a single month?
What is the closing balance for each customer at the end of the month?
What is the percentage of customers who increase their closing balance by more than 5%?
