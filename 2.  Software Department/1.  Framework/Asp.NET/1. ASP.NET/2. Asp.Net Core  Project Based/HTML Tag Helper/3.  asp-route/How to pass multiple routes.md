In ASP.NET Core, you can pass multiple route values using the `asp-route` attribute by adding additional `asp-route-{parameterName}` attributes for each route parameter you want to include. Here’s how you can do it:

### 1. **Using Multiple `asp-route` Parameters in Links**

You can specify multiple route parameters in an anchor tag:

#### Example with Anchor Tag:

```html
<a asp-controller="Student" 
   asp-action="Details" 
   asp-route-id="123" 
   asp-route-course="Mathematics" 
   asp-route-semester="Fall2024"
>
    View Student Details 
</a>
		///don't be confuse to this bcz <a> tag is so big that's why need to write this way
```

### 2. **Using Multiple `asp-route` Parameters in Forms**

Similarly, you can include multiple route parameters in a form:

#### Example with Form:

```html Copy code
<form asp-controller="Student" 
	  asp-action="Edit" 
	  asp-route-id="123" 
	  asp-route-course="Mathematics"
	   asp-route-semester="Fall2024" 
	   method="post"


	<input type="text" name="Name" /> 
	<button type="submit">Edit</button> 
	
</form>
```

### 3. **How It Works:**

- In the examples above, we are passing three route parameters:
    - `id`
    - `course`
    - `semester`
- When rendered, these will generate URLs that include all specified route parameters.

### 4. **Generated HTML:**

For the **anchor tag**, it will generate something like:

```html

<a href="/Student/Details/123?course=Mathematics&semester=Fall2024">View Student Details</a>
```

For the **form**, it will generate something like:

```html
<form action="/Student/Edit/123?course=Mathematics&semester=Fall2024" method="post">
	<input type="text" name="Name" />
	<button type="submit">Edit</button>
</form>
```

### 5. **Controller Action Methods:**

Your controller should have action methods that can accept these route parameters:

#### Example Controller:

```csharp

public class StudentController : Controller
{     
	// Action to view details of a student     
	public IActionResult Details(int id, string course, string semester)
	{   
		// Use id, course, and semester to fetch student details
		return View();    
	}      
	
	// Action to edit a student's information 
	    
	[HttpPost]     
	public IActionResult Edit(int id, string Name, string course, string semester)
	{         // Process the edit operation using id, Name, course, and semester         
		return View();
	} 
}

```


### Summary:

- To pass multiple routes, simply use multiple `asp-route-{parameterName}` attributes in your anchor tags or forms.
- Each attribute specifies a route parameter that will be included in the generated URL.
- Ensure that your controller actions accept the corresponding parameters to handle the requests properly.