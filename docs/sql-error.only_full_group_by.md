# SQL Error: GROUP BY incompatible with sql_mode=only_full_group_by

## References
* http://craftcms.stackexchange.com/questions/12084/getting-this-sql-error-group-by-incompatible-with-sql-mode-only-full-group-by/12106
* http://stackoverflow.com/questions/23921117/disable-only-full-group-by
* http://rpbouman.blogspot.com/2014/09/mysql-575-group-by-respects-functional.html


```
SQL Error: GROUP BY incompatible with sql_mode=only_full_group_by
```

* MySQL 5.7.5+ changed the way GROUP BY behaved in order to be SQL99 compliant (where in previous versions it was not).
* The workaround if you're running MySQL 5.7.5+ is to edit your my.cnf file and remove the ONLY_FULL_GROUP_BY option from sql_mode. That will change GROUP BY behavior back to its pre-MySQL 5.7.5 behavior.
