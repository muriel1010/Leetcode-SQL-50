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


```
🔗[196. Delete Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
DELETE FROM Person
WHERE id NOT IN (
    SELECT * FROM (
        SELECT MIN(id)
        FROM Person
        GROUP BY email
    ) AS sub
);
```

🔗[1581. Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT customer_id,count(*) as count_no_trans
from Visits V 
LEFT JOIN Transactions T ON V.visit_id=T.visit_id
WHERE  T.transaction_id is null
GROUP BY customer_id;
```
