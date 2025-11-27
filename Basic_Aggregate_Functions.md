# №1 [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)
## Solution
SELECT *

FROM cinema

WHERE id % 2 = 1 AND description NOT LIKE 'boring'

ORDER BY rating desc;
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

# №2 [1251. Average Selling Price](https://leetcode.com/problems/average-selling-price/)
## Solution
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

# №3
## Solution
## Result
# №4
## Solution
## Result
# №5
## Solution
## Result
# №6
## Solution
## Result
# №7
## Solution
## Result
# №8
## Solution
## Result