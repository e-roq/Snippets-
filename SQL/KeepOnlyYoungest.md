
```SQL
-- Gets only the information for the youngest person on that product and ammendment
SELECT Product_num, AmendmentNumber, MIN(Date) AS YoungestDate
INTO NewTable
FROM YourTable
GROUP BY Product, AmendmentNumber;
```
