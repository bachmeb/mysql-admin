# csv

## References
* http://stackoverflow.com/questions/356578/how-to-output-mysql-query-results-in-csv-format

```sql
SELECT order_id,product_name,qty
FROM orders
WHERE foo = 'bar'
INTO OUTFILE '/tmp/orders.csv'
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n';
```
