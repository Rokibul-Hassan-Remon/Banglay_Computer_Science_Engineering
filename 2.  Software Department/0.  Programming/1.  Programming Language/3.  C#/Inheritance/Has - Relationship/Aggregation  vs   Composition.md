কম্পোজিশন এবং অ্যাগ্রিগেশনের মধ্যে কোডের দৃষ্টিকোণ থেকে পার্থক্যটা তেমন স্পষ্ট হতে পারে না। আসলে, পার্থক্যটি কোডের মধ্যে **অবজেক্টগুলোর লাইফসাইকেল** এবং তাদের **সম্পর্কের শক্তি**তে নিহিত। আসুন, এই পার্থক্যগুলো আরও বিস্তারিতভাবে ব্যাখ্যা করি।

---

### 1. **Composition : Strong Ownership **

`Composition`, **owned object** (যেমন: অংশ) পুরো অবজেক্ট (whole) ছাড়া অস্তিত্ব রাখতে পারে না। অর্থাৎ, পুরো অবজেক্ট যদি মুছে ফেলা হয়, তবে তার অংশও মুছে যাবে। এখানে মালিকানা **বদ্ধভাবে** সংযুক্ত থাকে।

- **লাইফসাইকেল ডিপেন্ডেন্সি**: অংশ অবজেক্টটি পুরো অবজেক্টের ওপর নির্ভরশীল। পুরো অবজেক্ট মুছে ফেললে, অংশ অবজেক্টও মুছে যাবে।

#### উদাহরণ:
```cs
class Engine
{
    public void Start() => Console.WriteLine("Engine started");
}

class Car
{
    private Engine _engine;  // Car এর মধ্যে Engine রাখা হয়েছে

    public Car()
    {
        _engine = new Engine(); // Car owns Engine
    }

    public void Drive()
    {
        _engine.Start();
        Console.WriteLine("Car is moving...");
    }
}

class Program
{
    static void Main()
    {
        Car car = new Car(); // Car owns Engine, Engine doesn't exist without Car
        car.Drive();
    }
}

```

- **মালিকানা**: `Car` ক্লাস `Engine` কে মালিকানা দেয়, এবং `Engine` `Car` ছাড়া অস্তিত্ব রাখতে পারে না।
- **লাইফসাইকেল**: যদি `Car` অবজেক্টটি মুছে যায়, `Engine` অবজেক্টটিও মুছে যাবে, কারণ এটি `Car` এর সাথে গভীরভাবে সংযুক্ত।

### 2. **Aggregation : Weak Association **

অ্যাগ্রিগেশনে, **owned object** (যেমন: অংশ) পুরো অবজেক্ট (whole) থেকে স্বাধীনভাবে থাকতে পারে। পুরো অবজেক্টটি মুছে ফেললেও, অংশ অবজেক্টগুলির অস্তিত্ব অব্যাহত থাকে। সম্পর্কটি **দুর্বল**, এবং তাদের লাইফসাইকেল আলাদা থাকে।

- **লাইফসাইকেল স্বাধীনতা**: পুরো অবজেক্ট মুছে ফেললেও, অংশ অবজেক্টগুলি মুছে যায় না এবং তারা অন্য কোথাও ব্যবহার করা যেতে পারে।

#### উদাহরণ:
```cs
class Employee
{
    public string Name { get; set; }
    
    public Employee(string name)
    {
        Name = name;
    }
}

class Department
{
    private List<Employee> _employees = new List<Employee>(); // Employee গুলি Department এর অংশ হলেও তারা স্বাধীন

    public void AddEmployee(Employee employee)
    {
        _employees.Add(employee);
    }

    public void ShowEmployees()
    {
        foreach (var employee in _employees)
        {
            Console.WriteLine(employee.Name);
        }
    }
}

class Program
{
    static void Main()
    {
        Employee emp1 = new Employee("Rahim");
        Employee emp2 = new Employee("Karim");

        Department dept = new Department();
        dept.AddEmployee(emp1); // Employee অবজেক্টগুলি Department এ যোগ করা হচ্ছে
        dept.AddEmployee(emp2);

        dept.ShowEmployees();  // সমস্ত কর্মচারীদের প্রদর্শন

        // যদি Department মুছে যায়, তবে Employee গুলি মুছে যাবে না, তারা অন্য কোথাও ব্যবহার হতে পারে
    }
}

```

- **মালিকানা**: `Department` ক্লাস `Employee` কে অ্যাগ্রিগেট করে, কিন্তু `Employee` অন্য কোথাও ব্যবহার হতে পারে বা অস্তিত্ব রাখতে পারে।
- **লাইফসাইকেল**: যদি `Department` অবজেক্টটি মুছে যায়, তবে `Employee` অবজেক্টগুলি **মুছে যাবে না** কারণ তারা স্বাধীন।

