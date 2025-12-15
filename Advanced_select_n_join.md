# №1.  [1731. The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/)

## Solution:

SELECT

r.employee_id,

r.name,

COUNT(e.employee_id) AS reports_count,

ROUND(AVG(e.age)) AS average_age

FROM employees e

JOIN employees r

ON e.reports_to = r.employee_id

GROUP BY r.employee_id

ORDER BY r.employee_id;

## Result: 

Case 1:

Input

Employees =

| employee_id | name    | reports_to | age |
| ----------- | ------- | ---------- | --- |
| 9           | Hercy   | null       | 43  |
| 6           | Alice   | 9          | 41  |
| 4           | Bob     | 9          | 36  |
| 2           | Winston | null       | 37  |

Output

| employee_id | name | reports_count | average_age |
| ----------- | ----- | ------------- | ----------- |
| 9 | Hercy | 2 | 39 |

Expected

| employee_id | name | reports_count | average_age |
| ----------- | ----- | ------------- | ----------- |
| 9 | Hercy | 2 | 39 |

Case 2:
Input

Employees =

| employee_id | name    | reports_to | age |
| ----------- | ------- | ---------- | --- |
| 1           | Michael | null       | 45  |
| 2           | Alice   | 1          | 38  |
| 3           | Bob     | 1          | 42  |
| 4           | Charlie | 2          | 34  |
| 5           | David   | 2          | 40  |
| 6           | Eve     | 3          | 37  |
| 7           | Frank   | null       | 50  |
| 8           | Grace   | null       | 48  |

Output

| employee_id | name | reports_count | average_age |
| ----------- | ------- | ------------- | ----------- |
| 1 | Michael | 2 | 40 |
| 2 | Alice | 2 | 37 |
| 3 | Bob | 1 | 37 |

Expected

| employee_id | name | reports_count | average_age |
| ----------- | ------- | ------------- | ----------- |
| 1 | Michael | 2 | 40 |
| 2 | Alice | 2 | 37 |
| 3 | Bob | 1 | 37 |


# №2.  [1789. Primary Department for Each Employee](https://leetcode.com/problems/primary-department-for-each-employee/)

## Solution:

```sql

SELECT

	employee_id,

	CASE

		WHEN COUNT(*) = 1 THEN MAX(department_id)

		ELSE MAX(CASE WHEN primary_flag = 'Y' THEN department_id END)

	END AS department_id

FROM employee

GROUP BY employee_id

```


## Result: 

Input

Employee =

| employee_id | department_id | primary_flag |
| ----------- | ------------- | ------------ |
| 1 | 1 | N |
| 2 | 1 | Y |
| 2 | 2 | N |
| 3 | 3 | N |
| 4 | 2 | N |
| 4 | 3 | Y |
| 4 | 4 | N |

Output

| employee_id | department_id |
| ----------- | ------------- |
| 1 | 1 |
| 2 | 1 |
| 3 | 3 |
| 4 | 3 |

Expected

| employee_id | department_id |
| ----------- | ------------- |
| 1           | 1             |
| 2           | 1             |
| 3           | 3             |
| 4           | 3             |
