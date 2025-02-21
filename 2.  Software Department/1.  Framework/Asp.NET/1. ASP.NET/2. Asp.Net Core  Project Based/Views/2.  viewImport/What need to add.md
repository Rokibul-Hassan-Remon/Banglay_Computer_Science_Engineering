# Add **TagHelper**
```cs
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
```

- This **enables** special **HTML elements** called **Tag Helpers** in all your **Razor pages.**
- **Tag Helpers** make writing `forms, buttons, links`, etc., easier by **connecting** the **HTML** with the **backend logic (server-side code).**

# Add **Domains Model** as a **namespace** 
```cs
@using MasjidManagement.Models
```

- This line makes all the models (like `Donation`, `User`, etc.) from `MasjidManagement.Models` available in all Razor pages.
- You won’t need to write this line separately in every Razor page where you use these models.

# Add **DomainName** as a namespace
```cs
@using MasjidManagement
```

- This line allows you to use the **classes** and **methods** from the `MasjidManagement` namespace in all your **Razor pages** without typing `@using MasjidManagement` in each one.
- Think of it like **giving access** to **certain features** for all **pages** from a specific **section** of your **project**.
