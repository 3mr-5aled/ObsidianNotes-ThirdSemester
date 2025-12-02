## Introduction to Object-Oriented Programming (OOP)

**OOP** is a **programming paradigm** where a software system is represented as a collection of objects that interact with each other to solve a task.

> [!def] Object-Oriented Programming (OOP)
> A programming paradigm that models a system as a collection of interacting objects, captured from real-life examples like cars, mobiles, or PCs.

- OOP is captured from **real life**, where we constantly deal with different types of **objects**.
- All objects possess specific **attributes** (data) and **behavior** (operations).
- The primary goal of OOP is to address problems found in **Structured Programming (SP)**, such as **unrestricted access** to global data and **unrelated functions and data** (lack of real-world modeling).
### Classes and Objects
- **Class**: A user-defined **data type** that defines the **attributes** and **operations** (methods) of an object.
- **Object**: Variables of type class.
    - Every object is an **instance** of a class.
    - A program is essentially a set of objects communicating by sending **messages** (calling methods).

| Example Component | Type   | Details                                                                                                                |
| :---------------- | :----- | :--------------------------------------------------------------------------------------------------------------------- |
| **Student**       | Class  | Defines attributes like `+Name: String` and `+Grade: double`, and operations like `+Total() :double` and `+Display()`. |
| **Mark**          | Object | An instance of the `Student` class with specific attributes: `+Name="Mark"` and `+Grade=80.0`.                         |
| **Sally**         | Object | An instance of the `Student` class with specific attributes: `+Name="Sally"` and `+Grade=90.0`.                        |

### Main OOP Concepts (The Four Pillars)

The core concepts of OOP are often represented as the four pillars:
![[Pasted image 20251202214656.png]]
1. **Encapsulation**
2. **Abstraction**
3. **Inheritance**
4. **Polymorphism**

---

## Software Development Tools

Before Java, a typical software development process involved several tools:

- **Editor (IDE)**: Where the programmer writes the **source code**.
- **Compiler**: Translates the source code into **object code** (CPU-specific instructions).
	![[Pasted image 20251202214826.png]]
- **Linker**: Converts one or several object modules into an **executable program**.
	![[Pasted image 20251202214841.png]]
- **Debugger**: Helps find logical mistakes ("bugs") by stepping through the program in "slow motion".


---

## The Java Platform
![[Pasted image 20251202214859.png]]
**Java** is both **platform-independent** (the same program runs on any correctly implemented Java system) and **object-oriented** (structured in terms of classes).

### Java Platform Editions

The Java 2 Platform has three main editions:

- **J2SE** (Java 2 Platform, Standard Edition): Primarily focused on in this course.
- **J2ME** (Java 2 Platform, Micro Edition)
- **J2EE** (Java 2 Platform, Enterprise Edition)

### Java Installation Components
![[Pasted image 20251202214913.png]]
- **JDK (Java Development Kit)**: A superset that contains the **JRE**, **JVM**, and development tools. Its primary objective is to provide support for build and compilation.
- **JRE (Java Runtime Environment)**: Contains the **JVM** and all necessary libraries to run Java applications. It's enough to *run* an application.
- **JVM (Java Virtual Machine)**: The virtual engine that enables **byte code** support.

### How Java Code Runs
![[Pasted image 20251202214922.png]]
1. **Compile Time**: The **JDK** (containing the **Compiler**) translates **Java Code** (`MyDemo.java`) into **Byte Code** (`MyDemo.class`).
2. **Runtime**: The **JRE** (containing the **JVM**) executes the byte code:
    - **Class Loader**: Part of the JVM that loads the byte code.
    - **Bytecode Verifier**: Checks if the loaded byte code is valid and does not violate any security rules.
    - **Interpreter**: Reads the byte code stream and executes the program.
    - **JIT Code Generator** (Just-In-Time).

### Integrated Development Environments (IDEs)

An **IDE** is software that helps programmers develop software. Popular IDEs include:

- **IntelliJ IDEA** (most popular at 65%).
- **Eclipse** (48%).
- **VSCode** (27%).
- **NetBeans** (13%).

---

## Packages and I/O Operations

### Packages in Java

A **Package** is a group of related classes.

- **Naming**: To guarantee a unique name, use the reverse of a company's Internet domain name (e.g., `oracle.com` becomes `com.oracle`).
- **Nesting**: Packages can be nested.
- **Standard Packages**: Include `java.*` (like `java.lang`, `java.util`, `java.net`) and `javax.*`.
- **Importing**: A class can use all classes from its own package and all **public** classes from other packages. The `import` keyword is used to access public classes in other packages:
    - `import java.util.Date;` (Single class import)
    - `import java.util.*;` (All classes in a package)
- **Name Conflict Resolution**: If classes with the same name exist in two imported packages, the fully qualified name must be used (e.g., `java.util.Date deadline;`).

### Displaying Outputs
![[Pasted image 20251202214948.png]]
Java provides three primary methods via `System.out` for displaying output:

- **`System.out.print(...)`**: Shows the value passed to it without a newline.
- **`System.out.println(...)`**: Shows the value followed by a **new line**.
- **`System.out.printf(...)`**: Shows the value with a specific **format**.
    - **Format Specifiers** (`%parameter`): Used to format output.
        - `%d`: decimal integer.
        - `%,d`: decimal integer with thousand separators (e.g., 1,000).
        - `%.1f`: decimal notation for float/double, rounded to the nearest decimal place (e.g., `%.1f` rounds to 1 decimal).
        - `%s`: string.
        - `%n`: produces a newline, same as `\n`.

### Reading Input from User (Scanner Class)

To read input from the console, the **Scanner** class from the `java.util` package is used:

1. **Import**: `import java.util.Scanner;`
2. **Create Object**: `Scanner input = new Scanner(System.in);`
3. **Read Input**: Use the suitable Scanner method based on the data type:
    - `int x = input.nextInt();`
    - `float f = input.nextFloat();`
    - `String s = input.next();`
    - `char c = input.next().charAt(0);`

---

## Key Concepts & Definitions

> [!def] Object  
> An entity with particular behavior and attributes; a variable that is an instance of a class.

> [!def] Class  
> A user-defined data type that serves as a blueprint, defining the attributes and operations (behavior) for objects.

> [!def] Byte Code  
> An intermediate code generated by the Java Compiler that is platform-independent and executed by the Java Virtual Machine (JVM).

> [!def] JDK (Java Development Kit)  
> A superset of tools including the JRE, JVM, and development tools, primarily used for building and compiling Java applications.

> [!def] IDE (Integrated Development Environment)  
> Computer software designed to help programmers develop software, often including an editor, compiler, and debugger.

---

## 💡 Actionable Summary

- **OOP** models real-life scenarios by representing systems as interacting **objects** defined by **classes** (which possess attributes and operations).
- The four core pillars of OOP are **Encapsulation**, **Abstraction**, **Inheritance**, and **Polymorphism**.
- Java's **platform independence** is achieved through the **JVM** executing **Byte Code**, with the **JDK** and **JRE** providing the necessary environment for development and running, respectively.
- Use **`System.out.println()`** for simple output with a newline, and **`System.out.printf()`** for formatted output (e.g., controlling decimal places or adding thousand separators).
- User input is handled by importing the **Scanner** class (`import java.util.Scanner;`) and using methods like `nextInt()`, `nextFloat()`, or `next()` on a Scanner object.
