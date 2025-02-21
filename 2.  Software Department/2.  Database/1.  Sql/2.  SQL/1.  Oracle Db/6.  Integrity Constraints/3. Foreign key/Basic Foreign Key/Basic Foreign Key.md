
## Parent table structure : 
```sql
Create table Teacher (
			TName varchar2(20),
			TID   varchar2(7),
			Salary numeric(6),
			TDept  varchar2(5),
			TPhone varchar2(15),

		   constraints Teacher_pk primary key(TID) 
)
```




## Child Table Structure : 
```sql
Create table Student (
			SName varchar2(20),
			SID   varchar2(7),
			Fees numeric(6),
			Dept  varchar2(5),
			Parent_Phone  varchar2(15),
			Class_Teahcer varchar2(20),
			
			constraints Student_pk primary key(TID), 
			constraints Student_fk foreign key Class_Teacher refrences Teacher(TName)			
)

```
