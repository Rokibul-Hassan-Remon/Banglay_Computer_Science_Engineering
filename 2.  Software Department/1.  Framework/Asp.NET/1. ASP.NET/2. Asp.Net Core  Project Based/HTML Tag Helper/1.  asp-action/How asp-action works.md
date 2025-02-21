Here’s a simple summary of how `asp-action` works in ASP.NET Core and the whole form submission process:

1. **In the View**:
    
    - You use `asp-action="SubmitForm"` inside a `<form>` tag.
    - This tells the form to send the data to the `SubmitForm` method in the **controller** when it’s submitted.
#### Example : In `Views` folder here is `submitForm.cshtml` file written this
```html
<form asp-action="SubmitForm" method="post">
    <input type="text" asp-for="Description" />
    <button type="submit">Submit</button>
</form>

```


1. **What `asp-action` Does**:
    
    - **`asp-action="SubmitForm"`** generates the form's `action` URL.
    - If your controller is called `StudentController`, it will generate something like:
```html
<form action="/Student/SubmitForm" method="post">
```

### after **rendering** the `SubmitForm.cshtml` 
```html
<form action="/Student/SubmitForm" method="post">
    <input type="text" id="Description" name="Description" />
    <button type="submit">Submit</button>
</form>

```

- **When the Form is Submitted**:
    
    - The form data is sent to the `/Student/SubmitForm` URL (or the correct URL based on the controller and action).
    - The browser sends the data using a POST request.
- **In the Controller**:
    
    - In your **`StudentController`**, you define the `SubmitForm` method to handle the form submission:
```cs
public class StudentController : Controller
{
    [HttpPost]
    public IActionResult SubmitForm(MyViewModel model)
    {
        // Process the submitted data
        string description = model.Description;
        return View();
    }
}

```


