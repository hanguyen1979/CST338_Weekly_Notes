# Week 1 Notes - Java Primer

## Course Overview

### Who is this course for?
- Students with experience from about two programming classes.
- Expected knowledge:
  - Variables
  - Loops
  - If statements
  - Basic debugging
  - General understanding of programming
- Java experience is not required.

---

## Why Learn Java?

- Java is one of the most widely used programming languages.
- It is designed around Object-Oriented Programming (OOP).
- OOP helps create software that is:
  - Extensible
  - Robust
  - Well organized
- Java continues to be one of the most popular programming languages. 

---

## Goals of This Course

By the end of the course students should:

1. Improve Java programming skills.
2. Learn object-oriented design.
3. Build larger software projects.
4. Learn software development practices.
5. Create JavaFX applications.
6. Gain real programming experience. 

---

# Java Fundamentals

## Java is Strongly Typed

- Every variable has a declared data type.
- Variables must store values of the correct type.
- The compiler checks for type errors before the program runs.

### Example

```java
int age = 25;
String name = "Alice";
```

---

## Java Virtual Machine (JVM)

Java programs are compiled into byte code.

The bytecode runs on the Java Virtual Machine (JVM), allowing Java programs to run on different operating systems without changing the code.

---

# Java Files

## File and Class Names

A public class name **must exactly match** the filename.

Example:

```
Wk01_Demo.java
```

contains

```java
public class Wk01_Demo
```

If the names do not match, Java generates an error.

---

## Naming Matters

Java filenames are **case-sensitive**.

Example:

```
AnswerToTheQuestion.java
```

is **not** the same as

```
answerToTheQuestion.java
```

Always submit files using the exact filename requested.

---

## Classes and Packages

- Each class should be stored in its own file.
- Related classes can be organized into packages.

---

# Classes

A class contains:

- **Fields (Members)** — variables belonging to the class
- **Methods** — functions belonging to the class

---

## Access Modifiers

### public
Accessible from anywhere.

### private
Accessible only inside the class.

### protected
Accessible by subclasses and classes in the same package.

### Package-private
Accessible only within the same package.

---

# Primitive Data Types

Java provides primitive data types such as:

- byte
- short
- int
- long
- float
- double
- char
- boolean

Everything else is an **object**.

---

# Constructors

## What is a Constructor?

A constructor initializes an object when it is created using the **new** keyword.

Example:

```java
Dog myDog = new Dog();
```

The constructor:

- Has the same name as the class.
- Has no return type.
- Runs automatically when an object is created.
---

## Default Constructor

If no constructor is written, Java provides a default constructor automatically.
---

## Parameterized Constructor

Constructors can accept parameters.

Example:

```java
public Dog(String name) {
    this.name = name;
}
```

This allows objects to be initialized with different values.
---

## Constructor Overloading

A class may have multiple constructors with different parameter lists.

Example:

```java
Dog()

Dog(String name)

Dog(String name, int age)
```

Java chooses the correct constructor based on the arguments passed.

---

# The Main Method

Every Java application begins execution in:

```java
public static void main(String[] args)
```

Meaning of each keyword:

- **public** — accessible by the JVM
- **static** — belongs to the class
- **void** — returns nothing
- **String[] args** — command-line arguments
---

# Memory Management

Java does **not** have destructors.

Instead, Java automatically frees unused memory using **garbage collection**. 

---

# Lab 00 Goals

The first lab focuses on becoming comfortable with IntelliJ rather than writing complex Java programs.

Objectives:

- Download an IntelliJ project.
- Open an existing project.
- Install a JDK if needed.
- Run a Java project.
- Locate Java source files.
- Submit Java files correctly.

---

# Key Takeaways

- Java is an object-oriented, strongly typed language.
- Java programs run on the Java Virtual Machine (JVM).
- Public class names must exactly match filenames.
- Every class should be in its own file.
- Constructors initialize new objects.
- The `main()` method is the starting point of every Java application.
- Java automatically manages memory through garbage collection.
- Lab 00 is primarily about learning IntelliJ and the assignment submission process.

----

# Encapsulation

## What is Encapsulation?

Encapsulation is one of the four pillars of Object-Oriented Programming (OOP). It is the practice of hiding an object's internal data and only allowing controlled access through methods.

Benefits of encapsulation:
- Protects data from unintended changes.
- Makes code easier to maintain.
- Allows implementation details to change without affecting other code.

---

# Generics

## What are Generics?

Generics allow classes, methods, and collections to work with different data types while maintaining type safety.

Benefits of generics:
- Reduce code duplication.
- Catch type errors during compilation.
- Eliminate many type casts.
