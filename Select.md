# [1757. Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/)
## Solution:
SELECT product_id

FROM products

WHERE low_fats = 'Y' AND recyclable = 'Y'
## Result:
Input

Products =

| product_id | low_fats | recyclable |
| ---------- | -------- | ---------- |
| 0          | Y        | N          |
| 1          | Y        | Y          |
| 2          | N        | Y          |
| 3          | Y        | Y          |
| 4          | N        | N          |
Output

| product_id |
| ---------- |
| 1          |
| 3          |

Expected

| product_id |
| ---------- |
| 1          |
| 3          |

# [584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/)
## Solution 
SELECT name

FROM customer

WHERE referee_id != 2 OR referee_id IS NULL;

## Result
Input
Customer =

| id | name | referee_id |
| -- | ---- | ---------- |
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |

Output

| name |
| ---- |
| Will |
| Jane |
| Bill |
| Zack |
Expected

| name |
| ---- |
| Will |
| Jane |
| Bill |
| Zack |

# [595. Big Countries](https://leetcode.com/problems/big-countries/)

## Solution
SELECT name, population, area

FROM world

WHERE population >= 25000000 OR area >= 3000000;

## Result

Input

World =

| name        | continent | area    | population | gdp          |
| ----------- | --------- | ------- | ---------- | ------------ |
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |

Output

| name        | population | area    |
| ----------- | ---------- | ------- |
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |

Expected

| name        | population | area    |
| ----------- | ---------- | ------- |
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |


