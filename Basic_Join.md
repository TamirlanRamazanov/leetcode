# №1. [1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/)
## Solution
```sql
SELECT uni.unique_id, em.name
FROM Employees em
LEFT JOIN EmployeeUNI uni
ON em.id = uni.id
```

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
```sql
SELECT p.product_name, s.year, s.price

FROM sales s

LEFT JOIN product p

ON p.product_id = s.product_id
```

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
```sql
SELECT v.customer_id,

COUNT(v.visit_id) as count_no_trans

FROM visits v

LEFT JOIN transactions t

ON v.visit_id = t.visit_id

WHERE t.transaction_id IS NULL

GROUP BY v.customer_id;
```

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
```sql
SELECT a.id as Id

FROM weather a

JOIN weather b

ON a.recordDate = b.recordDate + 1

WHERE a.temperature > b.temperature
```

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
```sql
SELECT e.machine_id,

ROUND( AVG(e.timestamp - s.timestamp), 3) AS processing_time

FROM activity e

JOIN activity s

ON e.machine_id = s.machine_id

AND e.process_id = s.process_id

WHERE e.activity_type = 'end' AND s.activity_type = 'start'

GROUP BY (e.machine_id);
```

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


# №6. [577. Employee Bonus](https://leetcode.com/problems/employee-bonus/)

## Solution
```sql
SELECT e.name, b.bonus

FROM employee e

LEFT JOIN bonus b

ON e.empId = b.empId

WHERE b.bonus IS NULL OR bonus < 1000;
```

## Result 
Input

Employee =

| empId | name   | supervisor | salary |
| ----- | ------ | ---------- | ------ |
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |

Bonus =

| empId | bonus |
| ----- | ----- |
| 2     | 500   |
| 4     | 2000  |

Output

| name | bonus |
| ---- | ----- |
| Brad | null  |
| John | null  |
| Dan  | 500   |

Expected

| name | bonus |
| ---- | ----- |
| Brad | null  |
| John | null  |
| Dan  | 500   |

# №7.  [1280. Students and Examinations](https://leetcode.com/problems/students-and-examinations/)

## Solution
```sql
SELECT st.student_id, st.student_name, sub.subject_name, COUNT(e.student_id) as attended_exams

FROM students st

CROSS JOIN subjects sub

LEFT JOIN examinations e

ON e.subject_name = sub.subject_name

AND st.student_id = e.student_id

GROUP BY st.student_id, sub.subject_name

ORDER BY st.student_id, sub.subject_name;
```

## Result
Input

Students =

| student_id | student_name |
| ---------- | ------------ |
| 1          | Alice        |
| 2          | Bob          |
| 13         | John         |
| 6          | Alex         |

Subjects =

| subject_name |
| ------------ |
| Math         |
| Physics      |
| Programming  |

Examinations =

| student_id | subject_name |
| ---------- | ------------ |
| 1          | Math         |
| 1          | Physics      |
| 1          | Programming  |
| 2          | Programming  |
| 1          | Physics      |
| 1          | Math         |

View more

Output

| student_id | student_name | subject_name | attended_exams |
| ---------- | ------------ | ------------ | -------------- |
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |

View more

Expected

| student_id | student_name | subject_name | attended_exams |
| ---------- | ------------ | ------------ | -------------- |
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |

# №8. [570. Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)

## Solution
```sql
SELECT m.name

FROM employee e

JOIN employee m

ON e.managerId = m.id

GROUP BY e.managerId

HAVING COUNT(e.managerId) >= 5;
```

## Result

Input

Employee =

| id  | name  | department | managerId |
| --- | ----- | ---------- | --------- |
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |

Output

| name |
| ---- |
| John |

Expected

| name |
| ---- |
| John |


# №9. [1934. Confirmation Rate](https://leetcode.com/problems/confirmation-rate/)
# Solution:
```sql 
SELECT s.user_id,

ROUND(
	IFNULL( 
		SUM(CASE WHEN action = 'confirmed' THEN 1 ELSE 0 END) / COUNT(action), 
          0), 
	2)
as confirmation_rate

FROM signups s

LEFT JOIN confirmations c

ON s.user_id = c.user_id

GROUP BY s.user_id;
```

## Result
Input

Signups =

| user_id | time_stamp          |
| ------- | ------------------- |
| 3       | 2020-03-21 10:16:13 |
| 7       | 2020-01-04 13:57:59 |
| 2       | 2020-07-29 23:09:44 |
| 6       | 2020-12-09 10:39:37 |

Confirmations =

| user_id | time_stamp          | action    |
| ------- | ------------------- | --------- |
| 3       | 2021-01-06 03:30:46 | timeout   |
| 3       | 2021-07-14 14:00:00 | timeout   |
| 7       | 2021-06-12 11:57:29 | confirmed |
| 7       | 2021-06-13 12:58:28 | confirmed |
| 7       | 2021-06-14 13:59:27 | confirmed |
| 2       | 2021-01-22 00:00:00 | confirmed |

View more

Output

| user_id | confirmation_rate |
| ------- | ----------------- |
| 3       | 0                 |
| 7       | 1                 |
| 2       | 0.5               |
| 6       | 0                 |

Expected

| user_id | confirmation_rate |
| ------- | ----------------- |
| 6       | 0                 |
| 3       | 0                 |
| 7       | 1                 |
| 2       | 0.5               |