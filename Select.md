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



