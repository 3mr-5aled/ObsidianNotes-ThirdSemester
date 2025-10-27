# 🧠 OOP – Lecture 3: Methods and Strings

**Instructor:** Mohamed Mabrouk  
**Course:** Object-Oriented Programming  
**Lecture Focus:** Methods, Constructors, and Strings in Java

---

## 🧩 Lecture Outline
1. Methods  
2. Method Types  
3. Modifiers (static, final, abstract)  
4. Method Overloading  
5. Parameter Passing  
6. Constructors & `this` Keyword  
7. `main()` Method  
8. Object Destruction (Garbage Collection)  
9. Strings  
10. String Operations and Comparison  

---

## 1️⃣ Methods

**Definition:**  
A **method** is a block of code that performs a specific task and can be invoked when needed.

### Structure
Each method has:
- **Header:** Declares name, parameters, and return type, modifier 
- **Body:** Defines logic and operations

**Syntax:**
```java
<Modifier> ReturnType MethodName(ParamList) {
    // method body
}
```

---

## 2️⃣ Method Types

- **Instance Methods:** Belong to an object (non-static)
    
- **Class Methods (Static):** Belong to the class itself
    
- **Constructors:** Special methods used for object initialization
    
- **Main Method:** Entry point of Java applications
    

---

## 3️⃣ Method Modifiers

### Access Modifiers

|Modifier|Visibility|Usage|
|---|---|---|
|`private`|Within same class only|Encapsulation|
|_(none)_|Package-level|Default scope|
|`protected`|Same class + subclasses|Inheritance use|
|`public`|Everywhere|Global access|

**Example:**

```java
protected int add(int num1, int num2) {
 return num1 + num2; 
}
```
### Other Modifiers

- `static`: Belongs to class, not instance.
    
- `final`: Cannot be overridden by subclasses.
    
- `abstract`: Must be overridden in subclass (no body).
    
---

## 4️⃣ Static Members

**Definition:** Shared by all instances of a class.

**Key Points:**

- Accessed using the **class name** (`ClassName.method()`).
    
- Can only access other static members.
    
- The `main()` method **must** be static.
    

**Example – Instance Counter:**

```java
public class Student {
    static int count = 0;
    public Student() { count++; }
    public static void displayCount() {
        System.out.println("Number of students: " 
        + count);
    }
}
```

---

## 5️⃣ Method Calls

**Syntax:**

```java
reference.method(arguments);
```

- Static → `ClassName.method()`
    
- Non-static → `object.method()`
    

**Example:**

```java
TestClass.method1();
TestClass obj = new TestClass();
obj.method2();
```

---

## 6️⃣ Method Overloading

**Definition:**  
Multiple methods with the **same name** but **different parameter lists**.

**Rules:**

- *Return type alone cannot overload a method*.
    
- *Parameter type* or *count* **must differ**.
    

**Example:**

```java
int add(int a, int b) { return a + b; }
int add(int a, int b, int c) { return a + b + c; }
float add(float x, float y) { return x + y; }
```

---

## 7️⃣ Parameter Passing

Java uses **pass-by-value** for all parameters.

- For **primitive types**, *values are copied.*
    
- For **objects**, the *reference is copied* (object itself not duplicated).
    

**Example 1 – Changes Affect Original:**

```java
public static void changeName(Student s) {
    s.setName("B");
}
```

**Example 2 – New Object** [Does Not ] **Affect Original:**

```java
public static void changeName(Student s) {
    s = new Student();
    s.setName("B");
}
```

**Concept:**  
→ Fields of the same object can be modified, but you *cannot make it point to a new memory address.*

---

## 8️⃣ `this` Keyword

**Definition:** Refers to the **current object** instance.

**Usage 1 – Resolve Shadowing:**

```java
public Student(String name, float marks) {
    this.name = name;
    this.marks = marks;
}
```

**Usage 2 – Constructor Chaining:**

```java
public Student(String name) {
    this(name, 0.0F);
}
```

---

## 9️⃣ The `main()` Method

**Structure:**

```java
public static void main(String[] args)
```

**Meaning:**

- `public`: Accessible by JVM from anywhere.
    
- `static`: No instance required to invoke.
    
- `String[] args`: Used for passing runtime arguments.
    

**Example:**

```java
public class Greetings {
    public static void main(String[] args) {
        String name = args[0];
        System.out.println("Hello " + name);
    }
}
```

Run via terminal:

```
java Greetings Mohamed
```

---

