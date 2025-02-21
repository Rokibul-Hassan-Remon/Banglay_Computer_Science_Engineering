## Methods
- ### **Purpose**: Methods are used 
				- to perform `actions or operations`. 

- ### **Syntax**: Methods are defined with a 
				-  ` return type` (or `void` if they don't return a value)
				- a `name`, and `parentheses`, which may include parameters .

- ###  **Behavior**: Methods can contain 
				-`complex logic `, `loops`, and `conditionals`. They are invoked (called) with 
				-a set of parentheses and can be passed arguments.

```cs
class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    // Method to display person details
    public void DisplayDetails()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }

    // Method to increment age by a specified number of years
    public void IncrementAge(int years)
    {
        Age += years;
    }

	Person person = new Person { Name = "Alice", Age = 30 };
	person.DisplayDetails(); // --> method
	person.IncrementAge(5);  // --> method with argument

}

```

### Properties

- ### **Purpose**: Properties are used to
				- `store` and `retrieve values`, 
				- typically representing the state or attributes of an object.`They provide a way to read and write these values with encapsulation`.
- ### **Syntax**: Properties are 
			    - defined with `get` and `set` accessors within a property declaration. **They do not have parameters or complex logic** . *This line only for C# programming.*
			    
- ### **Behavior**: Properties often
				- encapsulate a private field, providing controlled access to it. They are accessed like fields but can include validation or other logic within the accessors

```cs
class Person
{
    private int age; // Private field

    // Property to get and set the age with validation
    public int Age
    {
        get { return age; }
        set
	        {
	            if (value >= 0)
	                age = value;
	            else
	                throw new ArgumentException("Age cannot be negative");
	        }
    }

    // Auto-implemented property for Name
    public string Name { get; set; }

	Person person = new Person { Name = "Alice" };
	person.Age = 30;           // Sets the age property
	Console.WriteLine(person.Age); // Gets the age property

}

```

key **dif.** between **Methods** & **Properties**

Ans: Based on C#

|      Feature      | Methods                                            | Properties                                       |
|:-----------------:|:-------------------------------------------------- |:------------------------------------------------ |
|    **Syntax**     | Defined with return type, name, and parentheses    | Defined with `get` and `set` accessors           |
|                   |                                                    |                                                  |
|  **Parameters**   | Can take parameters                                | Cannot take parameters                           |
|                   |                                                    |                                                  |
|  **Invocation**   | Called with parentheses (e.g., `method()`)         | Accessed like fields (e.g., `property`)          |
|                   |                                                    |                                                  |
|  **Complexity**   | Can contain complex logic, loops, and conditionals | Typically contain simple logic                   |
|                   |                                                    |                                                  |
| **Encapsulation** | Encapsulate behavior                               | Encapsulate data access with optional validation |
|                   |                                                    |                                                  |
| **Usage Example** | `person.DisplayDetails()`                          | `person.Age = 30` and `int age = person.Age`     |
|                   |                                                    |                                                  |
|    **Purpose**    | Perform actions or operations                      | Store and retrieve values                        |

