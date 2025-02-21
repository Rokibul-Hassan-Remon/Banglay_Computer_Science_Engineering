
##   Parent Table structure : 
```sql
Create table Teacher (
						TName varchar2(20),						
						TID   varchar2(7),						
						Salary numeric(6),						
						TDept  varchar2(5),						
						TPhone  varchar2(15),						
					    constraints Teacher_pk primary key(TID) 		    
)
```

# Problem : 
#### If you delete any record(row) from the Teacher table ,  but logically  impossible . 
### But It is possible , using cascade . 
#### If any record delete from the Teacher(Parent) table then automatically delete from the Student(Child) table . Because , deleted record  referenced by the child table record . So ,  Logically if somehow we can delete the record from the child table(Student ) Then . Overall structure of the student  and Teacher table will be maintained . 

## Child Table Structure : 
```sql
Create table Student (
			SName varchar2(20),
			SID   varchar2(7),
			Fees numeric(6),
			Dept  varchar2(5),
			Parent_Phone  varchar2(15),
			Class_Teahcer varchar2(20),
			
			constraints Student_pk primary key(SID), 
			constraints Student_fk foreign key Class_Teacher references Teacher(TName)
						on delete cascade
						
)
```


Oracle only support `Delete ` cascade operation..
