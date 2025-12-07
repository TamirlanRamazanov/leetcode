# №1. [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)
## Solution
```sql
SELECT *

FROM cinema

WHERE id % 2 = 1 AND description NOT LIKE 'boring'

ORDER BY rating desc;
```

## Result
Input

cinema =

| id  | movie      | description | rating |
| --- | ---------- | ----------- | ------ |
| 1   | War        | great 3D    | 8.9    |
| 2   | Science    | fiction     | 8.5    |
| 3   | irish      | boring      | 6.2    |
| 4   | Ice song   | Fantacy     | 8.6    |
| 5   | House card | Interesting | 9.1    |

Output

| id  | movie      | description | rating |
| --- | ---------- | ----------- | ------ |
| 5   | House card | Interesting | 9.1    |
| 1   | War        | great 3D    | 8.9    |

Expected

| id  | movie      | description | rating |
| --- | ---------- | ----------- | ------ |
| 5   | House card | Interesting | 9.1    |
| 1   | War        | great 3D    | 8.9    |

# №2. [1251. Average Selling Price](https://leetcode.com/problems/average-selling-price/)
## Solution
```sql
SELECT p.product_id,

ROUND(

COALESCE(

SUM(u.units * p.price ) / NULLIF(SUM(u.units), 0),

0),

2) as average_price

FROM prices p

LEFT JOIN UnitsSold u

ON p.product_id = u.product_id

AND u.purchase_date BETWEEN p.start_date and p.end_date

GROUP BY product_id
```

## Result
Input

Prices =

| product_id | start_date | end_date | price |
| ---------- | ---------- | ---------- | ----- | 
| 1 | 2019-02-17 | 2019-02-28 | 5 | 
| 1 | 2019-03-01 | 2019-03-22 | 20 | 
| 2 | 2019-02-01 | 2019-02-20 | 15 | 
| 2 | 2019-02-21 | 2019-03-31 | 30 |

UnitsSold =

| product_id | purchase_date | units |
| ---------- | ------------- | ----- |
| 1          | 2019-02-25    | 100   |
| 1          | 2019-03-01    | 15    |
| 2          | 2019-02-10    | 200   |
| 2          | 2019-03-22    | 30    |

Output

| product_id | average_price |
| ---------- | ------------- |
| 1          | 6.96          |
| 2          | 16.96         |

Expected

| product_id | average_price |
| ---------- | ------------- |
| 1          | 6.96          |
| 2          | 16.96         |

# №3. [1075. Project Employees I](https://leetcode.com/problems/project-employees-i/)
## Solution
```sql
SELECT project_id,

ROUND(SUM(e.experience_years)/ COUNT(p.project_id), 2) as average_years

FROM project p

LEFT JOIN employee e

ON p.employee_id = e.employee_id

GROUP BY (p.project_id)
```

## Result

Input

Project =

| project_id | employee_id |
| ---------- | ----------- |
| 1          | 1           |
| 1          | 2           |
| 1          | 3           |
| 2          | 1           |
| 2          | 4           |

Employee =

| employee_id | name   | experience_years |
| ----------- | ------ | ---------------- |
| 1           | Khaled | 3                |
| 2           | Ali    | 2                |
| 3           | John   | 1                |
| 4           | Doe    | 2                |

Output

| project_id | average_years |
| ---------- | ------------- |
| 1          | 2             |
| 2          | 2.5           |

Expected

| project_id | average_years |
| ---------- | ------------- |
| 1          | 2             |
| 2          | 2.5           |

# №4. [1633. Percentage of Users Attended a Contest](https://leetcode.com/problems/percentage-of-users-attended-a-contest/)
## Solution
```sql
SELECT r.contest_id,

ROUND(COUNT(r.user_id)/ (SELECT COUNT(*) FROM users) * 100, 2) AS percentage

FROM users u

  

LEFT JOIN register r

ON u.user_id = r.user_id

GROUP BY r.contest_id

ORDER BY percentage DESC, contest_id;
```

## Result

Input

Users =

| user_id | user_name |
| ------- | --------- |
| 6       | Alice     |
| 2       | Bob       |
| 7       | Alex      |

Register =

| contest_id | user_id |
| ---------- | ------- |
| 215        | 6       |
| 209        | 2       |
| 208        | 2       |
| 210        | 6       |
| 208        | 6       |
| 209        | 7       |

View more

Output

