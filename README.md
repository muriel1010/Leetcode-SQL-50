# LeetCode SQL 50 – Solutions

My proposed Solutions for the SQL 50 Study Plan on LeetCode.

---

🔗 [197. Rising Temperature](https://leetcode.com/problems/rising-temperature/description/?envType=study-plan-v2&envId=top-sql-50)

```sql

  select id 
from(
    select id,temperature,
    lag(temperature)over(order by recordDate asc ) as prev_temp
    from weather
)sub
where sub.temperature>sub.prev_temp';
```

🔗[197. Rising Temperature](https://leetcode.com/problems/second-highest-salary/description/?envType=study-plan-v2&envId=top-sql-50)
```sql
kkkkkkkkkkkkkkk
;
```
