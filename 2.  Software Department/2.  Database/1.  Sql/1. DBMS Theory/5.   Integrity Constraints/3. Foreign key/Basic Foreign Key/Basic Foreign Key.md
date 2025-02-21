
# Why comes Foreign key ?
## Ans: 
The DBMS enforces this restriction to ensure that:

1. `One-to-Many Relationships`: Each value in the foreign key corresponds to a single unique record in the parent table.
	- **Uniqueness**:  
	    A foreign key must reference a column that is unique, like a primary key or a column with a unique constraint. This avoids confusion, as multiple rows in the parent table can't have the same value, ensuring clear relationships.
	    
1. `Consistency`: Ambiguities or duplicate matches are avoided, ensuring the integrity of the data.
	- **Referential Integrity**:  
	    A foreign key ensures that every value in the child table matches an existing value in the parent table. If the referenced column isn’t unique, the database cannot guarantee a reliable and consistent link between the tables.



- You <span style="color:rgb(255, 255, 0)">cannot reference</span> a <span style="color:rgb(255, 255, 0)">non-unique</span> or <span style="color:rgb(255, 255, 0)">non-primary</span> key <span style="color:rgb(255, 255, 0)">column</span> as a<span style="color:rgb(255, 255, 0)"> foreign key.</span>


# Why always foreign key reference a primary key ?
## Ans : 
` WE know that `,
- You cannot reference a non-unique or non-primary key column as a foreign key.

And also 
`We know that` , 
	-  A primary key is implicitly unique, so referencing it is common practice.
	
#### **Note :**  That's why for safety purpose we reference the primary key .


## Example : 
```sql
-- Table with Unique Constraint
CREATE TABLE Departments (

    DepartmentID INT ,
    DepartmentCode VARCHAR(10) UNIQUE
);

-- Table with Foreign Key
CREATE TABLE Employees (

    EmployeeID INT PRIMARY KEY,
    DepartmentCode VARCHAR(10),
    FOREIGN KEY (DepartmentCode) REFERENCES Departments(DepartmentCode)
    
);

```