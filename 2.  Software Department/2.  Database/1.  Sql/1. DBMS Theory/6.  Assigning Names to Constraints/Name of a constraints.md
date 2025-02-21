It is <span style="color:rgb(255, 255, 0)">possible</span> for us to <span style="color:rgb(255, 255, 0)">assign</span> a name to <span style="color:rgb(255, 255, 0)">integrity constraint</span> .
```sql
CREATE TABLE 
			instructor
			(
						name varchar2(20) not null,
						salary numeric(8,2), 
						constraint minsalary check(salary > 29000)					
			);
```



```sql
alter table instructor drop constraint minsalary;
```




<span style="color:rgb(255, 255, 0)">Naming</span> the <span style="color:rgb(255, 31, 218)">Primary Key / Foreign key </span> 

```sql
CREATE TABLE department 
(
    dept_id NUMBER,
    dept_name VARCHAR2(50) NOT NULL,
    CONSTRAINT pk_dept PRIMARY KEY (dept_id)
);

CREATE TABLE instructor 
(
    name VARCHAR2(20) NOT NULL,
    salary NUMBER(8, 2),
    dept_id NUMBER,
    CONSTRAINT minsalary CHECK (salary > 29000),
    CONSTRAINT fk_dept FOREIGN KEY (dept_id) REFERENCES department(dept_id)
);

```

