## **Limitations** of  `COALESCE`:

- `COALESCE` only works if **all arguments** you provide are the **same type**.
- For example, if you try to mix `NUMBER` and `VARCHAR` (text) types in `COALESCE`, it won’t work because they are different types.

### Example Issue:

If you wanted to replace `NULL` salary values with `'N/A'` (a string), you couldn’t use `COALESCE` directly. This is because `N/A` is a string, and the salary is a number. `COALESCE` won’t allow mixing a string and a number.

## **Solution:** Use `DECODE Function:

Oracle’s `DECODE` function can handle this situation. It lets you compare values and return a replacement based on a match, and it **can mix types** (like numbers and text).

## General Form of `DECODE`:
```sql 
DECODE(value,                     ---- column name 
			 match1, replace1,
			 match2, replace2,
			  .
			  .
			  ., 
			 matchN, replaceN, 
			 default_replace
		)
```




- **`value`**: The value to compare.(Mainly it means <span style="color:rgb(255, 255, 0)">column</span> <span style="color:rgb(255, 255, 0)">name</span> or <span style="color:rgb(255, 255, 0)">attribute</span>)
- **`match1, match2, ...`**: The values to compare the `value` against.
- **`replace1, replace2, ...`**: The replacements if there's a match.
- **`default_replace`**: What to return if no match is found.

### Example:

Let’s say we want to replace `NULL` salary values with `'N/A'` (text):

```sql
SELECT 
		DECODE(salary , NULL, 'N/A', salary)  salary_display
FROM
	employees;
```

- If the `salary` is `NULL`, it will return `'N/A'`.
- If the `salary` is not `NULL`, it just returns the `salary` value itself.

### Example: 
```sql
SELECT 
	   employee_name , DECODE( department,
						              'HR', 'Human Resources',
						              'IT', 'Information Technology',
						              'Sales', 'Sales Department',
						              'Other Department')  department_name
FROM 
	employees;

```

### Explanation:

- **`DECODE(department, ...)`**: The `department` is the `value` being checked.
- **Matching multiple values**: The function compares `department` to each match in turn:
    - If `department` is `'HR'`, it returns `'Human Resources'`.
    - If `department` is `'IT'`, it returns `'Information Technology'`.
    - If `department` is `'Sales'`, it returns `'Sales Department'`.
    - If none of the matches (`HR`, `IT`, or `Sales`), it returns `'Other Department'` (the default value).

## Why `DECODE` Works Here:

- **`DECODE`** allows mixing different data types, like numbers (for salary) and text (`'N/A'`).
- `COALESCE` would have failed because it needs all arguments to be of the same type.

## Summary:

- **`COALESCE`** requires all arguments to be the same type.
- **`DECODE`** allows you to mix different data types, so it can handle situations like replacing `NULL` values with a string (like `'N/A'`).
