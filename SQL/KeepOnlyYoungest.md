
```SQL
-- Gets only the information for the youngest person on that product and ammendment
SELECT Product_num, AmendmentNumber, MIN(Date) AS YoungestDate
INTO NewTable
FROM YourTable
GROUP BY Product, AmendmentNumber;
```

Now to get how many years since that date as an integer and store as
new column in YourTable

```SQL
ALTER TABLE NewTable
ADD COLUMN years_since INT64;

UPDATE NewTable
SET YoungestDriverAge = CAST((DATE_DIFF(CURRENT_DATE(), YoungestDate, DAY)) / 365.25 AS INT64)
WHERE TRUE;
```