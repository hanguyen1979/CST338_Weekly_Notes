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
