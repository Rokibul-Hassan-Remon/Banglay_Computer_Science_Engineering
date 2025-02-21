# *Library Management Software*

### *Table of Contents*

1. [Executive Summary](#executive-summary)
2. [Introduction](#introduction)
3. [Project Objectives](#project-objectives)
4. [System Overview](#system-overview)
5. [Database Design](#database-design)
6. [Functional Requirements](#functional-requirements)
7. [User Interface Design](#user-interface-design)
8. [Implementation Plan](#implementation-plan)
9. [Testing and Deployment Plan](#testing-and-deployment-plan)
10. [Conclusion](#conclusion)
11. [Setup Guide](#setup-guide)

---

## *Executive Summary*

The *Library Management Software* is a web-based application designed to streamline library operations by managing books, categories, loans, students, and staff efficiently. This software eliminates manual record-keeping by providing an automated solution with user-friendly interfaces and CRUD functionalities.

---

## *Introduction*

The Library Management Software simplifies library management tasks by providing tools to manage books, users, and loans. It aims to provide a secure and user-friendly platform for librarians to operate smoothly while maintaining data integrity.

Key features include:

- Adding and managing book *categories*.
- Managing loans and student *information*.
- *Secure* user authentication and authorization.

---

## *Project Objectives*

1. Implement a secure *registration* and *login system*.
2. Provide functionalities to manage books, book categories, loans, students, and staff.
3. Enable *CRUD* operations for all entities.
4. Ensure data integrity and security.

---

## *System Overview*

The system architecture is divided into four main components:

1. *Web Project:* Handles user interactions via web pages.
2. *Service Project:* Implements business logic and processes requests.
3. *Repository Project:* Interacts with the database using Entity Framework Core.
4. *Model Project:* Defines the data structures (entities) representing the domain.

---

## *Database Design*

The system uses a *Code-First Approach* in Entity Framework Core.

### *Tables:*

1. *Registration Table:* Stores user email and password.
2. *Login Table:* Validates user credentials.
3. *Book Category Table:* Tracks book categories and details.
4. *Book Table:* Stores book details, including author, price, and ISBN.
5. *Book Loan Table:* Manages book loan information.
6. *Staff Table:* Tracks staff details like position, salary, and experience.
7. *Student Table:* Manages student information, including class and date of birth.

---

## *Functional Requirements*

1. *User Registration:* Secure user registration with email and password validation.
2. *User Login:* Authentication using stored credentials.
3. *Book Management:* Add, edit, delete, and view books.
4. *Category Management:* Manage book categories.
5. *Loan Management:* Track loans, including due dates.
6. *Staff and Student Management:* Manage staff and student details.

---

## *User Interface Design*

1. *Registration Page:* User-friendly form for creating new accounts.
2. *Login Page:* Secure login with options for registration.
3. *Management Pages:*
    - List views with CRUD options for books, categories, loans, staff, and students.

---

## *Implementation Plan*

### *Technologies Used:*

- *Backend:* ASP.NET Core, Entity Framework Core.
- *Frontend:* HTML, CSS, JavaScript, JQuery, Bootstrap.
- *Database:* Microsoft SQL Server.

---

## *Testing and Deployment Plan*

1. *Testing:*
    - Integration testing for key modules like user registration and book management.
2. *Deployment:*
    - Publish the application using Visual Studio.
    - Host the application via IIS and configure the database on the server.

---

## *Conclusion*

The Library Management Software provides a robust, efficient solution for library operations, offering enhanced functionality and user experience. Future enhancements could include advanced reporting and email notifications for overdue loans.

---

## *Setup Guide*

### *Step 1: Open a New Project*

1. Open Visual Studio.
2. Create an *ASP.NET Core MVC Web Application*.
3. Name the project and choose a location.

---

### *Step 2: Install Required Packages*

Run the following NuGet commands in the *Package Manager Console*:

Install-Package `Microsoft.EntityFrameworkCore.SqlServer` -Version 8.0.1  
Install-Package `Microsoft.EntityFrameworkCore.Tools` -Version 8.0.0  
Install-Package `Microsoft.AspNetCore.Identity.EntityFrameworkCore` -Version 8.0.10  
Install-Package `AutoMapper` -Version 13.0.1  



*Package Details:*

- `Microsoft.EntityFrameworkCore.SqlServer`: Database provider for Microsoft SQL Server.
- `Microsoft.EntityFrameworkCore.Tools`: Enables migrations and database updates via PMC.
- `Microsoft.AspNetCore.Identity.EntityFrameworkCore`: Simplifies user management and authentication.
- `AutoMapper`: Automates object-to-object mapping for DTOs and models.


---

### *Step 3: Configure Database Connection*

Add the connection string in the appsettings.json:
```json
"ConnectionStrings": {
  "LibraryManagementSoft": "Server=DESKTOP4BMGUC1\\SQLEXPRESS;Database=LibraryManagement;Trusted_Connection=True;MultipleActiveResultSets=True;TrustServerCertificate=True;"
}
```


---
### *Step 4: Create Models and Add DbSet*

1. Create entity classes in the *Models* folder.
2. Update the LibraryDBContext with the necessary DbSet properties.
#### Example : 
```cs
public class Book
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Author { get; set; }
    public DateTime PublishedDate { get; set; }
}
```


### *Step 5: Repository Project and DbContext*

- In *Solution Explorer*, right-click on your solution and select Add > New Project.
    
- Search for Class Library and name it LibraryManageRepository.
    
- Inside the repository project, create a folder named DbConfigure and add a LibraryDBContext class:
```cs
using Microsoft.AspNetCore.Identity.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;

public class LibraryDBContext : IdentityDbContext<ApplicationUser>
{
    public LibraryDBContext(DbContextOptions<LibraryDBContext> options) : base(options) { }

    public DbSet<Book> Books { get; set; }
    public DbSet<Student> Students { get; set; }
}
```
---

###  *Step 6: Run Migrations*

Run the following commands in the *Package Manager Console*:
```powershell
Add-Migration InitialCreate  
Update-Database 
``` 



- This will create and apply the initial database schema.

#  step 7: Create Interface in repository project.
In Repository project, Create a folder named "InterfaceRepository"
	Right click on "LibraryManageRepository" -> add-> New Folder -> name this "InterfaceRepository"
	Create a class named "ILibraryRepository" where "I" means Interface which is convention for naming interface.
	Right click on "InterfaceRepository" -> add-> Class -> name this "ILibraryRepository" and write this snippet.

```cs
public interface ILibraryRepository
{
	Task<IEnumerable<Book>> GetAllBookAsync();
	Task<Book> GetByIdAsync(int id);
	Task AddAsync(Book entity);
	Task UpdateAsync(Book entity);
	Task DeleteAsync(int id);

}
```

#  step 8 : Create "Repository"  folder and make new class named "LibraryRepository"
 Implement the Interface in Repository folder for ILibraryRepository. In Repository project, Create a folder named "Repository"
		Right click on "LibraryManageRepository" -> add-> New Folder -> name this "Repository"
		Create a class named "LibraryRepository" .
		Right click on "Repository" -> add-> Class -> name this "LibraryRepository" and write this snippet.

```cs
public class LibraryRepository : ILibraryRepository
{
	private readonly LibraryDBContext _context;

	public LibraryRepository(LibraryDBContext context)
	{
		_context = context;
	}

	public async Task<IEnumerable<Book>> GetAllBookAsync()
	{
		return await  _context.Books.ToListAsync();
	}

	public async Task<Book> GetByIdAsync(int id)
	{
		return await _context.Books.FindAsync(id);
	}

	public async Task AddAsync(Book entity)
	{
		_context.Books.Add(entity);
		await _context.SaveChangesAsync();

	}

	public async Task UpdateAsync(Book entity)
	{
		_context.Books.Update(entity);
		await _context.SaveChangesAsync();
	}

	public async Task DeleteAsync(int id)
	{
		var entity = await _context.Books.FindAsync(id);

		if (entity != null)
		{
			_context.Books.Remove(entity);
			await _context.SaveChangesAsync();
		}


	}
}
```



# step 9: Create Service project and make interface .
- In *Solution Explorer*, right-click on your solution and select Add > New Project.
    
- Search for Class Library and name it LibraryManageService.
    
- Inside the repository project, create a folder named InterfaceService and add a ILibraryService class. Then write this code:

```cs
public interface ILibraryService
{
    Task<IEnumerable<Book>> GetAllBookAsync();
    Task<BookVM> GetByIdAsync(int id);
    Task AddAsync(Book entity);
    Task UpdateAsync(Book entity);
    Task DeleteAsync(int id);

}
```


# step 10: Implementation of ILibraryService in LibraryService class

Implement the Interface in Service folder for ILibraryService. In Service project, Create a folder named "Service"
			Right click on "LibraryManageService" -> add-> New Folder -> name this "Service"
			Create a class named "LibraryService" .
			Right click on "Service" -> add-> Class -> name this "LibraryService" and write this snippet.

```cs
public class LibraryService : ILibraryService
 {
     private ILibraryRepository _libraryRepository;
		private readonly IMapper _mapper;

		public LibraryService(ILibraryRepository libraryRepository , IMapper mapper)
     {
         _libraryRepository = libraryRepository;
		 _mapper = mapper;
		}

     public async Task<IEnumerable<Book>> GetAllBookAsync()
     {
         return await _libraryRepository.GetAllBookAsync();
     }


     public async Task<BookVM> GetByIdAsync(int id)
     {
         var book = await _libraryRepository.GetByIdAsync(id);
         if (book == null)
             throw new Exception($"no book found");

         return _mapper.Map<BookVM>(book);

     }

     public async Task AddAsync(Book entity)
     {

          await _libraryRepository.AddAsync(entity);

     }

     public async Task UpdateAsync(Book entity)
     {
await _libraryRepository.UpdateAsync(entity);
     }

     public async Task DeleteAsync(int id)
     {
         await _libraryRepository.DeleteAsync(id);
     }

		Task<BookVM> ILibraryService.GetByIdAsync(int id)
		{
throw new NotImplementedException();
		}
	}
```

### **Step 11: Dependency Resolve and  Configure Services in Program.cs**

1. Open Program.cs and configure the DbContext service:

```cs
using Microsoft.EntityFrameworkCore;

var builder = WebApplication.CreateBuilder(args);

var conn = builder.Configuration.GetConnectionString("LibraryManagementSoft");
builder.Services.AddDbContext<LibraryDBContext>(options => options.UseSqlServer(conn));
```


2.  **Dependency resolve** in `program.cs`

```cs
		//Services
builder.Services.AddScoped<ILibraryRepository, LibraryRepository>();


//repositaries
builder.Services.AddScoped<ILibraryService, LibraryService>();
```
---
# step 12: add project reference 
1. for Web project add "LibraryManageService ", "LibraryManageModel", "LibraryManageRepository"
Right click on LibraryManage Project , 
go to Add -> Project Reference-> Tick 3 projects for reference -> click "OK"

2. for "LibraryManageRepository" project add "LibraryManageModel" .
Right click on LibraryManageRepository Project , 
go to Add -> Project Reference-> Tick for "LibraryManageModel"  projects for reference -> click "OK"

3. for "LibraryManageService " project add "LibraryManageModel", "LibraryManageRepository"
Right click on "LibraryManageService" Project , 
go to Add -> Project Reference-> Tick 2 projects "LibraryManageModel" and "LibraryManageRepository" for reference -> click "OK"

---

---

## Testing & Deployment

### *Testing*

- Perform integration testing to ensure seamless interaction between modules.
- Validate CRUD operations and authentication workflows.

### *Deployment*

1. Publish the application using Visual Studio.
2. Set up the database on the server.
3. Configure IIS (Internet Information Services) for hosting.

---

## Future Enhancements

- Advanced reporting features.
- Email notifications for book loan deadlines.
- Integration with external systems for extended functionality.

---

## *License*

This project is licensed under the MIT License.


*Developed by:* [Rokibul Hassan Remon & Md. Jahidul Islam Rakib]  
*GitHub Repository:* [Library Management Software](#)

Feel free to contribute and improve this project!