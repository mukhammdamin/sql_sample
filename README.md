# My protfolio Project
A collection of my sample SQL files and Projects

# SQL Aggregate functions
-To combine multiple entries into a single ,summarised result
-Also here it is best if the database does this for us
## For this,we can tell the databese to aggregate the result
-Counting All entries (COUNT(*)):
### SELECT COUNT (*) FROM students

## Additional aggregate functions: 
▶ Maximum: SELECT MAX(age) FROM students
▶ Minimum: SELECT MIN(age) FROM students 
▶ Sum: SELECT SUM(age) FROM students 
▶ Average: SELECT AVG(age) FROM students

## Filtering with LIKE
▶ So far, we could only filter by an exact value 
▶ Sometimes, we want to perform a more complex search 
- For this, we can use the LIKE clause: 
▶ ... WHERE [column] LIKE [pattern] 
▶ Available placeholders in the pattern: 
▶ %: Represents zero, one or multiple characters 
▶ _: Represents exactly one character: 
- Example: 
▶ Can we find all students whose email addresses end with @gmail.com? 
▶ SELECT * FROM students WHERE email LIKE '%@gmail.com' 
▶ How many students do we have in our database, whose name starts with 'M'? 
▶ SELECT COUNT(*) FROM students WHERE firstname LIKE 'M%' 
▶ How many students do we have in our database, whose name starts with 'M', followed 
by exactly 2 more characters? 
▶ SELECT COUNT(*) FROM students WHERE firstname LIKE 'M__'

# THE BIG 6 IN SQL

### The Big 6 are the foundation clasuses in SQL queries

## SELECT grade_level ,AVG(gpa) AS avg_gpa  > Columns to display
## FROM students > Table to pull data from
## WHERE school_lunch = "Yes" > Criteria to filter the rows by
## GR0UP BY grade_level > Column to group the rows by
## HAVING avg_gpa < 3.3 > Criteria to filter the grouded rows by
## ORDER BY grade level; > Column to sort values

## learn about how to create teachers tabele 

## data cleaning transformation

Looking at the customer_orders table below, we can see that there are

In the exclusions column, there are missing/ blank spaces ' ' and null values.
In the extras column, there are missing/ blank spaces ' ' and null values.

CREATE TEMP TABLE customer_orders_temp AS
SELECT 
  order_id, 
  customer_id, 
  pizza_id, 
  CASE
	  WHEN exclusions IS null OR exclusions LIKE 'null' THEN ' '
	  ELSE exclusions
	  END AS exclusions,
  CASE
	  WHEN extras IS NULL or extras LIKE 'null' THEN ' '
	  ELSE extras
	  END AS extras,
	order_time
FROM pizza_runner.customer_orders;

## here we can Learn how many pizzas were ordered
SELECT COUNT(*)  AS pizza_order_count
FROM customer_order_temp 

## How many succesful oreder made from each deliveries 
SELECT
     RUNNER_ID 
     COUNT(ORDERD_ID) AS succesful_orders

## How many each type of pizzas delivered

SELECT 
  p.pizza_name, 
  COUNT(c.pizza_id) AS delivered_pizza_count
FROM #customer_orders AS c
JOIN #runner_orders AS r
  ON c.order_id = r.order_id
JOIN pizza_names AS p
  ON c.pizza_id = p.pizza_id
WHERE r.distance != 0
GROUP BY p.pizza_name;

## for each customer how many delivered pizzas were changed at least one time or how many pizzas are not changes.


SELECT 
  c.customer_id,
  SUM(
    CASE WHEN c.exclusions <> ' ' OR c.extras <> ' ' THEN 1
    ELSE 0
    END) AS at_least_1_change,
  SUM(
    CASE WHEN c.exclusions = ' ' AND c.extras = ' ' THEN 1 
    ELSE 0
    END) AS no_change
FROM #customer_orders AS c
JOIN #runner_orders AS r
  ON c.order_id = r.order_id
WHERE r.distance != 0
GROUP BY c.customer_id
ORDER BY c.customer_id;
the answer is customer 101 and 102 has it is own original pizzas 

## In this post, you'll learn how to do the following:

Write SQL queries to extract data from two or more databases
Use SQL dot commands to simplify tasks
Perform aggregation with GROUP BY and PARTITION BY commands
Use window functions to simplify complex SQL queries
Read SQL queries from file and send SQL query results to file
 Here I will learn today How to write queries with Sql and What kind of projectsa are the best from other Candidates

 ## What is the totla amojnt each customer spent at the resturant

 ## How many days each customer visited each resturant
  SELECT customer_id 
  COUNT (DISITNCT order_date ) AS visit_count
FROM dannys_dinner.sales
GROUP_BY customer_id
HERE is the answer of each task

## Customer A visited 4 times
    Customer B visited 6 times
	Customer C visited 2 times 
## Other DATA mODEL FOR  MOVIE database
1 task
## Movies released since 2024-01-01

Answer of each question
SELECT id,title,runtime 
FROM movie
WHERE release_date >= '2024-01-01'
## Let's see a practical example.

Here we want to see the number of playlists in the app to which the users added each song.

