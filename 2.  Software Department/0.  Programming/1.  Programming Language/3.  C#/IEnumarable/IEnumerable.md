
`IEnumerable<T>` is a fundamental interface in C# that represents a collection of objects that can be enumerated (iterated) one at a time. Here's a breakdown of how it works:

### 1. Definition

`IEnumerable<T>` is defined in the `System.Collections.Generic` namespace and provides a way to iterate over a collection of a specified type.

### 2. Key Features

- **Iteration**: It allows you to use a `foreach` loop to iterate over the collection.
- **Deferred Execution**: When you query data (especially with LINQ), `IEnumerable<T>` supports deferred execution, meaning that the query is not executed until you actually enumerate it (e.g., with a loop or `.ToList()`).

### 3. Basic Structure

Here's how `IEnumerable<T>` is typically structured:

- It contains a single method:
```c#
IEnumerator<T> GetEnumerator();

```

### 4. Implementing IEnumerable

When you create a custom collection, you can implement `IEnumerable<T>` to allow iteration. Here’s a simple example:
```c#
using System;
using System.Collections;
using System.Collections.Generic;

public class MyCollection<T> : IEnumerable<T>
{
    private List<T> items = new List<T>();

    public void Add(T item) => items.Add(item);

    public IEnumerator<T> GetEnumerator() => items.GetEnumerator();

    IEnumerator IEnumerable.GetEnumerator() => GetEnumerator(); // Non-generic version
}

class Program
{
    static void Main()
    {
        var collection = new MyCollection<int>();
        collection.Add(1);
        collection.Add(2);
        collection.Add(3);

        foreach (var item in collection)
        {
            Console.WriteLine(item);
        }
    }
}

```

### 5. Using IEnumerable with LINQ

`IEnumerable<T>` is commonly used with LINQ queries, allowing you to work with collections easily:
```c#
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
        IEnumerable<int> evenNumbers = numbers.Where(n => n % 2 == 0);

        foreach (var num in evenNumbers)
        {
            Console.WriteLine(num);
        }
    }
}

```

### 6. Benefits of IEnumerable

- **Flexibility**: You can work with different types of collections (arrays, lists, etc.) uniformly.
- **Lazy Evaluation**: Only iterates over data when needed, which can be more efficient in terms of memory and performance.

### Conclusion

`IEnumerable<T>` is a powerful interface that allows for easy iteration over collections while providing benefits like deferred execution and compatibility with LINQ. Understanding it is essential for working effectively with collections in C#.