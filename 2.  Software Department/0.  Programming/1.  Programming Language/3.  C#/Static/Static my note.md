

### **স্ট্যাটিক কনসেপ্টস - নোটস**

#### **Static Variable**

- **Static** মানে **স্থির**।
- একটি ক্লাসে যতগুলো অবজেক্টই তৈরি করা হোক না কেন, একটি **static variable**-এর জন্য সকল অবজেক্ট **একই instance শেয়ার করবে**।
- **Static variables** ক্লাসের সাথে সম্পর্কিত, অবজেক্টের সাথে নয়।
- **Instance variables** প্রতিটি অবজেক্টের জন্য আলাদা, কিন্তু **static variables** পুরো ক্লাসের জন্য একটাই হয়।

---

#### **Static Class**

- **Static** মানে **স্থির**।
- একটি ক্লাস যদি **static** ঘোষণা করা হয়, তবে:
    1. এই ক্লাসটি থেকে কোনো অবজেক্ট তৈরি করা যায় না।
    2. ক্লাসের ফিল্ড ও মেথড সরাসরি ক্লাসের নাম ধরে ব্যবহার করতে হয়।
    3. **Static class** শুধুমাত্র **static members** রাখতে পারে।
- **Static class** সাধারণত utility বা helper ফাংশনগুলোর জন্য ব্যবহৃত হয়।

### **Static Class**

- যেমন আগে বলেছি, **static** মানে **স্থির**।
- যদি কোনো ক্লাসের আগে **static** লেখা থাকে, তাহলে সেই ক্লাসটি স্থির হয়ে যায়।
- আমরা জানি, ক্লাস হচ্ছে অবজেক্ট তৈরির **blueprint**।
- কিন্তু, যখন একটি **class static** হয়:
    - আমি যদি ১০০টা অবজেক্ট তৈরি করি, তাহলে সেই সমস্ত অবজেক্টের **field (data type variable)** এর value একই থাকবে।
    - তাই ১০০টা অবজেক্ট তৈরি করার কোনো অর্থ থাকে না, কারণ সবার মান একই থাকবে।
    - **Static ক্লাস** আমাদের এই কষ্ট থেকে মুক্তি দেয় কারণ এটি অবজেক্ট তৈরি করার প্রয়োজনীয়তা সরিয়ে ফেলে।
- **Static class**-এর **field** এবং **property** সরাসরি ব্যবহার করা যায়, অবজেক্ট তৈরির প্রয়োজন হয় না।
- সাধারণ ক্লাসে **object** তৈরি করে **dot ('.')** দিয়ে ফিল্ড অ্যাক্সেস করতে হয়, কিন্তু **static ক্লাস**-এর ক্ষেত্রে তা দরকার হয় না।

---

**নোট:** Static ক্লাস সাধারণত এমন ক্ষেত্রে ব্যবহার করা হয়, যেখানে একটি নির্দিষ্ট কার্যকলাপ বা utility ফাংশন সরাসরি ক্লাসের মাধ্যমে একাধিক জায়গায় ব্যবহৃত হয়।

**উদাহরণ:**
```cs
public static class MathUtils
{
    public static int Add(int a, int b) => a + b;
}

```


**ব্যবহার:**
```cs
int result = MathUtils.Add(5, 3);

```



---

#### **Static Constructor**

- **Static constructor** এমন একটি constructor যা প্রথম **static member** অ্যাক্সেস করার সময় একবারই চালিত হয়।
- এটি **static fields** বা **resources** এর প্রাথমিক মান সেট করার জন্য ব্যবহৃত হয়।
- **Static constructor**-এ কোনো প্যারামিটার থাকে না এবং এটি সরাসরি কল করা যায় না।

**ব্যবহার:**
```cs
public static class DatabaseConnection
{
    public static string ConnectionString { get; }

    static DatabaseConnection()
    {
        ConnectionString = "Server=...;Database=...;";
    }
}

```

---

#### **Main Method কেন Static হয়?**

- **Main method** হল প্রোগ্রামের এন্ট্রি পয়েন্ট।
- এটি **static** হয় কারণ প্রোগ্রাম চালানোর জন্য অবজেক্ট তৈরি করার প্রয়োজন নেই।
- **Main method**-কে সরাসরি ক্লাসের নাম ধরে **runtime**-এ কল করা হয়।

---
### **স্ট্যাটিক ক্লাস এবং স্ট্যাটিক কন্সট্রাক্টর**

#### **Static ক্লাসের Field এবং Property**

1. **Static ক্লাসের সকল field এবং property অবশ্যই static হতে হবে।**
    
    - Static ক্লাসে non-static member রাখা যাবে না।
    - যদি **static keyword** ব্যবহার না করা হয়, তাহলে **compiler error** আসবে।