| contest_id | percentage |
| ---------- | ---------- |
| 208        | 100        |
| 209        | 100        |
| 210        | 100        |
| 215        | 66.67      |
| 207        | 33.33      |

Expected

| contest_id | percentage |
| ---------- | ---------- |
| 208        | 100        |
| 209        | 100        |
| 210        | 100        |
| 215        | 66.67      |
| 207        | 33.33      |

# №5. [1211. Queries Quality and Percentage](https://leetcode.com/problems/queries-quality-and-percentage/)
## Solution
```sql
SELECT query_name, ROUND(AVG(rating / position), 2) as quality,

ROUND(100* SUM(rating < 3) / COUNT(rating), 2) as poor_query_percentage

FROM queries

GROUP BY query_name
```

## Result

Input

Queries =

| query_name | result           | position | rating |
| ---------- | ---------------- | -------- | ------ |
| Dog        | Golden Retriever | 1        | 5      |
| Dog        | German Shepherd  | 2        | 5      |
| Dog        | Mule             | 200      | 1      |
| Cat        | Shirazi          | 5        | 2      |
| Cat        | Siamese          | 3        | 3      |
| Cat        | Sphynx           | 7        | 4      |

Output

| query_name | quality | poor_query_percentage |
| ---------- | ------- | --------------------- |
| Dog        | 2.5     | 33.33                 |
| Cat        | 0.66    | 33.33                 |

Expected

| query_name | quality | poor_query_percentage |
| ---------- | ------- | --------------------- |
| Dog        | 2.5     | 33.33                 |
| Cat        | 0.66    | 33.33                 |

# №6. [1193. Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/)
## Solution

```sql
SELECT

DATE_FORMAT(trans_date, "%Y-%m") as month

, country

, COUNT(*) as trans_count

, SUM(state = 'approved') as approved_count

, SUM(amount) as trans_total_amount

, SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) as approved_total_amount

FROM transactions

GROUP BY month, country;
```

## Result
Input

Transactions =

| id  | country | state    | amount | trans_date |
| --- | ------- | -------- | ------ | ---------- |
| 121 | US      | approved | 1000   | 2018-12-18 |
| 122 | US      | declined | 2000   | 2018-12-19 |
| 123 | US      | approved | 2000   | 2019-01-01 |
| 124 | DE      | approved | 2000   | 2019-01-07 |

Output

| month   | country | trans_count | approved_count | trans_total_amount | approved_total_amount |
| ------- | ------- | ----------- | -------------- | ------------------ | --------------------- |
| 2018-12 | US      | 2           | 1              | 3000               | 1000                  |
| 2019-01 | US      | 1           | 1              | 2000               | 2000                  |
| 2019-01 | DE      | 1           | 1              | 2000               | 2000                  |

Expected

| month   | country | trans_count | approved_count | trans_total_amount | approved_total_amount |
| ------- | ------- | ----------- | -------------- | ------------------ | --------------------- |
| 2018-12 | US      | 2           | 1              | 3000               | 1000                  |
| 2019-01 | US      | 1           | 1              | 2000               | 2000                  |
| 2019-01 | DE      | 1           | 1              | 2000               | 2000                  |


# №7.
## Solution
```sql
SELECT ROUND( 100 * SUM(order_date = customer_pref_delivery_date) / COUNT(*), 2)

as immediate_percentage

FROM (

SELECT d.*

FROM delivery d

JOIN (

SELECT customer_id, MIN(order_date) AS first_date

FROM delivery

GROUP BY customer_id

) t

ON d.customer_id = t.customer_id

AND d.order_date = t.first_date

) temp;
```

## Result

Input

Delivery =

| delivery_id | customer_id | order_date | customer_pref_delivery_date |
| ----------- | ----------- | ---------- | --------------------------- |
| 1           | 1           | 2019-08-01 | 2019-08-02                  |
| 2           | 2           | 2019-08-02 | 2019-08-02                  |
| 3           | 1           | 2019-08-11 | 2019-08-12                  |
| 4           | 3           | 2019-08-24 | 2019-08-24                  |
| 5           | 3           | 2019-08-21 | 2019-08-22                  |
| 6           | 2           | 2019-08-11 | 2019-08-13                  |

View more

Output

| immediate_percentage |
| -------------------- | 
| 50 |

Expected

| immediate_percentage |
| -------------------- |
| 50                   |

# №8.
## Solution
## Result