### **1. Static কী?**

**Static** keyword দিয়ে এমন কিছু declare করা হয় যা class-এর সাথে যুক্ত থাকে, instance-এর সাথে নয়। Static members class-level এ থাকে, এবং এগুলো instantiate না করেই সরাসরি ব্যবহার করা যায়।

#### **মূল পয়েন্টসমূহ**:

- Static members class-এর memory share করে।
- Static members সব instance-এর জন্য একই থাকে।
- Static members-কে সরাসরি **class name** দিয়ে access করা যায়।

#### **উদাহরণ**:

```cs
class Example
{
    public static int Count = 0;

    public Example()
    {
        Count++; // প্রতিবার object তৈরি করলে Count বাড়বে
    }
}

class Program
{
    static void Main()
    {
        Example ex1 = new Example();
        Example ex2 = new Example();
        Console.WriteLine(Example.Count); // Output: 2
    }
}

```


**বিঃদ্রঃ** Static-কে instance দিয়ে access করা যায় না।