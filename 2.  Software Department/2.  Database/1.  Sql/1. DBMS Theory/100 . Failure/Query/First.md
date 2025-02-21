1. **Problem :**  <span style="color:rgb(255, 255, 0)">Consider the query</span> `Find the average instructors salaries of those departments where the average salary is greater than $42,000. `


**Sol: 1**
```sql
 select 
		 dept name,
		  avg salary 
 from 
		 (
			 select dept_name, avg (salary) 
			  from instructor group by dept_name
		  ) 
		as 
			dept_avg (dept_name, avg_salary)
  where avg_salary > 42000;
```



**Sol 2**

```sql
select 
	   dept name,
	   avg salary 
from 
	 (         -----create a customize table where i am getting to fetch the value
	   select dept name, avg (salary) as avg_salary
	   from instructor group by dept name
	 ) 
		as 
		   dept avg (dept name, avg_salary)
		       
where 
	  avg salary > 42000;
```




