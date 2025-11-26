# №1 [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)
## Solution
SELECT *

FROM cinema

WHERE id % 2 = 1 AND description NOT LIKE 'boring'

ORDER BY rating desc;
## Result
Input

cinema =

| id | movie | description | rating | | -- | ---------- | ----------- | ------ | | 1 | War | great 3D | 8.9 | | 2 | Science | fiction | 8.5 | | 3 | irish | boring | 6.2 | | 4 | Ice song | Fantacy | 8.6 | | 5 | House card | Interesting | 9.1 |

Output

| id | movie | description | rating | | -- | ---------- | ----------- | ------ | | 5 | House card | Interesting | 9.1 | | 1 | War | great 3D | 8.9 |

Expected

| id | movie | description | rating | | -- | ---------- | ----------- | ------ | | 5 | House card | Interesting | 9.1 | | 1 | War | great 3D | 8.9 |
# №2
## Solution
## Result
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