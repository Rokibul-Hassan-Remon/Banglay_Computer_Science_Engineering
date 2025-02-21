Here are the primary casting functions and their uses:

1. **CAST**:
    
    - Converts one data type to another within a SQL query.
    - Supports common data types (e.g., `VARCHAR2`, `NUMBER`, `DATE`, `TIMESTAMP`).
    - Syntax:
```sql
        CAST(expression AS target_data_type)
```



`Example:`

```sql
SELECT CAST('123' AS NUMBER) FROM dual;
```


2. **TO_CHAR**:
    
    - Converts a date or number to a string (character).
    - Useful for formatting dates or numbers for display.
    - Syntax:
    ```sql
    TO_CHAR(expression, [format])
```


    - `Example`:
```sql
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') FROM dual;
```     


3. **TO_DATE**:
    
    - Converts a string to a date data type.
    - Commonly used for handling string inputs that represent dates.
    - `Syntax`:

```sql
TO_DATE('string_date', 'format')
```
        
- `Example`:
```sql
SELECT TO_DATE('2024-11-14', 'YYYY-MM-DD') FROM dual;
```
        
4. **TO_NUMBER**:
    
    - Converts a string to a numeric type.
    - Often used when dealing with numeric data stored as text.
    - Syntax:
  ```sql
  TO_NUMBER('string_number', [format])
```
        
    - `Example`:
```sql
SELECT TO_NUMBER('123.45') FROM dual;
```
        
5. **CONVERT**:
    
    - Converts character data between different character sets.
    - `Syntax`:
        
```sql
CONVERT(expression, dest_char_set, [source_char_set])
```
        

```sql

SELECT CONVERT('Hello', 'UTF8', 'US7ASCII') FROM dual;

```
        
6. **NVL** and **COALESCE** (for conditional casting):
    
    go to the next folder
    