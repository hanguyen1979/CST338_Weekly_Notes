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

```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);      // false
System.out.println(s1.equals(s2)); // true
```

**Remember:**

* `==` → same object?
* `equals()` → same contents?

---

# 3. Never Use `==` to Compare String Contents

---

# 4. The `equals()` Method

Every Java object inherits an `equals()` method from `Object`.

Override it to define what makes two objects equal.

Example:

```java
@Override
public boolean equals(Object o) {
    if (this == o) {
        return true;
    }

    if (!(o instanceof Rectangle rectangle)) {
        return false;
    }

    return width == rectangle.width &&
           height == rectangle.height;
}
```

Without overriding `equals()`, Java only compares object references.

---

# 5. The `hashCode()` Method

Whenever you override `equals()`, you **must also override `hashCode()`.**

IntelliJ can generate both automatically.

Example:

```java
@Override
public int hashCode() {
    return Objects.hash(width, height);
}
```

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

| Relationship | UML Arrow   |
| ------------ | ----------- |
| extends      | solid line  |
| implements   | dashed line |

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

Generate these methods automatically:

```
Right Click
    ↓
Generate...
    ↓
toString()

or

Generate...
    ↓
equals() and hashCode()
```

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

| Term       | Meaning             |
| ---------- | ------------------- |
| Superclass | Parent/Base class   |
| Subclass   | Child/Derived class |

### Benefits

* Reuse code
* Avoid duplication
* Easier maintenance
* Override behavior
* Add new fields and methods

> **Inheritance models an "is-a" relationship.**

Example:

```
Book is a Product
Software is a Product
```

---

# 2. The `this` Keyword

`this()` calls **another constructor in the same class**.

```java
public Product() {
    this("", "", 0.0);
}
```

Rules:

* Must be the **first statement** in a constructor.
* Cannot be used after another statement.
* Cannot be used together with `super()` in the same constructor.

---

# 3. The `super` Keyword

`super()` calls a constructor in the parent class.

```java
public Book() {
    super();
}
```

Or pass arguments:

```java
public Book(String code,
            String description,
            double price,
            String author) {

    super(code, description, price);
    this.author = author;
}
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

Example:

```java
@Override
public String toString() {
    return super.toString()
            + "Author: " + author;
}
```

Use `@Override` to help the compiler detect mistakes.

`super.toString()` reuses the parent implementation.

---

# 6. Constructor Errors

Problem:

```java
class Sandwich {
    public Sandwich(String filling) {

    }
}

class Burger extends Sandwich {

}
```

Java automatically tries:

```java
super();
```

But `Sandwich()` doesn't exist.

Result:

```
Compile Error
```

Solutions:

### Option 1

Add a no-argument constructor.

```java
public Sandwich() {

}
```

### Option 2

Call the parent constructor explicitly.

```java
public Burger() {
    super("burger patty");
}
```

---

# 7. Don't Break Existing Code

When modifying constructors:

* Keep backward compatibility.
* Existing subclasses may rely on `super()`.
* Unit tests help detect problems.

---

# 8. HashMap

A `HashMap` stores **key-value pairs**.

```java
HashMap<String, Integer> map =
        new HashMap<>();
```

* Keys are unique.
* Values may repeat.
* Fast lookup.

---

## Common Methods

### put()

```java
map.put("Apple", 5);
```

Adds or updates a key.

### get()

```java
int qty = map.get("Apple");
```

Returns the value.

Missing keys return:

```java
null
```

---

## Useful HashMap Methods

```java
put()
get()
remove()
containsKey()
containsValue()
keySet()
entrySet()
values()
size()
```

Important:

* Cannot use primitive types (`int`, `double`) as generic types.
* Use wrapper classes:

```
Integer
Double
Boolean
Character
```

---

# 9. Enhanced For Loop

Instead of:

```java
for(int i=0;i<list.size();i++){

}
```

Use:

```java
for(String name : names){

}
```

For HashMaps:

```java
for(String key : map.keySet()){

}
```

Or:

```java
for(Map.Entry<String,Integer> entry : map.entrySet()){

}
```

Cleaner and easier to read.

---

# 10. Polymorphism

Meaning:

> One interface, many forms.

Example:

```java
Product p = new Book();
```

Valid because:

```
Book IS-A Product
```

Benefits:

* General code
* Flexible programs
* Easy to add new subclasses

---

# 11. Dynamic Binding

Example:

```java
Product p = new Book();
```

Static type:

```
Product
```

Dynamic type:

```
Book
```

Calling:

```java
p.toString();
```

executes:

```
Book.toString()
```

because Java chooses the method at **runtime**, not compile time.

---

# 12. Casting

## Upcasting (Safe)

```java
Product p = new Book();
```

Automatic.

---

## Downcasting

```java
Book b = (Book)p;
```

Requires explicit cast.

Can throw:

```
ClassCastException
```

Safer:

```java
if(p instanceof Book b){

}
```

---

# 13. The `final` Keyword

## Final Variable

Cannot change.

```java
final double PI = 3.14159;
```

---

## Final Method

Cannot be overridden.

```java
public final double getTax(){

}
```

---

## Final Class

Cannot be extended.

```java
public final class Employee{

}
```

Examples:

* String
* Math
* Integer

---

# 14. The Object Class

Every Java class ultimately extends:

```java
Object
```

Important inherited methods:

```java
toString()

