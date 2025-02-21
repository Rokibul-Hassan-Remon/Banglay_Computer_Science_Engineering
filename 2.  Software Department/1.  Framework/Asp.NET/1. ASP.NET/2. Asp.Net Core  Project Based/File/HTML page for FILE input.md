
## If u write this then your file don't be send . 
```html title:razor_syntax
  <input type="file" asp-for="UploadedFile" />
```



## Ensure the form supports file uploads: 
For the form to handle file uploads, you need to set the `enctype` attribute to
`"multipart/form-data"`. 


##### Without this, the file input won't be sent to the server.

**so ,Final and Corrected file is something like this:**
```html title:razor_syntax
<input type="file" asp-for="UploadedFile" enctype="multipart/form-data" />
```



