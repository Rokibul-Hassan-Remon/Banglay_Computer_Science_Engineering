#### **Build Process-এ obj এবং bin ডিরেক্টরির ভূমিকা:**

1. **Intermediate File Management**:
    
    - Build করার সময় **C# Compiler** এবং **Linker** চূড়ান্ত Output তৈরি করতে **obj** ডিরেক্টরির ইন্টারমিডিয়েট ফাইলগুলো ব্যবহার করে।
    - এই ফাইলগুলো চূড়ান্ত Output ফাইল **Optimize** এবং **Link** করতে সাহায্য করে।
2. **Final Output Management**:
    
    - **bin** ডিরেক্টরি চূড়ান্ত Executable ফাইল বা Library সংরক্ষণ করার জন্য **Default Output Location** হিসেবে কাজ করে।

---

#### **Source Code এবং Build Output আলাদা রাখা:**

- **"obj"** এবং **"bin"** ডিরেক্টরি ব্যবহার করার মাধ্যমে:
    - Build সম্পর্কিত ফাইলগুলো **Source Code** থেকে আলাদা রাখা যায়।
    - **Source Code** এবং **Compiled Files** একসঙ্গে মিশে যাওয়ার ঝুঁকি কমে।
    - **Compiled Files**-এ **Accidental Modifications** এড়ানো যায়।

---
#### **উপসংহার:**

- **"obj" ডিরেক্টরি**: Build প্রসেসের জন্য প্রয়োজনীয় **ইন্টারমিডিয়েট ফাইল** সংরক্ষণ করে।
- **"bin" ডিরেক্টরি**: চূড়ান্ত **Executable file** বা **Library** সংরক্ষণ করে।
- এই ডিরেক্টরিগুলো Build প্রসেস সহজ করে এবং **Source Code** ও **Output Files** আলাদা রাখতে সাহায্য করে।