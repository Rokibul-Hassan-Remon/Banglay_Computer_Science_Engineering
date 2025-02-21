# Purpose of viewImport.cshtml
This file is used to **avoid repeating** certain **code** in every **Razor page**. It allows you to write common settings in one place, 
and they apply to all the **Razor views (pages)** in your project.

- **Saves Time**: You don't have to write the same `@using` or `@addTagHelper` directives in every Razor page.
- **Keeps Code Clean**: You write common things once, and they work everywhere.

