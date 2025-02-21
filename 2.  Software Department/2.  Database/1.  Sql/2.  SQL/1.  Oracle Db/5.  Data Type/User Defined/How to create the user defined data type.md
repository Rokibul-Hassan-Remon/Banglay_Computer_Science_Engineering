## Create 

```sql 
CREATE 
TYPE 
		Dollars 
AS
		OBJECT 
			(
			    transaction_id NUMBER,
				amount NUMBER(12, 2) 
			) 
FINAL;

```


### Explanation

- **`AS OBJECT`**: This keyword is required when creating an object type in Oracle. <span style="color:rgb(255, 255, 0)">Without</span> `AS OBJECT`, Oracle <span style="color:rgb(255, 255, 0)">will not recognize</span> it as a <span style="color:rgb(255, 255, 0)">valid object</span> type.
- **`FINAL`**: This keyword marks the type as `FINAL`, meaning it<span style="color:rgb(255, 255, 0)"> cannot </span>be further <span style="color:rgb(255, 255, 0)">extended</span> or <span style="color:rgb(255, 255, 0)">subclassed</span>.

### Usage of `Dollars` Type

Once defined, you can use this `Dollars` object type to create columns in tables or as part of other structures:

## 1. **Using in a Table**:
```sql
CREATE
TABLE 
	transactions ( 
				    transaction_id NUMBER,     payment Dollars 
				);
```
    
Here, `payment` is a column of type `Dollars`, and each `payment` will have an `amount` attribute.
    
## 2. **Accessing the Attribute**: To retrieve the `amount` value, you can use dot notation:
    
```sql
SELECT transaction_id , payment.amount   FROM transactions;
```
    

### Important Notes

- This `Dollars` type is an **object type**, meaning it’s not a simple scalar. You access its fields (like `amount`) as attributes of the object.
- If you only need a numeric type with precision, it’s generally simpler to use `NUMBER(12, 2)` directly in table definitions. Creating an object type is useful when you want to bundle multiple related attributes together in one type.
