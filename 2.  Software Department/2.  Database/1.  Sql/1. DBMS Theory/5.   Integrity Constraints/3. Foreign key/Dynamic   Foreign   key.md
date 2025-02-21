
When a database has a _referential integrity_ rule (or constraint), it usually prevents any action that would break this rule. For example, if you try to delete or update data in one table that other tables depend on, the database will stop you to avoid errors.

However, there’s an option to handle this differently using a foreign key constraint. In the case of a foreign key constraint, you can specify different actions for what should happen if a row is deleted or updated in a referenced table. For instance:

- In the example below, there’s a table called `course` with a foreign key linking it to a `department` table:
```sql
    create table course
     (   ......
				     foreign key (dept_name) references department     
								     on delete cascade     
								     on update cascade,  
		 ......
	 );
```


- Here, the `on delete cascade` and `on update cascade` options mean:
    
    - **Delete Cascade**: If a row in `department` is deleted, any rows in `course` that refer to it will also be deleted automatically. This keeps the database consistent.
    - **Update Cascade**: If a value in `department` is updated, all related rows in `course` will also be updated to match the new value.

SQL also allows other options, like:

- **Set Null**: When the referenced row is deleted or updated, the foreign key value in the dependent table is set to `null`.
- **Set Default**: The foreign key value is set to a default value instead.