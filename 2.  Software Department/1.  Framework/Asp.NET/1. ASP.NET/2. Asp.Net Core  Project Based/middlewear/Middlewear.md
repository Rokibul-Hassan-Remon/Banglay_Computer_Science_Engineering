**Middleware is a component that is assembled into the application pipeline to handle requests and responses.** Each middleware component can:

1. **Examine** the incoming request.
2. **Modify** the request or response (if needed).
3. **Invoke** the next middleware in the pipeline or short-circuit the process and generate a response itself.

![[Pasted image 20240925093734.png]]


![[Pasted image 20240925093653.png]]

### **app.Use( )**
```csharp

app.Use(async (HttpContext context, RequestDelegate next) =>
{
   //before logic
   await next(context);
   //after logic
 });
```

_**The extension method called “Use” is used to execute a non-terminating / short-circuiting middleware that may / may not forward the request to the next middleware.**_

### Customize Middleware Class

```csharp
class MiddlewareClassName : IMiddleware
{
	public async Task InvokeAsync(HttpContext context, RequestDelegate next)
	{
		//befor logic
		await next(context)
		//after logic
	}
}
```

### **Middleware Chain (Request Pipeline)**

Imagine the request pipeline as a series of connected pipes. Each piece of middleware is like a valve in this pipeline, allowing you to control the flow of information and apply specific operations at different stages.

### **`app.Use` Vs `app.Run`**

These two methods are fundamental for adding middleware to your pipeline, but they have key differences:

```csharp
app.Use(
async (HttpContext context, RequestDelegate next) =>
											{
												await context.Response.WriteAsync("Hello World from Middleware 1");
												await next(context);
											
											}
);
```

- **`app.Use(async (context, next) => { ... })`**
    - **Non-Terminal Middleware:** This type of middleware typically performs some action and then calls the `next` delegate to pass control to the next middleware in the pipeline.
    - **Can Modify Request/Response:** It can change the request or response before passing it along.
    - **Examples:** Authentication, logging, custom headers, etc.
- **`app.Run(async (context) => { ... })`**
    - **Terminal Middleware:** This middleware doesn't call `next`; it ends the pipeline and generates the response itself.
    - **Often Used for the Final Response:** It's commonly used for handling requests that don't need further processing (e.g., returning a simple message).
    - **Can't Modify Request:** Since it's the end of the line, it cannot modify the request before passing it on.

```C#
app.Run(async (HttpContext context) => 
									{ 
									await context.Response.WriteAsync("Hello"); 
									} 
	);
app.Run(async (HttpContext context) =>
									{
									 await context.Response.WriteAsync("Hello again");
									 }
		); 
	
app.Run(); 
//In this code, only the first app.Run middleware will be executed. 
//It terminates the pipeline by writing "Hello" to the response, and 
//the subsequent app.Run

app.Use(async (context, next) => 
								{ 
									await context.Response.WriteAsync("Hello "); 
									await next(context); 
								}
		); 
	//middleware 2 
app.Use(async (context, next) => 
								{
								 await context.Response.WriteAsync("Hello again ");
								  await next(context);
								 }
		); 
//middleware 3 
app.Run(async (HttpContext context) => 
									{ 
										await context.Response.WriteAsync("Hello again"); 
									}
		);
```

**This code demonstrates a correct way to chain middleware.**

1. The first `app.Use` writes "Hello " to the response and then calls `next` to pass control to the next middleware.
2. The second `app.Use` writes "Hello again " and also calls `next`.
3. The final `app.Run` (which is terminal) writes "Hello again" and ends the pipeline. The result would be output of "Hello Hello again Hello again".

**Key Points to Remember**

- **Middleware Order is Crucial:** The order in which you register middleware matters, as they are executed in sequence.
- **Use `app.Use` for Non-Terminal Actions:** Use it for tasks like authentication, logging, or modifying headers/bodies.
- **Use `app.Run` to Terminate the Pipeline:** Employ it when you want to generate the final response.
- **Short-Circuiting:** Middleware can choose to short-circuit the pipeline (not call `next`) and return a response early if needed.
### **Custom Middleware**

- **Encapsulate logic:** Bundle related operations (e.g., logging, security checks, custom headers) into a reusable component.
- **Customize behavior:** Tailor the request/response pipeline to precisely match your application's needs.
- **Improve code organization:** Keep your middleware code clean and maintainable.

### **Anatomy of a Custom Middleware Class**

1. **Implement `IMiddleware`:** This interface requires a single method: `InvokeAsync(HttpContext context, RequestDelegate next)`. This is the heart of your middleware's logic.
2. **`InvokeAsync or Invoke` Method:**
    - `context`: The `HttpContext` provides access to the request and response objects.
    - `next`: The `RequestDelegate` allows you to call the next middleware in the pipeline.
