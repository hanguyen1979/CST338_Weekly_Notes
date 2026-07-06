# Override Methods & Inheritance (Java)

## Learning Objectives

* Understand why `==` does not work for comparing object contents.
* Learn how and why to override `equals()`, `hashCode()`, and `toString()`.
* Understand the purpose of the `@Override` annotation.
* Learn the basics of inheritance using `extends` and `implements`.
* Understand Java access modifiers.

---

# 1. Every Class Can Have a `main()` Method

Any Java class can contain a `main()` method.

```

Having a `main()` method allows the class to be run independently.

---

# 2. Why `==` Doesn't Work for Objects

## Primitive Types

For primitive values, `==` compares the actual values.

```

## Objects

For objects, `==` compares **references (memory locations)**, **not the contents**.


**Remember:**

* `==` → same object?
* `equals()` → same contents?

---

# 3. Never Use `==` to Compare String Contents

---

# 4. The `equals()` Method

Every Java object inherits an `equals()` method from `Object`.

Override it to define what makes two objects equal.

```

Without overriding `equals()`, Java only compares object references.

---

# 5. The `hashCode()` Method

Whenever you override `equals()`, you **must also override `hashCode()`.**

IntelliJ can generate both automatically.

# 6. The `toString()` Method

When you print an object:

```java
System.out.println(object);
```

Java automatically calls:

```java
object.toString();
```

Without overriding it, Java prints something like:

```
Rectangle@7cca494b
```

which is based on the object's hash code.

Example override:

```java
@Override
public String toString() {
    return "Rectangle{" +
            "width=" + width +
            ", height=" + height +
            '}';
}
```

# 7. The `@Override` Annotation

`@Override` tells the compiler that you are replacing an inherited method.

Benefits:

* Prevents spelling mistakes
* Checks the method signature
* Makes code easier to understand

---

# 8. Inheritance

Inheritance allows one class to reuse another class's code.

There are two forms:

## Extending a Class

```java
public class Dog extends Animal {

}
```

## Implementing an Interface

```java
public class Rectangle implements Shape {

}
```

Uses the keyword:

```
implements
```

---

# 9. UML Notation
extends: solid line  
implements: dashed line

The arrow points toward the parent class or interface.

---

# 10. Method Signature

A method's signature consists of:

* Method name
* Parameter list

It **does not include the return type.**

Example:

```java
public void draw()

public void draw(int size)
```

These are different signatures.

---

# 11. Common Methods to Override

Most Java classes commonly override:

* `toString()`
* `equals()`
* `hashCode()`

---

# 12. IntelliJ Shortcut

Generate these methods automatically

---

# Key Takeaways

* `==` compares object references, not contents.
* Use `equals()` to compare object values.
* Always override `hashCode()` when overriding `equals()`.
* Override `toString()` to display meaningful object information.
* Use `@Override` whenever overriding inherited methods.
* Inheritance allows code reuse through `extends` or `implements`.
* IntelliJ can automatically generate `equals()`, `hashCode()`, and `toString()`.

---

# Lecture 14 – Inheritance (Java)

## Learning Objectives

* Understand inheritance and class hierarchies.
* Use `super` and `this` correctly.
* Apply the `protected` access modifier.
* Understand polymorphism and dynamic binding.
* Learn abstract classes and abstract methods.
* Understand the `Object` class.
* Use `HashMap<K, V>` for key-value storage.

---

# 1. Inheritance

## Definition

Inheritance allows one class to **reuse fields and methods** from another class.

```java
public class Book extends Product {

}
```

### Terminology
Superclass:  Parent/Base clasS
Subclass:  Child/Derived class

### Benefits

* Reuse code
* Avoid duplication
* Easier maintenance
* Override behavior
* Add new fields and methods

> **Inheritance models an "is-a" relationship.**

---

# 2. The `this` Keyword

`this()` calls **another constructor in the same class**.

```

Rules:

* Must be the **first statement** in a constructor.
* Cannot be used after another statement.
* Cannot be used together with `super()` in the same constructor.

---

# 3. The `super` Keyword

`super()` calls a constructor in the parent class.

```

### Rules

* Must be the **first line** in the constructor.
* Constructors are **not inherited**.
* If omitted, Java automatically inserts:

```java
super();
```

provided the parent has a no-argument constructor.

---

# 4. Access Modifiers with Inheritance

Private members should be accessed through getters/setters.

---

# 5. Overriding Methods

A subclass can replace an inherited method.

Requirements:

* Same method name
* Same parameters
* Same return type

```

Use `@Override` to help the compiler detect mistakes.

`super.toString()` reuses the parent implementation.

---

# 6. Don't Break Existing Code

When modifying constructors:

* Keep backward compatibility.
* Existing subclasses may rely on `super()`.
* Unit tests help detect problems.

---

# Lecture 09 – Static Methods & Static Variables

## Learning Objectives

After completing this lecture, you should be able to:

* Understand static variables and static methods.
* Explain the difference between static and instance members.
* Use the `Math` class.
* Understand wrapper classes, boxing, and unboxing.
* Use the `var` keyword.
* Understand static methods in interfaces.
* Use common static methods in the `Character` class.

---

# 1. Static Variables

## Definition

A **static variable** belongs to the **class**, not to individual objects.

```java
private static int numOfCarsMade;
```

An **instance variable** belongs to each object created with `new`.

---

# 2. The `this` Keyword

`this` refers to the **current object**.

```

If you see `this`, there must be an object instance.

### Why `this` Doesn't Work in Static Methods

Static methods belong to the class, not to an object.

```

# 3. Declaring Static Variables

```java
private static int count;
```

Good practice:

* Make static variables `private`.
* Access them through methods.

All objects share the same value.

---

# 4. Example of Static Variables

```java
public class CarMade {

    private static int numOfCars = 0;

    public void demoMethod() {
        numOfCars++;
    }

    public void outputCount() {
        System.out.println(numOfCars);
    }
}

---

# 5. Static Constants

A symbolic constant uses:

```java
public static final int BIRTH_YEAR = 1982;
```

Meaning:

* `public` → accessible everywhere
* `static` → belongs to the class
* `final` → cannot change

Use:

```java
int year = MyClass.BIRTH_YEAR;
```

instead of creating an object.

---

# 6. Static Methods

A static method belongs to the class.

Syntax:

```java
public static returnType methodName(...) {

}
```

Call it using:

```java
ClassName.methodName();
```

Example:

```java
Temperature.toCelsius(32);
```

No object is needed.

---

# 7. The `Math` Class

The `Math` class is entirely static.

No import statement is required.

---

# 8. Wrapper Classes

Wrapper classes convert primitive types into objects.
Wrapper classes include many useful static methods and constants.

---

# 9. Boxing

Convert a primitive into an object.

---

# 10. Unboxing

Convert an object back into a primitive.

---

# 11. Wrapper Constants

Useful predefined constants:

---

# 12. Wrapper Static Methods

Convert Strings to numbers:

```java
Integer.parseInt("42");

Double.parseDouble("19.95");

Float.parseFloat("3.14");
```

Convert numbers to Strings:

```java
Double.toString(123.45);
```

---

# 13. The `var` Keyword (Java 10+)

`var` lets Java infer the variable type.

```java
var count = 10;

var name = "Bob";

var list = new ArrayList<>();
```

Rules:

* Local variables only
* Must initialize immediately
* Cannot be fields
* Cannot be method parameters

---

