# LeetCode SQL 50 – Solutions

My proposed Solutions for the SQL 50 Study Plan on LeetCode.

---

🔗 [197. Rising Temperature](https://leetcode.com/problems/rising-temperature/description/?envType=study-plan-v2&envId=top-sql-50)

```sql

SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON w1.recordDate = DATE_ADD(w2.recordDate, INTERVAL 1 DAY)
WHERE w1.temperature > w2.temperature;

```

🔗[176. Second Highest Salary](https://leetcode.com/problems/second-highest-salary/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT 
  (SELECT DISTINCT salary 
   FROM Employee 
   ORDER BY salary DESC 
   LIMIT 1 OFFSET 1) AS SecondHighestSalary;

;
```