## 🔟 Destroying Objects (Garbage Collection)

**Triggered When:**

- Reference is set to `null`.
    
- Reference points to another object.
    

**Force GC (Not Recommended):**

```java
System.gc();
```

Garbage collector deletes unreferenced objects **automatically**.

---

## 🔠 Strings in Java

### Overview

- Sequence of characters enclosed in `" "`.
    
- Reference type (not primitive [ Object ] ).
    
- **Immutable** → Value cannot be changed once created.
    

**Example:**

```java
String str = "Hello";
char[] chars = {'H', 'i'};
String s1 = new String();
String s2 = new String(str);
String s3 = new String(chars);
```

---

## 🔄 String Conversion

To convert any object to string, **override** `toString()`:

```java
public String toString() {
    return name + " - " + marks;
}
```

---

## ⚖️ String Comparison

### Using ` == `

- Compares **references**, not contents.
    

### Using `equals()`

- Compares **content** of two strings.
    

### Using `compareTo()`

Returns:

- `0` → equal
    
- `<0` → first < second
    
- `>0` → first > second
    

**Example:**

```java
String s1 = "Hello";
String s2 = "Hi";
int val = s1.compareTo(s2);
System.out.println(val);
```

---

## 🧰 Useful String Methods

|Method|Description|
|---|---|
|`substring(start, end)`|Extract substring|
|`indexOf(str)`|Returns index or -1|
|`lastIndexOf(str)`|Searches from end|
|`replace(old, new)`|Replaces substring|
|`split(delimiter)`|Splits string|
|`startsWith(prefix)`|Checks beginning|
|`endsWith(suffix)`|Checks ending|
|`toUpperCase()`|Converts to uppercase|
|`toLowerCase()`|Converts to lowercase|
|`charAt(index)`|Returns character at index|

---

## 🧩 Glossary

|Term|Meaning|
|---|---|
|**Method Header**|Part defining name, parameters, return type|
|**Static**|Belongs to the class, not instance|
|**Constructor**|Initializes object|
|**Immutable**|Cannot be changed after creation|
|**Overloading**|Multiple methods with same name but different parameters|
|**Garbage Collection**|Automatic memory cleanup|
|**this**|Reference to current object|

---

## 💡 Real-World Applications

- **Static counters** for tracking number of users or sessions.
    
- **Overloaded methods** in APIs (e.g., `print()` in `System.out`).
    
- **String methods** used in data validation, text processing, and file I/O.
    

---

## 🧠 Mnemonics

- **PAST** for method modifiers:  
    `P`rivate, `(A)`ccess default, `S`tatic, `T`ransient (extra for memory)
    
- **CEO** for method structure:  
    **C**all, **E**xecute, **O**utput
    

---

## ❓ Thought-Provoking & Exam Questions

1. Explain how `this` keyword helps resolve variable shadowing.
    
2. Why can’t Java use pass-by-reference?
    
3. What happens when two strings with identical content are compared using ` == `?
    
4. Give an example of method overloading and explain how the compiler differentiates them.
    
5. Explain why strings are immutable and how that affects memory.
    
6. What is the role of `String[] args` in `main()`?
    
7. How does garbage collection enhance memory management in Java?
    

---

## 🧭 Summary

- Methods encapsulate functionality and improve reusability.
    
- Modifiers control visibility and inheritance.
    
- Overloading enables polymorphism at compile time.
    
- Java passes all parameters by value.
    
- `this` helps reference current instance and call constructors.
    
- The `main()` method acts as the program entry point.
    
- Garbage collection manages memory automatically.
    
- Strings are immutable and manipulated via methods like `equals()` and `compareTo()`.
    

---

## 🧩 Concept Mind Map (Text Format)

```
OOP Lecture 3
├── Methods
│   ├── Types: Instance, Static, Constructors, Main
│   ├── Modifiers: Access + Other (static, final, abstract)
│   ├── Calls: ClassName.method(), object.method()
│   ├── Overloading
│   └── Parameters (pass-by-value)
├── this Keyword
│   ├── Shadowing resolution
│   └── Constructor chaining
├── main() Method
│   ├── public, static, String[] args
│   └── Command-line arguments
├── Garbage Collection
│   ├── Null reference
│   ├── Re-assignment
│   └── System.gc()
└── Strings
    ├── Immutable nature
    ├── Comparison (==, equals, compareTo)
    └── Useful methods (substring, replace, split, etc.)
```

---

**End of Lecture 3 Notes – Methods and Strings**
