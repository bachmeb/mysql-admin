# concat

## References
* http://stackoverflow.com/questions/14282369/mysql-concatenate-a-string-to-a-column

##### Concat a string into the results of a query
```
sql
UPDATE users 
SET obs = CONCAT(obs,' frienly hard worker') 
WHERE area='it';
```
