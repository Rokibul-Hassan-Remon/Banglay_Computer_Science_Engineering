
# **Library Management Software** 
The **Library Management System**, built with **Clean Architecture** in **ASP.NET Core MVC**, ensures modularity and scalability through layered design. It automates library operations like book, loan, and user management while maintaining data integrity and security. The project combines a responsive UI with robust backend services for an efficient, modern solution.
### **Table of Contents**

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

## **Executive Summary**

The **Library Management Software** is a web-based application designed to streamline library operations by managing books, categories, loans, students, and staff efficiently. This software eliminates manual record-keeping by providing an automated solution with user-friendly interfaces and **CRUD** functionalities.

---

## **Introduction**

The Library Management Software simplifies library management tasks by providing tools to manage books, users, and loans. It aims to provide a secure and user-friendly platform for librarians to operate smoothly while maintaining data integrity.

`Key features` include:

- `Adding` and `managing book` **categories**.
- `Managing loans` and `student` **information**.
- **Secure** `user authentication` and `authorization`.

---

## **Project Objectives**

1. Implement a secure **registration** and **login system**.
2. Provide functionalities to manage books, book categories, loans, students, and staff.
3. Enable **CRUD** operations for all entities.
4. Ensure `data integrity` and `security`.

---

## **System Overview**

The system architecture is divided into four main components:

1. **Web Project:** Handles user interactions via web pages.
2. **Service Project:** Implements business logic and processes requests.
3. **Repository Project:** Interacts with the database using Entity Framework Core.
4. **Model Project:** Defines the data structures (entities) representing the domain.

---

## **Database Design**

The system uses a **Code-First Approach** in Entity Framework Core.
### **Core Tables**:

1. **Users Table**: Stores user authentication details.
2. **Books Table**: Contains book details such as title, author, and ISBN.
3. **Categories Table**: Manages book categories.
4. **Loans Table**: Tracks book loans and due dates.
5. **Students Table**: Maintains student details like name and date of birth.
6. **Staff Table**: Tracks staff information such as positions and salaries.

---

## **Functional Requirements**
1. **User Management**: Registration, login, and secure session handling.
2. **Book Management:** Add, edit, delete, and view books.
3. **Category Management:** Manage book categories.
4. **Loan Management:** Track loans, including due dates.
5. **Staff and Student Management:** Manage staff and student details.

---

## **User Interface Design**

1. **Registration Page:** User-friendly form for creating new accounts.
2. **Login Page:** Secure login with options for registration.
3. **Management Pages:**
    - List views with **CRUD** options for books, categories, loans, staff, and students.

---

## **Implementation Plan**

### **Technologies Used:**

- **Backend:** ASP.NET Core, Entity Framework Core.
- **Frontend:** HTML, CSS, JavaScript, JQuery, Bootstrap.
- **Database:** Microsoft SQL Server.

---

### **Architecture Highlights**

- **Repository-Service Pattern**: Ensures separation of concerns.
- **AutoMapper**: Simplifies object mapping between entities and DTOs.

---

## **Testing and Deployment Plan**

1. **Testing:**
    - Integration testing for key modules like user registration and book management.
2. **Deployment:**
    - Publish the application using Visual Studio.
    - Host the application via IIS and configure the database on the server.

---

## **Conclusion**

The Library Management Software provides a robust, efficient solution for library operations, offering enhanced functionality and user experience. Future enhancements could include advanced reporting and email notifications for overdue loans.

---

## **Setup Guide**

### **Step 1: Open a New Project**

1. Open `Visual Studio`.
2. Create an **ASP.NET Core MVC Web Application**.
3. Name the project and choose a location.

---

### **Step 2: Install Required Packages**

Run the following NuGet commands in the **Package Manager Console**:
```powershell
Install-Package Microsoft.EntityFrameworkCore.SqlServer -Version 8.0.1  
Install-Package Microsoft.EntityFrameworkCore.Tools -Version 8.0.0  
Install-Package Microsoft.AspNetCore.Identity.EntityFrameworkCore -Version 8.0.10  
Install-Package AutoMapper -Version 13.0.1  

```

**Package Details:**

- `Microsoft.EntityFrameworkCore.SqlServer`: Database provider for Microsoft SQL Server.
- `Microsoft.EntityFrameworkCore.Tools`: Enables migrations and database updates via PMC.
- `Microsoft.AspNetCore.Identity.EntityFrameworkCore`: Simplifies user management and authentication.
- `AutoMapper`: Automates object-to-object mapping for DTOs and models.


---

### **Step 3: Configure Database Connection**

Add the connection string in the `appsettings.json`:
```json
"ConnectionStrings": {
  "LibraryManagementSoft": "Server=DESKTOP4BMGUC1\\SQLEXPRESS;Database=LibraryManagement;Trusted_Connection=True;MultipleActiveResultSets=True;TrustServerCertificate=True;"
}


```

---
### **Step 4: Create Models**

Define entity classes in the `Models` folder.

#### Example Model:
```cs
public class Book
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Author { get; set; }
    public DateTime PublishedDate { get; set; }
}

```


---


### **Step 5: Configure DbContext**

Add a `LibraryDBContext` class in the `DbConfigure` folder of your repository project:
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

### **Step 6: Run Migrations**

Run the following commands to create and update the database schema:
```powershell
Add-Migration InitialCreate  
Update-Database


```


---

### **Step 7: Add Repository Interface**

Create an `ILibraryRepository` interface:
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


---

### **Step 8: Implement Repository**

Implement `ILibraryRepository` in the `LibraryRepository` class:
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
        return await _context.Books.ToListAsync();
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


---



### **Step 9: Create Service Interface**

Create an `ILibraryService` interface in the `LibraryManageService` project:
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

---

### **Step 10: Implement Service**

Implement `ILibraryService` in the `LibraryService` class:
```cs
public class LibraryService : ILibraryService
{
    private readonly ILibraryRepository _libraryRepository;
    private readonly IMapper _mapper;

    public LibraryService(ILibraryRepository libraryRepository, IMapper mapper)
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
        if (book == null) throw new Exception("No book found");
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
}

```


---

### **Step 11: Configure Dependencies in Program.cs**

Add the following services in `Program.cs`:
```cs
builder.Services.AddDbContext<LibraryDBContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("LibraryManagementSoft")));

builder.Services.AddScoped<ILibraryRepository, LibraryRepository>();
builder.Services.AddScoped<ILibraryService, LibraryService>();

```


---

### **Step 12: Add Project References**

- Web Project: Add references to `LibraryManageService`, `LibraryManageModel`, and `LibraryManageRepository`.
- Repository Project: Add a reference to `LibraryManageModel`.
- Service Project: Add references to `LibraryManageModel` and `LibraryManageRepository`.

---
## Testing & Deployment

### **Testing**

- Perform integration testing to ensure seamless interaction between modules.
- Validate CRUD operations and authentication workflows.

### **Deployment**

1. Publish the application using Visual Studio.
2. Set up the database on the server.
3. Configure IIS (Internet Information Services) for hosting.

---

## Future Enhancements

- Advanced reporting features.
- Email notifications for book loan deadlines.
- Integration with external systems for extended functionality.

---

## **License**

This project is licensed under the MIT License.


**Developed by:** [Rokibul Hassan Remon](https://github.com/Rokibul-Hassan-Remon) & [Md. Jahidul Islam Rakib](https://github.com/Jahidul-islam-rakib)  
**GitHub Repository:** [Library Management Software](#)

Feel free to contribute and improve this project!

