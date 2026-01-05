---
course: Object-Oriented Programming
lecture: Lists, Generics, and Stream APIs
date: 2025-12-07
tags:
  - subject
  - lecture
  - university
  - notes
---
> [!note] **Overview**
> This lecture introduces **Java Lists**, **ArrayList**, **Generics**, **overriding equals**, and the **Stream API**, emphasizing type safety, correct element access, and functional-style processing. It covers practical pitfalls, best practices, and modern Java workflows for handling collections.

---

## ⭐ Core Concepts

### 1. Lists  
🟢 **Basic**

> [!note] **Definition**
> A **List** is an ordered collection in Java that preserves **insertion order**.  
> Key implementations: **ArrayList**, **LinkedList**.

- **Ordered ≠ Sorted**
  - Ordered → items stay in the sequence they were inserted  
  - Sorted → items follow a comparison rule

> [!example]  
> `["Hi", "Greetings", "Hello"]` stays in this order unless modified.

---

## 2. ArrayList  
🟢 **Basic**

> [!note]  
> **ArrayList** is a dynamically resizable array that implements the **List** interface.

### Key Features
- Auto-resizable  
- Random access via indices  
- Supports `get(i)`, `set(i, obj)`, `indexOf(element)`, `contains(element)`  
- Preserves insertion order  
- Iterable using enhanced for-loops  
- Supports sorting via `sort()`

#### Example
```java
ArrayList strings = new ArrayList();
strings.add("Hi");
strings.add("Greetings");
strings.add("Hello");

for(Object obj : strings){
    String str = (String) obj; // manual unboxing
    System.out.println(str);
}
```

> [!warning]  
> Without generics, **manual casting (unboxing)** is required.  
> Mixing types can throw **ClassCastException**.

---

## 3. Incorrect ArrayList Usage (Without Generics)

🟡 **Intermediate**

### Problem Scenario

```java
ArrayList items = new ArrayList();
items.add("John Smith");
items.add(10.5F);
items.add(new Student(4, "Jane Doe", 59.5F));

for(Object obj : items){
    String item = (String) obj; // error occurs here
}
```

> [!warning]  
> **Incorrect unboxing** → trying to cast a Float or Student to a String.

### Output

```
John Smith
Exception in thread "main" java.lang.ClassCastException: Float cannot be cast to String
```

---

## 4. Generics

🟡 **Intermediate**

> [!note] **Definition**  
> **Generics enforce compile-time type safety**, restricting a collection to store only one data type.

### Benefits

- Prevents invalid types from being added
    
- No manual casting needed
    
- Eliminates `ClassCastException` at runtime
    

### Generic ArrayList Example

```java
ArrayList<String> strings = new ArrayList<>();
strings.add("Hi");
strings.add("Greetings");
strings.add("Hello");

for(String str : strings){
    System.out.println(str);
}
```

> [!tip] **Mnemonic — “R U S Safe?”**  
> **R**estricts type  
> **U**nboxing not required  
> **S**afer code  
> **Safe** = fewer runtime errors

---

## 5. Overriding equals

🟡 **Intermediate**

### Why override it?

By default, Java compares objects using **memory addresses**.  
To check for **logical equality**, you must override `equals`.

### Without Overriding equals

```java
int index = students.indexOf(new Student(2, "Jane Doe", 59.5F));
System.out.println(index); // -1
```

Different objects → different memory addresses → List cannot find match.

### Overridden equals Example

```java
@Override
public boolean equals(Object obj) {
    Student otherStudent = (Student) obj;
    return this.id == otherStudent.id;
}
```

> [!example]  
> Now `indexOf(new Student(2, ...))` → returns correct index `1`.

> [!tip]  
> Always override `hashCode()` when overriding `equals()` in real-world applications.

---

## 6. Stream API

🟡 **Intermediate**

> [!note]  
> Stream APIs treat collections as **pipelines of data**, enabling operations like **filter**, **map**, **reduce**, and **forEach**.

### Traditional Filtering

```java
for(String str : strings){
    if(str.startsWith("H")){
        System.out.println(str);
    }
}
```

### Stream API Equivalent

```java
strings.stream()
    .filter(str -> str.startsWith("H"))
    .forEach(System.out::println);
```

Output:

```
Hi
Hello
```

> [!tip]  
> **Mnemonic: “SFF”** for basic stream usage  
> **S**tream → **F**ilter → **F**orEach

### Challenge from Lecture

> [!question]  
> _Use streams to compute total marks of students with marks > 50._

> [!example]
> 
> ```java
> float total = students.stream()
>     .filter(s -> s.getMarks() > 50)
>     .map(s -> s.getMarks())
>     .reduce(0f, Float::sum);
> ```
> 

---

## 🔗 Continuity with Previous Lectures

- Builds on earlier topics:
    
    - **Objects & classes** → needed for Student examples
        
    - **Methods** → required for overriding equals
        
    - **Collections** → extended through Lists & ArrayList
        
- Introduces **functional programming** concepts foundational for future material (map/reduce).
    

---

## 🧩 Hands-On Practice

1. Create an ArrayList of Students and:
    
    - Add 5 Student objects
        
    - Sort by marks
        
    - Filter by grade (> 70)
        
    - Print the top scorer
        
2. Modify equals to compare by **name** instead of **id**.
    
3. Build a stream pipeline that:
    
    - Filters names starting with “A”
        
    - Converts them to uppercase
        
    - Prints final results
        

---

## 📘 Lecture Questions (from slides)

- _Can you change equals to check equality via name field?_
    
- _Can you use stream APIs with a list of Student objects and calculate the total marks of all students with marks > 50?_
    

---

## 🗺 Concept Hierarchy Diagram

```mermaid
mindmap
  root((Lists & Streams))
    Lists
      List Interface
      ArrayList
        get/set
        indexOf
        contains
    Generics
      Type Safety
      No Unboxing
    equals()
      Address Comparison
      Logical Equality
    Stream API
      filter
      forEach
      Pipelines
```

---

## 📚 Glossary

- **List** – Ordered Java collection preserving insertion order
    
- **ArrayList** – Dynamic array implementation of List
    
- **Generics** – Type-safe mechanisms restricting allowed data types
    
- **equals()** – Object method for logical comparison
    
- **Stream API** – Functional operations on collections (filter, map, reduce)
    

---

## 🎯 Key Takeaways

- Lists store ordered, index-accessible elements.
    
- ArrayList is flexible but dangerous without generics.
    
- Generics prevent runtime casting errors.
    
- `equals()` must be overridden for logical equality.
    
- Stream API simplifies filtering and processing collections.
    

---

## 🧾 Quick Review Card

**Q:** Why does `indexOf()` return −1 without overriding equals?  
**A:** Because objects are compared by memory address, not field values.

**Q:** What’s the main advantage of generics?  
**A:** Compile-time type safety and no need for casting.

**Q:** What does `filter()` do in streams?  
**A:** Selects elements that satisfy a condition.

**Q:** What error occurs with wrong casting in ArrayList?  
**A:** `ClassCastException`.

**Q:** Which methods form the basic stream pipeline?  
**A:** `stream() → filter() → forEach()`.

---

## 📖 Further Resources

- _Effective Java_ — Joshua Bloch (Generics & equals best practices)
    
- Oracle Java Docs: Collections and Streams
    
- JetBrains Academy: Java Functional Programming Modules
    