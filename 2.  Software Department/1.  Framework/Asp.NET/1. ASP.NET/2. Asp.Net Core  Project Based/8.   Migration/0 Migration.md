### The term **"migration"** is used because it describes how your database **moves or changes** from one **version(state)** to another over time.

- When you **change your code** (like adding a new class or field), 
		the **database needs to be updated to match these changes**.
		
- A **migration** helps to **apply** these **changes** **step by step**, so your database 
	 **migrates** or moves from its **old structure** to the **new structure.**

### Version/State = Structure of the database changes
- ###### **Data and Schema Transition**: Migrations are used to **move** (or "**migrate**") a database schema 
######      from its current state to a new one. This includes creating tables, modifying columns, or adding 
######     relationships based on changes in your code or models.
    
- ###### **Smooth Transitions Over Time**: As your application evolves, you make changes to the data model 
######     (e.g., adding new fields, renaming tables). Migrations help keep the database in sync with 
######      these changes, allowing it to "move" or "migrate" smoothly from the old structure to the new one.
#### Example:
- **Old State**: Your database has a table called `Users` with columns `Id`, `Name`, and `Email`.
- **New State**: You want to add a `DateOfBirth` column to `Users`. This change is reflected in your code.

###### *migration is something like git. 
#### Not like actually same but pretty much same *

##### NuGet Package Manager Console:
```c#
add-migration add<No_of_tables>
update-database
```
##### The same thing could done by this given below CLI  arguments

##### CLI  Console:
```JSON
dotnet ef migrations add AddDateOfBirthToUser
dotnet ef update-database
```

#### `ef` mean
```JSON
		ef = Entity FrameWork
```
