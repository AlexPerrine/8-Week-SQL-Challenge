
# Week 1 Challenge!

<img src='Dannys-Diner.png' alt="Danny's Diner Logo" width=auto height="700">
For more information about the <a href="https://8weeksqlchallenge.com/case-study-1/">week 1</a> challenge. 

### Introduction
This week we are looking at Danny's Diner, a Japanese restaurant which began in 2021. The diner needs help staying afloat so they asked me to help with a basic analysis using the limited data that has been gathered.

### Problem Statement
To help stay afloat we have been tasked with answering a few simple questions about the customers of the diner, especially about their visiting patterns, which items are their favorites and how much they have spent. The goal of Danny's Diner after the analysis is over with would be to have enough of an understanding of the customers to expand the existing loyalty program that is already in place.

### Data
Danny is proving me 3 datasets to use for the analysis
 - Sales
 - Menu
 - Members
Along with an entity relationship diagram (ERD henceforth).

<img src='ERD.png' alt="Entity Relationship Diagram for Week 1" width=auto height="500">

### Questions
Danny has provided me 10 questions he is seeking to get more information about regarding his customers and the business. To answer each question I will have the SQL script and the output of the the script.

1. What is the total amount each customer spent at the restaurant?

```sql
SELECT
  sales.customer_id AS customer,
  SUM(menu.price) AS total_paid
FROM dannys_diner.sales AS sales
JOIN dannys_diner.menu AS menu
ON sales.product_id = menu.product_id
GROUP BY 1
ORDER BY total_paid DESC
```

| customer | total\_paid |
| -------- | ----------- |
| A        | 76          |
| B        | 74          |
| C        | 36          |

1. How many days has each customer visited the restaurant?
2. What was the first item from the menu purchased by each customer?
3. What is the most purchased item on the menu and how many times was it purchased by all customers?
4. Which item was the most popular for each customer?
5. Which item was purchased first by the customer after they became a member?
6. Which item was purchased just before the customer became a member?
7. What is the total items and amount spent for each member before they became a member?
8.  If each $1 spent equates to 10 points and sushi has a 2x points multiplier - how many points would each customer have?
9.  In the first week after a customer joins the program (including their join date) they earn 2x points on all items, not just sushi - how many points do customer A and B have at the end of January?
