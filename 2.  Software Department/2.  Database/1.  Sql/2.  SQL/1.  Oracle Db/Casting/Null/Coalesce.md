# `COALESCE` in Oracle

The `COALESCE` function returns the first non-`NULL` value from a list of expressions. It’s helpful when you need to check multiple values in a specific order and return the first one that is not `NULL`.

### Syntax

```sql
COALESCE(expr1, expr2, ..., exprN)
```

- **`expr1, expr2, ..., exprN`**: A list of expressions. `COALESCE` returns the first non-`NULL` expression it finds in the list. If all values are `NULL`, it returns `NULL`.

### Example

Let’s say we have a table `employees` with columns `bonus`, `commission`, and `salary_adjustment`. We want to use the first available value among these columns and display it as `extra_income`.

```sql
SELECT employee_id,        COALESCE(bonus, commission, salary_adjustment, 0) AS extra_income FROM employees;
```

In this example:

- `COALESCE` checks `bonus` first, then `commission`, then `salary_adjustment`.
- It returns the first non-`NULL` value it finds.
- If all three columns are `NULL`, it returns `0` (as specified at the end).

### Differences Between `NVL` and `COALESCE`

- **`NVL`** only allows you to provide a single fallback value for a `NULL` expression.
- **`COALESCE`** lets you provide multiple fallback values in a prioritized order.

### When to Use Which

- Use **`NVL`** if you only need to handle a single `NULL` check.
- Use **`COALESCE`** if you need to check multiple values in sequence or want a more flexible solution for handling `NULL` values.