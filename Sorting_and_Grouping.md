# №1. [2356. Number of Unique Subjects Taught by Each Teacher](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/)

## Solution:
```sql
SELECT teacher_id, COUNT(DISTINCT subject_id) as cnt

FROM teacher

GROUP BY teacher_id
```

## Result:

Input

Teacher =

| teacher_id | subject_id | dept_id |
| ---------- | ---------- | ------- |
| 1          | 2          | 3       |
| 1          | 2          | 4       |
| 1          | 3          | 3       |
| 2          | 1          | 1       |
| 2          | 2          | 1       |
| 2          | 3          | 1       |
| 2          | 4          | 1       |

View more

Output

| teacher_id | cnt |
| ---------- | --- |
| 1          | 2   |
| 2          | 4   |

Expected

| teacher_id | cnt |
| ---------- | --- |
| 1          | 2   |
| 2          | 4   |
# №2. [1141. User Activity for the Past 30 Days I](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/)

## Solution:

```sql
SELECT activity_date as day, COUNT(distinct user_id ) as active_users

FROM activity

WHERE activity_date BETWEEN '2019-06-28' AND '2019-07-27'

GROUP BY day
```

## Result:

Input

Activity =

| user_id | session_id | activity_date | activity_type |
| ------- | ---------- | ------------- | ------------- |
| 1       | 1          | 2019-07-20    | open_session  |
| 1       | 1          | 2019-07-20    | scroll_down   |
| 1       | 1          | 2019-07-20    | end_session   |
| 2       | 4          | 2019-07-20    | open_session  |
| 2       | 4          | 2019-07-21    | send_message  |
| 2       | 4          | 2019-07-21    | end_session   |

View more

Output

| day        | active_users |
| ---------- | ------------ |
| 2019-07-20 | 2            |
| 2019-07-21 | 2            |

Expected

| day | active_users |
| ---------- | ------------ |
| 2019-07-20 | 2 |
| 2019-07-21 | 2 |

# №3. [1070. Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/)

## Solution:

```sql
SELECT s.product_id, s.year as first_year, s.quantity, s.price

FROM Sales s

JOIN

    (SELECT product_id, MIN(year) as first_year

    FROM Sales

    GROUP BY product_id) t

    ON s.product_id = t.product_id AND s.year = t.first_year
```

## Result:

Input

Sales =

| sale_id | product_id | year | quantity | price |
| ------- | ---------- | ---- | -------- | ----- |
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |

Output

| product_id | first_year | quantity | price |
| ---------- | ---------- | -------- | ----- |
| 100        | 2008       | 10       | 5000  |
| 200        | 2011       | 15       | 9000  |

Expected

| product_id | first_year | quantity | price |
| ---------- | ---------- | -------- | ----- |
| 100        | 2008       | 10       | 5000  |
| 200        | 2011       | 15       | 9000  |