---

### মূল পার্থক্য:

1. **লাইফসাইকেল ডিপেন্ডেন্সি**:
    
    - **কম্পোজিশন**: অংশ অবজেক্ট (যেমন: `Engine`) পুরো অবজেক্ট (যেমন: `Car`) এর উপর নির্ভরশীল। পুরো অবজেক্টটি মুছে ফেললে, অংশ অবজেক্টও মুছে যাবে।
    - **অ্যাগ্রিগেশন**: অংশ অবজেক্ট (যেমন: `Employee`) পুরো অবজেক্ট (যেমন: `Department`) থেকে স্বাধীন। পুরো অবজেক্ট মুছে ফেললে, অংশ অবজেক্টগুলি অব্যাহত থাকে এবং অন্য কোথাও ব্যবহার হতে পারে।
2. **ক্লোজড কপ্লিং (Tight Coupling) vs লুজ কপ্লিং (Loose Coupling)**:
    
    - **কম্পোজিশন**: সম্পর্কটি **ক্লোজড কপ্লিং**। অংশ অবজেক্ট (যেমন: `Engine`) পুরো অবজেক্ট (যেমন: `Car`) এর সাথে দৃঢ়ভাবে সংযুক্ত থাকে।
    - **অ্যাগ্রিগেশন**: সম্পর্কটি **লুজ কপ্লিং**। অংশ অবজেক্ট (যেমন: `Employee`) পুরো অবজেক্ট (যেমন: `Department`) এর সাথে আলাদা থাকতে পারে।
3. **পুনঃব্যবহারযোগ্যতা**:
    
    - **কম্পোজিশন**: অংশ অবজেক্টটি পুরো অবজেক্টের বাইরে ব্যবহারযোগ্য নয়।
    - **অ্যাগ্রিগেশন**: অংশ অবজেক্টটি অন্য কোনো অবজেক্টে পুনরায় ব্যবহার করা যেতে পারে।

---

### আরও পরিষ্কার উদাহরণ:

#### **কম্পোজিশন (শক্তিশালী মালিকানা):**

```cs
class Car
{
    private Engine _engine = new Engine();

    public void Drive()
    {
        _engine.Start();
        Console.WriteLine("Car is moving...");
    }
}

class Engine
{
    public void Start() => Console.WriteLine("Engine started");
}

class Program
{
    static void Main()
    {
        Car car = new Car();
        car.Drive();

        // যদি Car মুছে যায়, তবে Engine মুছে যাবে, কারণ Car Engine এর মালিক
    }
}

```

- **যদি `car` মুছে যায়**, তবে `Engine` মুছে যাবে, কারণ `Engine` `Car` এর অংশ এবং এটি `Car` ছাড়া অস্তিত্ব রাখতে পারে না।

#### **অ্যাগ্রিগেশন (দুর্বল সম্পর্ক):**
```cs
class Department
{
    private List<Employee> _employees = new List<Employee>();

    public void AddEmployee(Employee employee)
    {
        _employees.Add(employee);
    }

    public void ShowEmployees()
    {
        foreach (var emp in _employees)
        {
            Console.WriteLine(emp.Name);
        }
    }
}

class Employee
{
    public string Name { get; set; }
    public Employee(string name) => Name = name;
}

class Program
{
    static void Main()
    {
        Employee emp1 = new Employee("Rahim");
        Employee emp2 = new Employee("Karim");

        Department dept = new Department();
        dept.AddEmployee(emp1);
        dept.AddEmployee(emp2);

        dept.ShowEmployees();

        // যদি Department মুছে যায়, তবে Employee গুলি মুছে যাবে না, তারা স্বাধীন অবজেক্ট
    }
}

```

- **যদি `dept` মুছে যায়**, `Employee` অবজেক্টগুলি মুছে যাবে না, কারণ তারা স্বাধীন অবজেক্ট এবং অন্য কোথাও ব্যবহার হতে পারে।

---

### উপসংহার:

- **কম্পোজিশন** মানে **শক্তিশালী মালিকানা**, যেখানে অংশ অবজেক্ট (যেমন: `Engine`) পুরো অবজেক্ট (যেমন: `Car`) এর উপর নির্ভরশীল এবং একে ছাড়া অস্তিত্ব রাখতে পারে না।
- **অ্যাগ্রিগেশন** মানে **দুর্বল মালিকানা**, যেখানে অংশ অবজেক্ট (যেমন: `Employee`) পুরো অবজেক্ট (যেমন: `Department`) থেকে স্বাধীন এবং অন্য কোথাও ব্যবহৃত হতে পারে।

