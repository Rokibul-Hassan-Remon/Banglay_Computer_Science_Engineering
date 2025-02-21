In C#, add `@` before a string to make it a <span style="color:rgb(255, 255, 0)">verbatim</span(<span style="color:rgb(255, 255, 0)">আক্ষরিকভাবে</span>) string. This way:

- Backslashes don’t need `\\`.
- You can span multiple lines.
- Double quotes are written as `""`.

Example: 
			<span style="color:rgb(255, 255, 0)">using</span> <span style="color:rgb(255, 255, 0)">verbatim</span> <span style="color:rgb(255, 255, 0)">string</span> type
```cs
string path = @"C:\Folder\MyFile.txt";

```

Example:
		**Not**  <span style="color:rgb(255, 255, 0)">verbatim</span> <span style="color:rgb(255, 255, 0)">string</span> type
```cs
string path = "C:\\Folder\\MyFile.txt";

```

<span style="color:rgb(255, 255, 0)">without</span> using <span style="color:rgb(255, 255, 0)">verbatim</span> it is so <span style="color:rgb(255, 255, 0)">hard</span> to <span style="color:rgb(255, 255, 0)">add extra</span> **backslash** `( \ )` 