2. **Static field অ্যাক্সেস করতে হলে ক্লাসের নাম ধরে কল করলেই হবে।**
    
    - কোনো অবজেক্ট তৈরি করার প্রয়োজন হয় না।

---

#### **Main Function কেন Static হয়?**

1. **Main Function** হল প্রোগ্রামের এন্ট্রি পয়েন্ট।
2. এটি **static** হয় কারণ:
    - **Main Function**-এর বাইরে কোনো অবজেক্ট তৈরি করা সম্ভব নয়।
    - Static না হলে, ক্লাসের property বা method কল করার আগে অবজেক্ট তৈরি করতে হতো, যা Main Function-এর ক্ষেত্রে সম্ভব নয়।
3. **Static Main Function** সরাসরি **runtime**-এ ক্লাসের নাম ধরে কল করা যায়।

---

#### **Static Constructor**

1. **Static Constructor** শুধুমাত্র একবারই চালিত হয়।
    
    - যখন প্রথমবার **static member** অ্যাক্সেস করা হয় বা ক্লাস প্রথমবার ব্যবহৃত হয়, তখন এটি স্বয়ংক্রিয়ভাবে চালিত হয়।
2. **Static Constructor**-এ কোনো প্যারামিটার রাখা যায় না।
    
    - এটি নিজে থেকে কল করা যায় না, এবং এটি সম্পূর্ণরূপে **runtime**-এর নিয়ন্ত্রণে।
3. **ব্যবহার:**
    
    - **Static fields**-এর প্রাথমিক মান সেট করতে।
    - **Shared resources** (যেমন ডেটাবেজ কানেকশন, configuration setup) প্রাথমিকভাবে সেট করতে।

---

#### **সমস্যা:**

- যদি অবজেক্ট তৈরি করার আগেই ডেটাবেজ কানেকশন সেটআপ করতে হয়, তাহলে কিভাবে করব?

#### **সমাধান:**

- **Static Constructor**-এর মাধ্যমে ডেটাবেজ কানেকশন সেট করা যায়।
- এতে প্রথমবার ক্লাস ব্যবহারের আগেই ডেটাবেজ কানেক্ট হয়ে যাবে।

---

### **উদাহরণ:**
```cs
public static class DatabaseConnection
{
    public static string ConnectionString { get; }

    // Static Constructor
    static DatabaseConnection()
    {
        ConnectionString = "Server=localhost;Database=MyDB;";
    }
}

// Accessing the ConnectionString
string conn = DatabaseConnection.ConnectionString;


```

#### **Static vs Non-Static ক্লাস এবং মেথডের পার্থক্য**

|বিষয়|Static|Non-Static|
|---|---|---|
|**Object Creation**|প্রয়োজন নেই|প্রয়োজন আছে|
|**Members**|শুধুমাত্র static members থাকে|static এবং non-static থাকে|
|**Access**|ক্লাসের নাম ধরে কল করা হয়|অবজেক্টের মাধ্যমে কল করা হয়|


Class object (reference type)  store in stack. 
Struct(value type) stores in heap. 

Enum :
Enum is a special data type.

enum DaysofWeek{
Monday,
Sunday,
Saturday
Tuesday 
Wednesday 
Thursday 
Friday
}
by default এখানে 0 থেকে এগুলোর value সেট হয়ে গেছে। চাইলে  এই ভেলু গুলো সেট করা যায়। 
enum DaysofWeek{
Monday =3
Sunday =6
Saturday=4
Tuesday= 7
Wednesday =2
Thursday =1
Friday=5
}

এখন ধরো আমি কিছু enum এর কিছু value set করলাম। কিন্তু বাকিগুলা করলাম না তাহলে কি হবে? 
soln: 
enum DaysofWeek{
Monday 3,
Sunday,
Saturday
Tuesday 
Wednesday 
Thursday 
Friday
}
এখন এখানে 3 এর পর থেকে এক এক করে value বাড়তে থাকবে। 

যদি এমন হয় তাহলে কি হবে? 
enum DaysofWeek{
Monday=8, 
Sunday=1008,
Saturday
Tuesday 
Wednesday 
Thursday 
Friday
}
তাহলে যেহেতু sunday =1008 এর পর যেহেতু আর কিছু লেখা নাই তাই এর পর থেকে এক এক করে বৃদ্ধি পাবে। 


এই daysofWeek এর length কিন্তু fixed. ুটা আর চেন্জ করা যাবে না। 

enum datatype র value প্রিন্ট করার সময় convertকরে নিতে হবে 
যেমন:string d= daysofWeek. Sunday;
Console.WriteLine(d.ToString()); 

Enum তখনই করা লাগে যখন if else condition wise   আমাদের difderentiate করা লাগবে তখনই এটা use করা লাগাবে। 
String convert to enum
Use Enum.parse(datatypeof(),container)

