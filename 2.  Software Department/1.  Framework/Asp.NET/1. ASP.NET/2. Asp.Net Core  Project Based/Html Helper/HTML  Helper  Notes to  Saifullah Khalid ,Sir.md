
# Helper methods 10

Below are common **Asp.NET Core** HTML helper methods, demonstrated with both **model binding** and **non-model binding** approaches. Each method includes parameter descriptions to help understand how to use them effectively.

---

### 1. **TextBox**

### Description:

Renders a standard `<input type="text">` element.

### Parameters:

- **name**: Name of the input field.
- **value**: Initial value of the textbox.
- **htmlAttributes**: Object containing HTML attributes for the element (e.g., class, id).

### Example:
**With Model Binding:**

```cs

@model MyViewModel
@Html.TextBoxFor(model => model.Name, new { @class = "form-control", @placeholder = "Enter name" })

```

- **TextBoxFor** binds to the `Name` property in `MyViewModel`.
- `new { @class = "form-control" }` adds Bootstrap styling and placeholder text.


**Without Model Binding:**
```cs
@Html.TextBox("Name", "Default Value", new { @class = "form-control" })

```

- **TextBox** requires the field name (`Name`), the default value (`Default Value`), and HTML attributes.

---

### 2. **Password**

### Description:

Renders a password input `<input type="password">`.

### Parameters:

- **name**: Name of the input field.
- **value**: Initial value (null by default for security).
- **htmlAttributes**: Object for additional HTML attributes.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.PasswordFor(model => model.Password, new { @class = "form-control" })

```

- **PasswordFor** binds to the `Password` property.

**Without Model Binding:**

```cs
@Html.Password("Password", null, new { @class = "form-control" })

```

- **Password** manually defines the name and HTML attributes.

---

### 3. **TextArea**

### Description:

Renders a multi-line text input (i.e., `<textarea>` element).

### Parameters:

- **name**: Name of the field.
- **value**: Initial text content.
- **htmlAttributes**: HTML attributes like rows, columns, class, etc.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.TextAreaFor(model => model.Description, new { @class = "form-control", @rows = 5 })

```

- **TextAreaFor** binds to `Description` and allows you to set the number of rows.

**Without Model Binding:**

```cs
@Html.TextArea("Description", "Enter your description", new { @class = "form-control", @rows = 5 })

```

- **TextArea** manually sets the name and value.

---

### 4. **CheckBox**

### Description:

Renders a checkbox `<input type="checkbox">`.

### Parameters:

- **name**: Name of the checkbox.
- **isChecked**: Whether the checkbox is checked (`true`/`false`).
- **htmlAttributes**: HTML attributes for styling.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.CheckBoxFor(model => model.IsActive, new { @class = "form-check-input" })

```

- **CheckBoxFor** binds to `IsActive` and renders it as a checkbox.

**Without Model Binding:**

```cs
@Html.CheckBox("IsActive", true, new { @class = "form-check-input" })

```

- **CheckBox** manually sets the name and whether it is checked.

---

### 5. **DropDownList**

### Description:

Renders a `<select>` dropdown list.

### Parameters:

- **name**: Name of the dropdown field.
- **selectList**: List of items to populate the dropdown.
- **optionLabel**: Optional label to be displayed at the top.
- **htmlAttributes**: HTML attributes for the dropdown.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.DropDownListFor(model => model.SelectedCountry, new SelectList(Model.Countries, "Value", "Text"), "Select Country", new { @class = "form-select" })

```

- **DropDownListFor** binds to `SelectedCountry` and populates the dropdown with the list of countries.

**Without Model Binding:**

```cs
@Html.DropDownList("SelectedCountry", new SelectList(new List<SelectListItem>
{
    new SelectListItem { Text = "USA", Value = "1" },
    new SelectListItem { Text = "UK", Value = "2" }
}, "Value", "Text"), "Select Country", new { @class = "form-select" })

```

- **DropDownList** requires the name and manually populates the list.

---

### 6. **RadioButton**

### Description:

Renders a radio button input `<input type="radio">`.

### Parameters:

- **name**: Name of the radio button group.
- **value**: The value when selected.
- **isChecked**: Whether the radio button is initially selected.
- **htmlAttributes**: Additional HTML attributes.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.RadioButtonFor(model => model.Gender, "Male", new { @class = "form-check-input" })
@Html.RadioButtonFor(model => model.Gender, "Female", new { @class = "form-check-input" })

```

- **RadioButtonFor** binds to the `Gender` property and provides two options (Male/Female).

**Without Model Binding:**

```cs
@Html.RadioButton("Gender", "Male", true, new { @class = "form-check-input" })
@Html.RadioButton("Gender", "Female", false, new { @class = "form-check-input" })

```

- **RadioButton** requires manual setup of name, value, and whether it's checked.

---

### 7. **Label**

### Description:

Renders an HTML `<label>` element.

### Parameters:

- **name**: Name for the associated input.
- **labelText**: Text to display as the label.
- **htmlAttributes**: Additional HTML attributes for styling.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.LabelFor(model => model.Name, "Your Name", new { @class = "form-label" })

```

- **LabelFor** binds to `Name` and generates the corresponding label.

**Without Model Binding:**

```cs
@Html.Label("Name", "Your Name", new { @class = "form-label" })

```

- **Label** requires the name and text to be specified manually.

---

### 8. **Hidden Field**

### Description:

Renders a hidden input field `<input type="hidden">`.

### Parameters:

- **name**: Name of the hidden field.
- **value**: Value for the hidden field.

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.HiddenFor(model => model.Id)

```

- **HiddenFor** binds to the `Id` property and stores the value as a hidden field.

**Without Model Binding:**

```cs
@Html.Hidden("Id", "123")

```

- **Hidden** manually sets the name and value.

---

### 9. **ValidationMessage**

### Description:

Renders validation error messages for a specific field.

### Parameters:

- **name**: Name of the field associated with the validation message.
- **message**: Custom validation message (optional).
- **htmlAttributes**: HTML attributes for the message (e.g., styling).

### Example:

**With Model Binding:**

```cs
@model MyViewModel
@Html.ValidationMessageFor(model => model.Name, "", new { @class = "text-danger" })

```

- **ValidationMessageFor** automatically displays the validation error for `Name`.

**Without Model Binding:**

```cs
@Html.ValidationMessage("Name", "", new { @class = "text-danger" })

```

- **ValidationMessage** requires the field name and optionally allows for custom error text.

---

### 10. **ActionLink**

### Description:

Generates an HTML `<a>` tag (hyperlink) that links to a specific action.

### Parameters:

- **linkText**: The display text for the link.
- **actionName**: The name of the action to link to.
- **controllerName**: The name of the controller to link to (optional).
- **routeValues**: Any route values for the link (optional).
- **htmlAttributes**: HTML attributes for the anchor tag.

### Example:

**With Route Values (Dynamic):**

```cs
@Html.ActionLink("Go to Home", "Index", "Home", new { id = 5 }, new { @class = "btn btn-primary" })

```

- Generates a link that navigates to `/Home/Index?id=5`.

**Without Route Values:**

```cs
@Html.ActionLink("Home", "Index")

```

- Generates a basic link to the `Index` action of the `Home` controller.

---

These helper methods provide both flexibility and strong typing in views, allowing you to interact with data models or manually create HTML elements with ease.