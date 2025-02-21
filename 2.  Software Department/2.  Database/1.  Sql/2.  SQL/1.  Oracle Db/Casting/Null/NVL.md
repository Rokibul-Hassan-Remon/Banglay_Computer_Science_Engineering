In Oracle SQL, **`NVL`** is a function that lets you replace `NULL` values with a specified alternative value. It’s particularly useful when working with optional data or nullable columns in a database.

### Syntax

```sql
NVL(expression, replacement_value)
```

- **`expression`**: The value or column you’re checking for `NULL`.
- **`replacement_value`**: The value you want to return if `expression` is `NULL`.

### How It Works

- If `expression` is `NULL`, Oracle returns `replacement_value`.
- If `expression` is not `NULL`, Oracle simply returns `expression`.

### Example

Suppose we have a table named `employees` with a column `bonus` that may contain `NULL` values. We want to show `0` instead of `NULL` for employees without a bonus.



```sql 
SELECT employee_id, NVL(bonus, 0) AS bonus FROM employees;
```

In this example:

- If an employee's `bonus` is `NULL`, the query will display `0`.
- If `bonus` has a value, that value will be shown.

### Additional Use Case

You can also use `NVL` in calculations to avoid `NULL` values affecting your results. For instance, adding a `NULL` in Oracle returns `NULL`, but with `NVL`, you can replace `NULL` with `0` for meaningful calculations.


```sql 
SELECT salary + NVL(bonus, 0) AS total_compensation FROM employees;
```


In this case, if `bonus` is `NULL`, the calculation will still proceed using `0` instead, preventing the result from becoming `NULL`.