## **1**.    Open  a  New   Project  with   `Model-View-Controller`

## **2** .   Install 3 given Packages
.
				`1. Microsoft .Net Core .SQlServer 8.0.1 (Latest)`
				`2. Microsoft .Net Core .tools 8.0.0 (Latest) `
				`3. Microsoft .Net Core .design 8.0.0  (Latest)`

## **3**.    Create `Connection`  string in `appsetting.json`

## **4**.    Create `DbContex`  so that connect with the database  	

## **5**.    Configure the   
.
					`builder.Configuration.GetConnectionString( )`
					`builder.Services( ) ` 
##     in `program.cs` and so that the  specific table  connect with this `ssql` .

## **6** .   Create  `Data Model` (Entity )

## **7**.    If we want  to **create** a **new**  **model** the  just go to the
.
					`ProjectNameDbContext`  
##    class   and   Create a 
.
					` DbSet `  
##                                         **object**   

## **8**.     Run the **migration** from the **package manager console** 

