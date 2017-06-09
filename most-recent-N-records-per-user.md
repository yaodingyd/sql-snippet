### Problem
If I want to get the most, say 5 records for each user, or per group in one table, or have a job that delete all except the 5 latest records.

### Solution

To delete 

```sql
select *
from table
where id not in (
  select t1.id
  from table t1
  join table t2
    on t1.date >= t2.date
    and t1.user_id = t2.user_id
    group by t1.user_id, t1.name
    having count(*) >= 2
  )
```

### References
1. [http://www.sql-ex.com/help/select16.php](http://www.sql-ex.com/help/select16.php)
