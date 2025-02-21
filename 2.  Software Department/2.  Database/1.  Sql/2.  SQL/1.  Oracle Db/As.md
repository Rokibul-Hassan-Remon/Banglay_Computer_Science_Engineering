
Give/Use a alias name we can use `as` key word 
## without `as` sql  `Oracle Db`
``` sql

SELECT
		cols.column_name
FROM 
		all_constraints (cons)
JOIN 
		all_cons_columns cols
ON 
	  cons.constraint_name = cols.constraint_name


```

## Without `as` sql for `Oracle Db`

``` sql

SELECT
		cols.column_name
FROM 
		all_constraints AS cons
JOIN 
		all_cons_columns AS cols
ON 
	  cons.constraint_name = cols.constraint_name

```

`AS` is optional not mandatory .