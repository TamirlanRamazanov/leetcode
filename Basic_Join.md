# №1. [1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/)
## Solution

 SELECT uni.unique_id, em.name

FROM Employees em

LEFT JOIN EmployeeUNI uni

ON em.id = uni.id

## Result

Input

Employees =

| id  | name     |
| --- | -------- |
| 1   | Alice    |
| 7   | Bob      |
| 11  | Meir     |
| 90  | Winston  |
| 3   | Jonathan |

EmployeeUNI =

| id  | unique_id |
| --- | --------- |
| 3   | 1         |
| 11  | 2         |
| 90  | 3         |

Output

| unique_id | name     |
| --------- | -------- |
| null      | Alice    |
| 1         | Jonathan |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |

Expected

| unique_id | name     |
| --------- | -------- |
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |

# №2. [1068. Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/)
## Solution
SELECT p.product_name, s.year, s.price

FROM sales s

LEFT JOIN product p

ON p.product_id = s.product_id

## Result
 
Input

Sales =

| sale_id | product_id | year | quantity | price |
| ------- | ---------- | ---- | -------- | ----- |
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |

Product =

| product_id | product_name |
| ---------- | ------------ |
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |

Output

| product_name | year | price |
| ------------ | ---- | ----- |
| Nokia        | 2008 | 5000  |
| Nokia        | 2009 | 5000  |
| Apple        | 2011 | 9000  |

Expected

| product_name | year | price |
| ------------ | ---- | ----- |
| Nokia        | 2009 | 5000  |
| Nokia        | 2008 | 5000  |
| Apple        | 2011 | 9000  |

# №3. [1581. Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/)

## Solution
SELECT v.customer_id,

COUNT(v.visit_id) as count_no_trans

FROM visits v

LEFT JOIN transactions t

ON v.visit_id = t.visit_id

WHERE t.transaction_id IS NULL

GROUP BY v.customer_id;
## Result

Input

Visits =

| visit_id | customer_id |
| -------- | ----------- |
| 1        | 23          |
| 2        | 9           |
| 4        | 30          |
| 5        | 54          |
| 6        | 96          |
| 7        | 54          |

View more

Transactions =

| transaction_id | visit_id | amount |
| -------------- | -------- | ------ |
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |

Output

| customer_id | count_no_trans |
| ----------- | -------------- |
| 30          | 1              |
| 54          | 2              |
| 96          | 1              |

Expected

| customer_id | count_no_trans |
| ----------- | -------------- |
| 30          | 1              |
| 96          | 1              |
| 54          | 2              |

# №4. [197. Rising Temperature](https://leetcode.com/problems/rising-temperature/)

## Solution

SELECT a.id as Id

FROM weather a

JOIN weather b

ON a.recordDate = b.recordDate + 1

WHERE a.temperature > b.temperature

## Result

Input

Weather =

| id | recordDate | temperature |
| -- | ---------- | ----------- | 
| 1 | 2015-01-01 | 10 |
| 2 | 2015-01-02 | 25 |
| 3 | 2015-01-03 | 20 |
| 4 | 2015-01-04 | 30 |

Output

| id  |
| --- |
| 2   |
| 4   |

Expected

| Id  |
| --- |
| 2   |
| 4   |

# №5. [1661. Average Time of Process per Machine](https://leetcode.com/problems/average-time-of-process-per-machine/)

## Solution 
SELECT e.machine_id,

ROUND( AVG(e.timestamp - s.timestamp), 3) AS processing_time

FROM activity e

JOIN activity s

ON e.machine_id = s.machine_id

AND e.process_id = s.process_id

WHERE e.activity_type = 'end' AND s.activity_type = 'start'

GROUP BY (e.machine_id);

## Result
Input

Activity =

| machine_id | process_id | activity_type | timestamp |
| ---------- | ---------- | ------------- | --------- |
| 0          | 0          | start         | 0.712     |
| 0          | 0          | end           | 1.52      |
| 0          | 1          | start         | 3.14      |
| 0          | 1          | end           | 4.12      |
| 1          | 0          | start         | 0.55      |
| 1          | 0          | end           | 1.55      |

View more

Output

| machine_id | processing_time |
| ---------- | --------------- |
| 0          | 0.894           |
| 1          | 0.995           |
| 2          | 1.456           |

Expected

| machine_id | processing_time |
| ---------- | --------------- |
| 0          | 0.894           |
| 1          | 0.995           |
| 2          | 1.456           |
