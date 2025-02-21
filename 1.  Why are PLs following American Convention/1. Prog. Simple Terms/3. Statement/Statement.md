
In programming, a **statement** is a complete instruction that performs some action. It can be anything from declaring a variable, making decisions (conditional statements), performing iterations (loops), or calling a function. Statements are the **building blocks** of a program and are executed **sequentially** unless control flow alters that.

### Characteristics of a Statement:

- It **performs an action** or **executes a command**.
- It usually ends with a **semicolon** (`;`) in languages like C#, C++, and Java.
- Statements can contain **expressions**, but an expression alone isn't necessarily a statement unless it's part of a larger action.


**Declaration Statements**: Declares variables or constants.
```c#
int x = 10;  // Variable declaration
const double pi = 3.14;  // Constant declaration

```

**Expression Statements**: Evaluates an expression and performs an operation (like assignment, method call, etc.).
```c#
x = x + 1;  // Assignment (Expression Statement)
Console.WriteLine(x);  // Method call (Expression Statement)

```

**Control Flow Statements**: Directs the flow of the program by making decisions or repeating actions (using loops, conditions, etc.).
###### Conditional Statements (if, else, switch)
```c#
if (x > 10) {
    Console.WriteLine("x is greater than 10");
} else {
    Console.WriteLine("x is 10 or less");
}

```

**Loop Statements (for, while, do-while)**:
```c#
for (int i = 0; i < 5; i++) {
    Console.WriteLine(i);
}

```

**Jump Statements**: Alters the flow of execution by jumping to another part of the code.

- **Return Statement**: Exits a function and optionally returns a value
```c#
return 42;

```

**Break Statement**: Exits a loop or switch statement
```c#
break;
continue;

```

**Exception Handling Statements**: Catches and handles errors or exceptions that occur during execution.

```c#
try {
    int result = 10 / 0;
} catch (DivideByZeroException ex) {
    Console.WriteLine("Cannot divide by zero");
} finally {
    Console.WriteLine("End of operation");
}

```

### Statement vs. Expression:

- **Expression**: Produces a value.
    - Example: `5 + 3` or `x * 2`
- **Statement**: Executes an action (could include expressions).
    - Example: `int x = 5 + 3;` or `Console.WriteLine(x * 2);`
### Summary:

- A **statement** is an individual instruction in code that performs an action, such as declaring a variable, calling a method, or controlling the flow of execution.
- Statements are executed in sequence and are terminated with a semicolon (`;`) in most languages like C#, C++, and Java.
- Common statements include **declarations**, **expressions**, **control flow**, **loops**, and **error handling**.