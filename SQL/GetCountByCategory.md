
To get the count of one column based on the categories of another column in SQL, you can use the GROUP BY clause along with the COUNT function. 

```SQL
SELECT Column1, Column2, COUNT(*) as Count
FROM your_table
GROUP BY Column1, Column2;
```