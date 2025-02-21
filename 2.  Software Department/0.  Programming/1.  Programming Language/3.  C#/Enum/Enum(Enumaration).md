`enum` is a keyword of enumeration. It mainly made for developers to handle which are logically related constant variable with it's value. By default , it is `int` type . But we can typecast it's type using `:` this and then define the type of the value of `enum` values corresponding value.
#### Exam:

```cs

enum WeekDays : byte {
	Sunday,
	Saturday,
	Monday,
	Thursday,
	Friday
};
```




- **What is Parsing?**: Parsing is the process of taking a string of characters (like text) and breaking it down into smaller pieces that make sense. It's like taking a sentence and identifying each word and punctuation mark.

- **Why is it Important?**: Computers need to understand the data we give them. Parsing helps convert raw data into a format that the computer can work with.

- **How it Works**: When you parse a string, the computer looks at each character and decides how to group them based on rules (like grammar in a language).

###  Enum.Parse in C#:

- **Purpose**: `Enum.Parse` is used to convert a string into an enum type. Enums are special types in C# that group related constants (like days of the week or colors).
- **How it Works**:
    1. **Input String**: You give it a string that represents the name or value of an `enum`.
    2. **Analysis**: `Enum.Parse` checks if the string matches any names or values in the `enum`.
    3. **Conversion**: If it finds a match, it converts the string into the corresponding `enum` value.




```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello from Console.WriteLine");
        Console.Write("Hello from Console.Write\n"); // Equivalent to printf without adding a newline automatically
    }
}