```cs
namespace MiddlewareExample.CustomMiddleware
{
    public class MyCustomMiddleware : IMiddleware  
    {
        public async Task InvokeAsync(HttpContext context, RequestDelegate next)
        {
            await context.Response.WriteAsync("My Custom Middleware - Starts\n");
            await next(context);  
            await context.Response.WriteAsync("My Custom Middleware - Ends\n");
        }
    }
 
    // Extension method for easy registration
    public static class CustomMiddlewareExtension
    {
        public static IApplicationBuilder UseMyCustomMiddleware(this IApplicationBuilder app)
        {
            return app.UseMiddleware<MyCustomMiddleware>();
        }
    }
}
```

```cs
// Program.cs (or Startup.cs)
using MiddlewareExample.CustomMiddleware;
 
// ...
 
builder.Services.AddTransient<MyCustomMiddleware>(); // Register as transient
 
app.Use(async (HttpContext context, RequestDelegate next) => {
														    await context.Response.WriteAsync("From Midleware 1\n");
														    await next(context);
														}
		);
 
app.UseMyCustomMiddleware(); // Use the extension method
 
app.Run(async (HttpContext context) => {
								    await context.Response.WriteAsync("From Middleware 3\n");
								}
        );
```

- **`MyCustomMiddleware` Class:** This class implements `IMiddleware`. Its `InvokeAsync` method:
    - Writes "My Custom Middleware - Starts" to the response.
    - Calls `next(context)` to invoke the next middleware in the pipeline.
    - Writes "My Custom Middleware - Ends" to the response after the next middleware has finished.
- **`CustomMiddlewareExtension` Class:** This provides a convenient extension method `UseMyCustomMiddleware` to register your middleware in the `Startup.Configure` method.

### **How It Works**

1. **Registration:** You register `MyCustomMiddleware` as a transient service so that [ASP.NET](http://ASP.NET) Core can create instances of it when needed.
2. **Pipeline Integration:** The `app.UseMyCustomMiddleware()` extension method seamlessly adds your middleware to the pipeline.
3. **Execution Order:** Middleware components are executed in the order they are added to the pipeline. In this case, the order would be Middleware 1, MyCustomMiddleware, then Middleware 3.

### **Custom Conventional Middleware**
```cs
class MiddlewareClassName
{
  private readonly RequestDelegate _next;
 
  public MiddlewareClassName(RequestDelegate next)
  {
    _next = next;
  }
 
  public async Task InvokeAsync(HttpContext context)
  {
   //before logic
   await _next(context);
   //after logic
  }
});

```

### The Ideal Order of Middleware Pipeline

1. **Exception/Error Handling:**
    - **Purpose:** Catches and handles exceptions that occur anywhere in the pipeline.
    - **Examples:** `UseExceptionHandler`, `UseDeveloperExceptionPage` (for development environments).
2. **HTTPS Redirection:**
    - **Purpose:** Redirects HTTP requests to HTTPS for security.
    - **Example:** `UseHttpsRedirection`.
3. **Static Files:**
    - **Purpose:** Serves static files like images, CSS, and JavaScript directly to the client.
    - **Example:** `UseStaticFiles`.
4. **Routing:**
    - **Purpose:** Matches incoming requests to specific endpoints based on their URLs.
    - **Examples:** `UseRouting`, `UseEndpoints`.
5. **CORS (Cross-Origin Resource Sharing):**
    - **Purpose:** Enables secure cross-origin requests from different domains.
    - **Example:** `UseCors`.
6. **Authentication:**
    - **Purpose:** Verifies user identities and establishes a user principal.
    - **Example:** `UseAuthentication`.
7. **Authorization:**
    - **Purpose:** Determines whether a user is allowed to access a particular resource or perform a certain action.
    - **Example:** `UseAuthorization`.
8. **Custom Middleware:**
    - **Purpose:** Your application-specific middleware components to handle tasks like logging, feature flags, etc.

**Reasoning Behind the Order**

- **Early Exception Handling:** Catching exceptions early prevents them from propagating and causing further issues down the pipeline.
- **Security First:** HTTPS redirection, authentication, and authorization are essential for securing your application.
- **Performance Optimization:** Static files, response caching, and compression are placed early to optimize the response generation process.
- **Routing as a Foundation:** Routing determines how requests are handled by your application's core logic.
- **CORS for Flexibility:** CORS allows your application to be consumed by a wider range of clients.
- **Custom Middleware:** Your custom middleware can be placed strategically within the pipeline to apply logic at the appropriate stage.

### The Right Order Of Middleware

![[Pasted image 20240925095156.png]]

```csharp
**app.UseExceptionHandler("/Error");
app.UseHsts();
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseCors();
app.UseAuthentication();
app.UseAuthorization();
app.UseSession();
app.MapControllers();
//add your custom middlewares
app.Run();**
```