equals()

hashCode()

clone()

getClass()
```

Example:

```java
public class Person {

}
```

is equivalent to:

```java
public class Person extends Object {

}
```

---

# 15. Abstract Classes

Declare with:

```java
public abstract class Product {

}
```

Characteristics:

* Cannot instantiate.
* Used only as a parent class.
* Can contain fields and regular methods.
* Can contain abstract methods.

Example:

```java
Product p = new Product();
```

Compile Error.

---

# 16. Abstract Methods

No implementation.

```java
public abstract void example();
```

Rules:

* Only inside abstract classes.
* Subclasses must implement them.
* Otherwise the subclass must also be abstract.

---

# 17. Benefits of Abstract Classes

* Prevent creating incomplete objects.
* Define common behavior.
* Force subclasses to implement required methods.
* Support polymorphism.
* 
---

# Remember:

* `super()` must be first.
* Constructors are not inherited.
* Always use `@Override`.
* Upcasting is safe.
* Downcasting requires care.
* Dynamic binding chooses methods at runtime.
* Abstract classes cannot be instantiated.
* `HashMap` stores key-value pairs.
* Use wrapper classes (`Integer`, `Double`) instead of primitives in generics.

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

### Static vs Instance Variables

| Static Variable                | Instance Variable            |
| ------------------------------ | ---------------------------- |
| Belongs to the class           | Belongs to each object       |
| One copy shared by all objects | Each object has its own copy |
| Declared with `static`         | No `static` keyword          |
| Accessed using the class name  | Accessed through an object   |

---

# 2. The `this` Keyword

`this` refers to the **current object**.

Example:

```java
this.name = name;
```

If you see `this`, there must be an object instance.

### Why `this` Doesn't Work in Static Methods

Static methods belong to the class, not to an object.

```java
public static void demo() {
    System.out.println(this.name);   // ERROR
}
```

Error:

```text
cannot be referenced from a static context
```

There is no current object, so there is no `this`.

---

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
```

Each call to `demoMethod()` increases the same shared variable.

Even if multiple objects are created:

```java
CarMade object1 = new CarMade();
CarMade object2 = new CarMade();
```

both modify the same `numOfCars`.

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

# 7. Rules for Static Methods

A static method:

Can access static variables

Can call other static methods

Cannot access instance variables

Cannot call instance methods directly

Example:

```java
public static void method() {

}
```

Cannot do:

```java
this.name
```

because there is no object.

---

# 8. The `Math` Class

The `Math` class is entirely static.

No object:

```java
Math math = new Math();   // Wrong
```

Use directly:

```java
Math.sqrt(25);
```

No import statement is required.

---

## Common Constants

```java
Math.PI
Math.E
```

Example:

```java
double area = Math.PI * radius * radius;
```

---

## Useful Math Methods

Examples:

```java
Math.pow(2,3);      // 8

Math.sqrt(1764);    // 42

Math.abs(-42);      // 42

Math.ceil(41.3);    // 42.0

Math.floor(42.7);   // 42.0

Math.round(41.57);  // 42
```

---

# 9. Wrapper Classes

Wrapper classes convert primitive types into objects.
Wrapper classes include many useful static methods and constants.

---

# 10. Boxing

Convert a primitive into an object.

```java
Integer number = Integer.valueOf(42);
```

Automatic boxing:

```java
Integer number = 42;
```

---

# 11. Unboxing

Convert an object back into a primitive.

```java
int value = number.intValue();
```

Automatic unboxing:

```java
int value = number;
```

---

# 12. Wrapper Constants

Useful predefined constants:

```java
Integer.MAX_VALUE

Integer.MIN_VALUE

Double.MAX_VALUE

Double.MIN_VALUE

Boolean.TRUE

Boolean.FALSE
```

---

# 13. Wrapper Static Methods

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

# 14. The `var` Keyword (Java 10+)

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

Invalid:

```java
var x;

var y = null;

private var count = 5;
```

---

# 15. Static Methods in Interfaces (Java 8+)

Interfaces can define static utility methods.

```java
public interface Calculable {

    double calculate(double x, double y);

    static double applyTax(double amount){
        return amount * 1.0825;
    }
}
```

Call:

```java
Calculable.applyTax(100);
```

Implementing classes cannot override interface static methods.

---

# 16. Pattern Matching with `instanceof` (Java 16+)

Old syntax:

```java
if(obj instanceof String){
    String s = (String)obj;
}
```

Modern syntax:

```java
if(obj instanceof String s){
    System.out.println(s.toUpperCase());
}
```

Benefits:

* No explicit cast
* Cleaner code
* Safer

---

# 17. Character Class

Useful static methods include:

```java
Character.isLetter(c);

Character.isDigit(c);

Character.isUpperCase(c);

Character.isLowerCase(c);

Character.isWhitespace(c);

Character.toUpperCase(c);

Character.toLowerCase(c);
```

These methods are commonly used for input validation and string processing.

---

# 18. `main()` Method

Any Java class can contain:

```java
public static void main(String[] args)
```

This is the most common use of a static method because Java can call it without creating an object.

---

