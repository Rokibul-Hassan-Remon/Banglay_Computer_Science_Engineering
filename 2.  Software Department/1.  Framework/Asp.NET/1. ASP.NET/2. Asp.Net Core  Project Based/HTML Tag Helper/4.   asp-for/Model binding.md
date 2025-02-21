**Model binding** is a process in ASP.NET Core that automatically takes data from a user's request (like form submissions) and fills a model (a C# class) with that data.

### Key Points:

1. **Automatic Mapping**: It maps data from form fields, query strings, and route data to the properties of a model class.
    
2. **Example Model**:
    
    ```csharp
    public class Student 
    {     public int Id { get; set; }     
		  public string Name { get; set; }     
		  public string Description { get; set; } 
	}
```
    
3. **Controller Action**:
    
    ```csharp
    public class StudentController : Controller 
    {     
	    [HttpPost]     
	    public IActionResult SubmitForm(Student student)
		{
	                  // The 'student' object is filled with data from the request
	         return View();     
	    } 
    }
```

    
4. **How It Works**: When a form is submitted, ASP.NET Core looks for matching properties in the model and automatically fills them with the submitted data.
    

### Summary:

Model binding makes it easy to work with user input by converting request data into C# objects.