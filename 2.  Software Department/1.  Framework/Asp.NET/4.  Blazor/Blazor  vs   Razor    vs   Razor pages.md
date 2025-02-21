### Razor

- **Razor**: This is a <span style="color:rgb(255, 255, 0)">markup</span> <span style="color:rgb(255, 255, 0)">syntax</span> used in ASP.NET to create <span style="color:rgb(255, 255, 0)">dynamic web content</span>. It allows you to <span style="color:rgb(255, 255, 0)">mix HTML</span> with  <span style="color:rgb(255, 255, 0)">C# </span> code.
- <span style="color:rgb(255, 0, 0)">Razor</span> itself is <span style="color:rgb(255, 255, 0)">not</span> a <span style="color:rgb(255, 255, 0)">framework</span>; it is a <span style="color:rgb(255, 255, 0)">view engine</span> used in ASP.NET applications.

### Razor View File
- If your `.cshtml` file is in the **Views** folder and tied to a **controller**, it’s an **MVC View**,<span style="color:rgb(255, 0, 0)"> not a Razor Page</span> 
	It is known as <span style="color:rgb(255, 255, 0)">Razor View File/View File.</span>
- We need to<span style="color:rgb(255, 255, 0)"> Resolve Dependencies </span>like this way:
```cs
  builder.Services.AddControllersWithViews()
```
	
### Feature of (Razor View File)
These are some <span style="color:rgb(255, 255, 0)">key point</span> of <span style="color:rgb(255, 255, 0)">Razor View File</span>:
	1. **Razor Syntax**: Mixes HTML with C# for dynamic content.
	2. **MVC**: Used in MVC as the "<span style="color:rgb(255, 255, 0)">View</span>" part, <span style="color:rgb(255, 255, 0)">rendering data</span> from <span style="color:rgb(255, 255, 0)">controllers</span>.
	3. **.cshtml**: File extension combining C# and HTML.
	4. **Controller Dependency**: <span style="color:rgb(255, 255, 0)">Views</span> <span style="color:rgb(255, 255, 0)">rely</span> on <span style="color:rgb(255, 255, 0)">controllers </span>for data.
	5. **Separation of Concerns**: UI (HTML) and logic (C#) are kept separate.
	6. **Data Objects**: Use `ViewBag`, `ViewData`, or `Model` to pass data.
	7. **Layout**: Supports shared layouts for consistent design.(`_layout.cshtml`)
	8. **Partial Views**: Allows reusable UI components.

This should make it easier to remember key points!

### Razor Pages

- **Razor Pages**: This is a <span style="color:rgb(255, 255, 0)">feature</span> of ASP.NET Core that <span style="color:rgb(255, 255, 0)">uses</span> the <span style="color:rgb(255, 255, 0)">Razor syntax</span> for <span style="color:rgb(255, 255, 0)">page-based programming</span>. 
- It is a way to <span style="color:rgb(255, 255, 0)">build</span> <span style="color:rgb(255, 255, 0)">web</span> <span style="color:rgb(255, 255, 0)">applications</span> by organizing <span style="color:rgb(30, 255, 0)">content</span> into <span style="color:rgb(30, 255, 0)">pages</span> rather than <span style="color:rgb(255, 0, 0)">controllers</span> and <span style="color:rgb(255, 0, 0)">actions</span> (as in MVC). 
   <span style="color:rgb(255, 0, 0)"> Don't  confuse  with Razor Pages :</span>
-  <span style="color:rgb(255, 255, 0)">Razor Pages</span> as a <span style="color:rgb(255, 255, 0)">simplified</span> way to<span style="color:rgb(255, 255, 0)"> build web applications</span>, but it is built on top of the <span style="color:rgb(255, 255, 0)">Razor view engine.</span>
- If it's in the **Pages** folder and has a `.cshtml.cs` file, it's a **Razor Page**.
- if we add<span style="color:rgb(255, 255, 0)"> Razor pages</span> in our project then we have to <span style="color:rgb(255, 255, 0)">add Services</span> or  <span style="color:rgb(255, 255, 0)">Dependency Resolve </span>like this way
 ```cs
 builder.Services.AddRazorPages();
```

### Blazor

- **Blazor**: This is a <span style="color:rgb(255, 255, 0)">framework</span> for building <span style="color:rgb(255, 255, 0)">interactive web applications </span>using C#. It allows you to create<span style="color:rgb(255, 255, 0)"> web apps</span> that run in the browser using <span style="color:rgb(255, 255, 0)">WebAssembly</span> (<span style="color:rgb(255, 255, 0)">Blazor</span> <span style="color:rgb(255, 255, 0)">WebAssembly</span>) or on the <span style="color:rgb(255, 255, 0)">server (Blazor Server</span>).
	   <span style="color:rgb(255, 0, 0)"> Don't  confuse  with Blazor Pages :</span>
- <span style="color:rgb(255, 255, 0)">Blazor</span> uses <span style="color:rgb(255, 255, 0)">Razor syntax</span> for defining <span style="color:rgb(255, 255, 0)">UI components</span>, which is why it can sometimes create confusion.
- For <span style="color:rgb(255, 255, 0)">Blazor Server</span> :
```cs
builder.Services.AddServerSideBlazor();
builder.Services.AddRazorComponents();
```
- For <span style="color:rgb(255, 255, 0)">Blazor</span> <span style="color:rgb(255, 255, 0)">WebAssembly</span> :
```cs
builder.Services.AddBlazorWebAssembly()
```

### Summary

- **Razor**: Markup syntax for combining HTML and C#.
- **Razor Pages**: A page-focused feature of ASP.NET Core that uses Razor syntax (not a standalone framework). and file extension something like 
		`.cshtml.cs`
- **Blazor**: A full-fledged framework for building interactive web applications, utilizing Razor syntax for UI components.