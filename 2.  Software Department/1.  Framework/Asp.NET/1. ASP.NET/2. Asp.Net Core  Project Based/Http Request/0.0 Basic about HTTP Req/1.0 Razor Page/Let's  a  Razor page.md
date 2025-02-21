```HTML 

<form asp-action="Update" method="post">
	
    <input type = "hidden" asp-for = "Id" value = "@Model.Id" />
     
    <div class="form-group">
        <label asp-for="Name">Name:</label>
        <input type="text" class="form-control" asp-for="Name"  />
    </div>
    
    <div class="form-group">
        <label asp-for="Email">Email:</label>
        <input type="email" class="form-control" asp-for="Email" />
    </div>
    
    <button type="submit" class="btn btn-primary">Save Changes</button>
</form>

```

