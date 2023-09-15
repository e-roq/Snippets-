# Join Table By Identifier in SQL

Use a LEFT JOIN to add columns from another table where the identifier is the same. The LEFT JOIN command returns all the rows from the left table and the matched rows from the right table. If no match is found, then the result is NULL on the right side.

This command will return all rows from table1 and the matching rows from table2 based on the identifier. If there is no match found in table2, NULL will be returned for columnToAdd.

If you want to add multiple columns from table2, you can do so by listing them after table2. in the SELECT statement, separated by commas:

```SQL
SELECT table1.*, table2.columnToAdd1, table2.columnToAdd2, table2.columnToAdd3
FROM table1
LEFT JOIN table2 
ON table1.identifier = table2.identifier;
```

Replace columnToAdd1, columnToAdd2, and columnToAdd3 with the names of the columns you want to add from table2 to table1