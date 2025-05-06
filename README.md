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
🔗[570. Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT name
FROM Employee
WHERE id IN (
    SELECT managerId
    FROM Employee
    WHERE managerId IS NOT NULL
    GROUP BY managerId
    HAVING COUNT(*) >= 5
);

```

🔗[1934. Confirmation Rate](https://leetcode.com/problems/confirmation-rate/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT 
    s.user_id,
    ROUND(
        IFNULL(SUM(c.action = 'confirmed') / COUNT(c.action), 0), 
        2
    ) AS confirmation_rate
FROM 
    Signups s
LEFT JOIN 
    Confirmations c ON s.user_id = c.user_id
GROUP BY 
    s.user_id;

```

🔗[620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT * 
FROM Cinema 
WHERE (id mod 2 != 0) AND (description != 'boring')
ORDER BY rating DESC;

```
🔗[1251. Average Selling Price](https://leetcode.com/problems/average-selling-price/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT 
    p.product_id,
    ROUND(SUM(u.units * p.price) / SUM(u.units), 2) AS average_price
FROM 
    Prices p
JOIN 
    UnitsSold u 
    ON p.product_id = u.product_id
    AND u.purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY 
    p.product_id
UNION
SELECT 
    p.product_id,
    0 AS average_price
FROM 
    Prices p
WHERE 
    p.product_id NOT IN (
        SELECT DISTINCT product_id FROM UnitsSold
    );

```
🔗[1517. Find Users With Valid E-Mails](https://leetcode.com/problems/find-users-with-valid-e-mails/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT user_id, name, mail
FROM Users
WHERE mail REGEXP '^[a-zA-Z][a-zA-Z0-9_.-]*@leetcode\\.com$';


```
🔗[1327. List the Products Ordered in a Period](https://leetcode.com/problems/list-the-products-ordered-in-a-period/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
# Write your MySQL query statement below
SELECT p.product_name,sum(o.unit) as unit
FROM Products p 
JOIN Orders o ON p.product_id =o.product_id 
WHERE o.order_date BETWEEN '2020-02-01' AND '2020-02-29'
GROUP BY p.product_id
HAVING sum(o.unit) >=100; 

```
🔗[1484. Group Sold Products By The Date](https://leetcode.com/problems/group-sold-products-by-the-date/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT 
    sell_date,
    COUNT(DISTINCT product) AS num_sold,
    GROUP_CONCAT(DISTINCT product ORDER BY product SEPARATOR ',') AS products
FROM Activities
GROUP BY sell_date
ORDER BY sell_date;


```
🔗[1527. Patients With a Condition](https://leetcode.com/problems/patients-with-a-condition/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT patient_id, patient_name, conditions
FROM Patients
WHERE conditions REGEXP '(^| )DIAB1';


```
🔗[1667. Fix Names in a Table](https://leetcode.com/problems/fix-names-in-a-table/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT 
    user_id,
    CONCAT(UPPER(LEFT(name, 1)), LOWER(SUBSTRING(name, 2))) AS name
FROM Users
ORDER BY user_id;

```
🔗[1731. The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
# Write your MySQL query statement below
SELECT 
    e.employee_id,
    e.name,
    COUNT(r.employee_id) AS reports_count,
    ROUND(AVG(r.age)) AS average_age
FROM Employees e
JOIN Employees r
    ON e.employee_id = r.reports_to
GROUP BY e.employee_id, e.name
ORDER BY e.employee_id;


```
🔗[1789. Primary Department for Each Employee](https://leetcode.com/problems/primary-department-for-each-employee/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
SELECT employee_id, department_id
FROM Employee
WHERE primary_flag = 'Y'
   OR employee_id IN (
        SELECT employee_id
        FROM Employee
        GROUP BY employee_id
        HAVING COUNT(*) = 1
   );


```
🔗[]()
```sql


```
🔗[]()
```sql


```
🔗[]()
```sql


```
🔗[]()
```sql


```
🔗[]()
```sql


```
