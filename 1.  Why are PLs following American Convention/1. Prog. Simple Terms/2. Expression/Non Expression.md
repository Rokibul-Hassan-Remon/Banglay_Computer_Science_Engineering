

### 1. **Variable Declarations**

A variable declaration defines a variable but doesn’t produce a value on its own.

**Example:**
```c#
int x; // Variable declaration, not an expression
string name = "Alice"; // Variable assignment (part after `=` is an expression, but the declaration isn't)

```

### 2. **Control Flow Statements**

Control flow statements like `if`, `for`, `while`, `switch`, etc., direct the flow of execution but don’t produce values.

**Example 1:**

```c#
if (x > 0)   // Conditional check, but doesn't return a value itself
{
    Console.WriteLine("x is positive");
}

```

```c#
for (int i = 0; i < 5; i++) // Loop statement controlling execution, no value returned
{
    Console.WriteLine(i);
}

```

### 3. **Method Declarations**

Declaring a method or function defines a block of code that can be executed, but the declaration itself doesn’t return a value.

**Example:**

```C#
void PrintMessage() // Method declaration, not an expression
{
    Console.WriteLine("Hello, World!");
}

```

### 4. **Return Statements**

The `return` statement terminates a method and optionally sends a value back to the caller, but the statement itself doesn’t evaluate to a value.

**Example:**

```c#
return 5; // Terminates the method, but the return statement itself isn't an expression

```

### 5. **Break/Continue Statements**

These statements are used to control loop execution but do not evaluate to a value.

**Example:**

```c#
for (int i = 0; i < 10; i++)
{
    if (i == 5) break; // Stops the loop, but does not return a value
}

```

### 6. **Throw Statements**

The `throw` statement is used to raise an exception, but it doesn’t produce a value.

**Example:**

```c#
throw new Exception("An error occurred"); // Raises an error, doesn't return a value

```

### 7. **Class Declarations**

Defining a class or struct is a way to organize code and create custom types, but it’s not an expression.

**Example:**

```C#
class Person  // Class declaration, not an expression
{
    public string Name;
    public int Age;
}

```

### 8. **Namespace Declarations**

A namespace organizes classes and types into logical groups but doesn’t produce a value.

**Example:**
```c#
namespace MyApplication  // Organizes code, not an expression
{
    class Program
    {
        // ...
    }
}

```

### 9. **Using Statement**

The `using` statement ensures that `IDisposable` objects are properly disposed of, but the statement itself doesn’t evaluate to a value.

**Example:**
```c#
using (StreamReader reader = new StreamReader("file.txt"))
{
    // Reads from file, but `using` itself is not an expression
}

```

### 10. **Void Methods**

A method that returns `void` does not return a value, and thus the method call is not an expression (unless used in an expression like method chaining, where it still doesn't return a meaningful value).

**Example:**
```c#
Console.WriteLine("Hello"); // The method call itself doesn’t return a value

```