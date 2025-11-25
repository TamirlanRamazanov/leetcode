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
