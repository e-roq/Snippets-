
```SQL
-- Way to filter out all but the most recent ammendment number

-- You can create a temporary table that stores the highest version numbers 
-- for each unique value in product_num.
CREATE TEMPORARY TABLE temp_table AS
    SELECT product_num, MAX(ammendment_num) AS highest_version
    FROM table_name
    GROUP BY product_num;

-- Remove all rows from original table where the product number 
-- and maximum ammendment number do not exist
DELETE FROM table_name
    WHERE (product_num, ammendment_num) 
    NOT IN (SELECT product_num, ammendment_num FROM temp_table);

-- Clean Up the Temporary Table
DROP TEMPORARY TABLE IF EXISTS temp_table;
```

