join `table2` with `table1` by matching project IDs and selecting the greatest `amendment_number` in `table2` that is still less than or equal to the `amendment_number` in `table1`. Here's the SQL code to achieve that:

```sql
proc sql;
   create table table3 as
   select t1.*, t2.column1, t2.column2
   from table1 as t1
   left join table2 as t2
   on t1.project_id = t2.project_id
   and t2.amendment_number = (
      select max(amendment_number)
      from table2
      where t2.project_id = table1.project_id
      and amendment_number <= t1.amendment_number
   );
quit;
```

In this code:

1. We start with a `LEFT JOIN` between `table1` (aliased as `t1`) and `table2` (aliased as `t2`) based on matching `project_id`.

2. The join condition includes a subquery that selects the maximum `amendment_number` from `table2` for the same `project_id` as in `table1`, but with the additional condition that the `amendment_number` in `table2` must be less than or equal to the `amendment_number` in `table1`.

This code will create a new table, `table3`, that contains all columns from `table1` and the specified columns from `table2`. The join ensures that for each row in `table1`, it associates the corresponding row from `table2` with the highest applicable `amendment_number`.
