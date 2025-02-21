### T-SQL (Transact-SQL):

- **Developed by**: Microsoft for SQL Server and Azure SQL Database.
- **Usage**: Primarily used in Microsoft SQL Server.
- **Key Features**:
    
    - Control-of-flow language (e.g., `BEGIN`, `END`, `IF`, `WHILE`, `CASE`).
    - Supports procedural programming constructs like variables, loops, and error handling (`TRY...CATCH`).
    - Includes built-in functions for string manipulation, date/time handling, and more.
    - Strong integration with Microsoft services like reporting and analysis tools.
    
    Example of T-SQL syntax:
    
```sql

    DECLARE @Count INT; 
    SET @Count = 10;  
    WHILE @Count > 0
     BEGIN     
		     PRINT 'Count is: ' + CAST(@Count AS VARCHAR);   
	  SET 
		  @Count = @Count - 1; END
	  
```
    
    

### PL/SQL (Procedural Language/SQL):

- **Developed by**: Oracle.
- **Usage**: Primarily used in Oracle databases.
- **Key Features**:
    
    - Procedural language designed specifically for use in Oracle environments.
    - Stronger focus on block-structured programming with packages, functions, procedures, and triggers.
    - Built-in error-handling mechanism (`EXCEPTION`).
    
    Example of PL/SQL syntax:
    
    ```sql
		DECLARE    
				 count_var NUMBER := 10; 
		BEGIN    
				 WHILE count_var > 0 LOOP   
				       
					DBMS_OUTPUT.PUT_LINE('Count is: ' || count_var); 
			        count_var := count_var - 1;    
			        
				END LOOP; 
	    END;
```
    
    
    

In summary, **T-SQL** is to Microsoft SQL Server what **PL/SQL** is to Oracle, both providing enhanced functionality over standard SQL with procedural capabilities, control-of-flow constructs, and database-specific features.