The main query returns two columns: the name of the song and the number of playlists to which users added it. It's the second column that demands a subquery. The subquery is necessary here because we have to match the track_id assigned to the playlist with the track_id in the track table and then count them for each track.


SELECT t.name,
    (SELECT 
         count(playlist_id)
    FROM playlist_track pt
    WHERE pt.track_id = t.track_id
    ) as number_of_playlists
FROM track t 
GROUP BY 1
ORDER BY number_of_playlists DESC
LIMIT 50

-- Top 10 movies (English)
select v.view_rank, m.title, v.hours_viewed, m.runtime, v.views, v.cumulative_weeks_in_top10
from view_summary v
inner join movie m on m.id = v.movie_id
where duration = 'WEEKLY'
  and end_date = '2025-06-29'
  and m.locale = 'en'
order by v.view_rank;

Top 10 movies English

select v view rank m title  v hours viewed ,m.runtime,v.cumulative_weeks_in_top10

from view summary v
inner join movies 

##The main objective of this project is to develop a comprehensive library management system that simplifies the management of books within a library. This system maintains a centralized database of books, including their details such as title, price, status, and the total number of books available. It streamlines the borrowing process and provides users with easy access to information, making it an efficient alternative to the traditional manual recording system.

The main objectiveof this project is develop and comrehense library managnment systme that simplifies the managnemet
of books within a library .This system maintains and helps for centralized 2 or 3 library in One place  with database of books ,including their details such as title name of the book,price  of the book ,status  and total number of books available.It streamline and connect all the  books in the one place fofr helping users and with easy access to information making it an efficent alternative to the tradiditonal manual recording systems

## which client has spent at least 100$ or more than this $in the store 

SELECT
    c.customer_id,
    round(sum(i.total), 2) as total
FROM customer c
INNER JOIN invoice i on c.customer_id = i.customer_id
GROUP BY c.customer_id
HAVING sum(i.total) > 100
ORDER BY 2 DESC


## Balanced tree clothing
1What was the total quantity sold for all products

2 What is the total generated revenue for all products before discounts

## What arethe top selling pruducts for each segments

WITH top_selling_cte AS ( 
  SELECT 
    product.segment_id,
    product.segment_name, 
    product.product_id,
    product.product_name,
    SUM(sales.qty) AS total_quantity,
    RANK() OVER (
      PARTITION BY segment_id 
      ORDER BY SUM(sales.qty) DESC) AS ranking
  FROM balanced_tree.sales
  INNER JOIN balanced_tree.product_details AS product
    ON sales.prod_id = product.product_id
  GROUP BY 
    product.segment_id, product.segment_name, product.product_id, product.product_name
)

SELECT 
  segment_id,
  segment_name, 
  product_id,
  product_name,
  total_quantity
FROM top_selling_cte
WHERE ranking = 1;

## Balanced tree clothingin sql

 SELECT 
 segment_id 
 segment_name 
 product_id
 product_name
 total_quantity
FROM top_selling_cte 
WHERE rankingv = 2:


## Here is the foodie fie projectplans

two Girls opens new shops which is named foodie fie
Here is the quesiton and solution In the 


##SELECT
  DATE_PART('month', start_date) AS month_date, -- Cast start_date as month in numerical format
  COUNT(sub.customer_id) AS trial_plan_subscriptions
FROM foodie_fi.subscriptions AS sub
JOIN foodie_fi.plans p
  ON s.plan_id = p.plan_id
WHERE s.plan_id = 0 -- Trial plan ID is 0
GROUP BY DATE_PART('month',start_date)
ORDER BY month_date;



## SELECT
DATE_PART (month, start_date )as month_date,--case start_dateas monthin numerical format
COUNT (sub.customer_id)AS trial_plan_subscription
    FROM foodie_fi.subscription AS sub
	JOIN foodie_fi plans p
ON s.plan_id= p.plan_id 
GROUP BY DATE_PART (month,start_date)


## Todays topic is 
Basics of SQL concepts Understanding Database and a table 
Insert sasmple data into the table 
Oerfirn bvasuc queries to retrive data 

## Next Important task is Filtering and Sorting Data 
1 Using WHERE clause for filtering 
2 Sorting results using ORDER BY 
3 Limiting results with LIMIT

## Next Important thing is Aggregate Function 
Using COUNT ,SUM,AVG ,MIN,MAX
Grouping data with GROUP BY 
Filtering groups with HAVING 

## NEXT one is JOINS 
1 Understanding different types of Joins ,INNER JOIN,LEFT JOIN,RIGHT JOIN ,FULL OUTER JOIN

## NEXT one is SUBQUERIES AND NESTED QUERIES
WRITING SUBQUERIS IN SELECT ,FROM, WHERE clauses


## Databease design and consantrains 

Understanding primary keys foreign keys unique consantrains and not null consantrains 
Apply unique and not null consantrains
Normalize given database shcema

## Advanced SQL Functions 

Case Statement in SQL
DML Function In SQL
Using string function 
Practice tasks : Write queries using string manipulation function


## After completing this lessons I need to Make a 3 or 4 Projects based on this Topics 

1 Topic card is Retail Project 
here I will do Create a simple database





