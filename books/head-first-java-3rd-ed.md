# Head First Java 3rd Edition

Make it Stick

- **Java is Pass by value**
- **Wash Cat**
- **threads wait() notify()**

## 1. Dive In: A Quick Dip

### The way Java works

The goal is to write one application and have it work on whatever device your friends have.

1. **Source:** Create a source document. Use an established protocol (in this case, the Java language).

2. **Compiler:** Run your document through a source code compiler. The compiler checks for errors and won’t let you compile until it’s satisfied that everything will run correctly.

3. **Output (code):** The compiler creates a new document, coded into Java **bytecode**. Any device capable of running Java will be able to interpret/translate this file into something it can run. The compiled bytecode is platform-independent.

4. **Virtual Machines:** Your friends all have a Java **virtual** machine (JVM), implemented in software, running inside their electronic gadgets. When your friends run your program, the virtual machine reads and runs the bytecode.

### Code structure in Java

- In a source file, put a **class**.
- In a class, put **methods**.
- In a method, put **statements**.

### Writing a class with a main()

In Java, everything goes in a **class**. You’ll type your source code file (with a *.java* extension), then compile it into a new class file (with a *.class* extension). When you run your program, you’re really running a class.

Running a program means telling the Java Virtual Machine (JVM) to “Load the **HelloWorld** class, then start executing its **main()** method. Keep running ’til all the code in main is finished.”

The **main()** method is where your program starts running.

No matter how big your program is (in other words, no matter how many *classes* your program uses), there’s got to be a **main()** method to get the ball rolling.

```java
class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello, World!"); 
  }
}
```

## 2. Classes and Objects: A Trip to Objectville

### Thinking about objects

When you design a class, think about the objects that will be created from that class type. Think about:

- Things the object *knows*
- Things the object *does*

Things an object *knows* about itself are called **instance variables** (state).
Things an object can *do* are called **methods** (behavior).

> Think of **instance** as another way of saying **object**.

### A class is not an object (but it’s used to construct them)

**A class is a blueprint for an object.** It tells the virtual machine how to make an object of that particular type. Each object made from that class can have its own values for the instance variables of that class.

## 3. Primitives and References: Know Your Variables

- There is actually no such thing as an **object** variable.
- There’s only an object **reference** variable.
- An object reference variable holds bits that represent a way to **access** an object.
- It doesn’t hold the object itself, but it holds something like a pointer. Or an address. Except, in Java we don’t really know what is inside a reference variable. We do know that whatever it is, it represents one and only one object. And the JVM knows how to use the reference to get to the object.

> An object reference is just another variable value

### The 3 steps of object declaration, creation an assignment

``` java
Dog myDog = new Dog();
```

#### 1. Declare a reference variable

```java
Dog myDog
```

Tells the JVM to allocate space for a reference variable, and names that variable ``myDog``. The reference variable is, forever, of type Dog. In other words, a remote control that has buttons to control a Dog, but not a Cat or a Button or a Socket.

#### 2. Create an object

```java
new Dog();
```

Tells the JVM to allocate space for a new Dog object on the **heap**.

#### 3. Link the object and the reference

```java
=
```

Assigns the new Dog to the reference variable ``myDog``.

### Arrays are objects too

You can have an array object that’s declared to hold primitive values. In other words, the array object can have elements that are primitives, but the array itself is never a primitive. **Regardless of what the array holds, the array itself is always an object!**

### 3rd Chapter's Bullet Points

- Variables come in two flavors: primitive and reference.
- Variables must always be declared with a name and a type.
- A primitive variable value is the bits representing the value (5, ‘a’, true, 3.1416, etc.).
- A reference variable value is the bits representing a way to get to an object on the heap.
- A reference variable is like a remote control. Using the dot operator (.) on a reference variable is like pressing a button on the remote control to access a method or instance variable.
- A reference variable has a value of ``null`` when it is not referencing any object.
- An array is always an object, even if the array is declared to hold primitives. There is no such thing as a primitive array, only an array that *holds* primitives.

## 4. Methods *Use* Instance Variables: How Objects Behave

**State affects behavior,** *behavior affects state.* We know that objects have **state** and **behavior**, represented by **instance variables** and **methods**.

Depending on your programming background and personal preferences, *you* might use the term *arguments* or perhaps *parameters* for the values passed into a method. Although there *are* formal computer science distinctions that people who wear lab coats (and who will almost certainly not read this book) make, we have bigger fish to fry in this book. So *you* can call them whatever you like (arguments, donuts, hair - balls, etc.) but we’re doing it like this:

A caller **passes** arguments. A method **takes** parameters.

Arguments are the things you pass into the methods. An **argument** (a value like 2, Foo, or a reference to a Dog) lands face-down into a...wait for it...**parameter**. And a parameter is nothing more than a local variable. A variable with a type and a name that can be used inside the body of the method.

### Pass-by-Value in Action

Java follows a pass-by-value approach when arguments are passed to methods. This means a copy of the data is passed, not the original data itself.

#### Example 1: Primitive Data Types (int)

```java
public class PassByValueDemo {
  public static void main(String[] args) {
    int x = 5; // Original value

    System.out.println("Before changeValue: x = " + x);
    changeValue(x); // Pass a copy of x
    System.out.println("After changeValue: x = " + x);
  }

  public static void changeValue(int y) {
    y = 10; // Modify the copy (doesn't affect original x)
  }
}
```

1. `x` is assigned the value 5.
2. `changeValue` is called, passing a copy of `x` (the value 5).
3. Inside `changeValue`, `y` (the copy) is modified to 10.
4. However, this change only affects the copy within the method, not the original `x` in `main`.
5. Printing `x` before and after the call shows its value remains 5.

##### Key Point: Pass-by-value for primitives ensures the original data in the calling method remains untouched

#### Example 2: Objects (Pass-by-Reference of Object References)

```java
public class PassByValueDemo {
  public static void main(String[] args) {
    Person person = new Person("Alice", 25); // Create a Person object

    System.out.println("Before changeName: " + person.getName() + ", " + person.getAge());
    changeName(person); // Pass the reference (copy) of person
    System.out.println("After changeName: " + person.getName() + ", " + person.getAge());
  }

  public static void changeName(Person p) {
    p.setName("Bob"); // Modify the object's name (affects original person)
  }
}

class Person {
  private String name;
  private int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  // getters and setters for age (not shown for brevity)
}
```

1. A `Person` object `person` is created.
2. `changeName` is called, passing a copy of the reference to `person` (imagine the reference as a pointer to the object's location in memory).
3. Inside `changeName`, modifications to `p` (which refers to the same object as `person`) affect the original object's attributes (`name` in this case).
4. Printing before and after calling `changeName` shows the object's `name` is indeed changed to "Bob".

##### Key Point: While Java uses pass-by-value, for objects, the reference copy allows modifications within the method to affect the original object

### 4th Chapter's Bullet Points

- **Encapsulation** gives you control over who changes the data in your class and how.
- Make an instance variable *private* so it can’t be changed by accessing the variable directly.
- Create a *public* mutator method, e.g., a setter, to control how other code interacts with your data. For example, you can add validation code inside a setter to make sure the value isn’t changed to something invalid.
- *Instance* variables are assigned values by default, even if you don’t set them explicitly.
- *Local* variables, e.g., variables inside methods, are not assigned a value by default. You always need to initialize them.
- Use == to check if two primitives are the same value.
- Use == to check if two references are the same, i.e., two object variables are actually the same object.
- Use .equals() to see if two objects are equivalent (but not necessarily the same object), e.g., to check if two String values contain the same characters.

## 5. Writing a Program: Extra-Strength Methods

### 5th Chapter's Bullet Points

- Your Java program should start with a high-level design.
- Typically you’ll write three things when you create a new class:
  - **prep code**
  - **test code**
  - **real (Java) code**
- Prep code should describe *what* to do, not *how* to do it. Implementation comes later.
- Use the prep code to help design the test code.
- A class can have one superclass only.
- Write test code *before* you implement the methods.
- Choose *for* loops over *while* loops when you know how many times you want to repeat the loop code.
- The enhanced for loop is an easy way to loop over an array or collection.
- Use the *increment* operator to add 1 to a variable (x++;).
- Use the *decrement* operator to subtract 1 from a variable (x--;).
- Use *break* to leave a loop early (i.e., even if the boolean test condition is still true).

## 6. Get to Know the Java API: Using the Java Library

### 6th Chapter's Bullet Points

- **ArrayList** is a class in the Java API.
- To put something into an ArrayList, use **add().**
- To remove something from an ArrayList use **remove().**
- To find out where something is (and if it is) in an ArrayList, use **indexOf().**
- To find out if an ArrayList is empty, use **isEmpty().**
- To get the size (number of elements) in an ArrayList, use the **size() *method*.**
- To get the **length** (number of elements) in a regular old array, remember, you use the **length *variable*.**
- An ArrayList **resizes dynamically** to whatever size is needed. It grows when objects are added, and it **shrinks** when objects are removed.
- You declare the type of the array using a **type parameter**, which is a type name in angle brackets.
- Although an ArrayList holds objects and not primitives, the compiler will automatically “wrap” (and “un-wrap” when you take it out) a primitive into an Object and place that object in the ArrayList instead of the primitive.
- Classes are grouped into packages.
- A class has a full name, which is a combination of the package name and the class name. Class ArrayList is really java.util.ArrayList.
- To use a class in a package other than java.lang, you must tell Java the full name of the class.
- You can either use an import statement at the top of your source code, or you can type the full name every place you use the class in your code.

## 7. Inheritance and Polymorphism: Better Living in Objectville

### A Subclass Extends a Superclass

This means a new class (subclass) inherits properties from an existing class (superclass). Imagine a class `Vehicle` with properties like `engine` and `wheels`. A `Car` class can **extend** `Vehicle` to inherit those properties and add car-specific ones like `doors` and `seats`.

```java
public class Vehicle {
  // common properties for all vehicles
  private String engine;
  private int wheels;

  // getters and setters for engine and wheels
}

public class Car extends Vehicle {
  // specific properties for Cars
  private int doors;
  private int seats;

  // getters and setters for doors and seats
}
```

### Subclasses Inherit Public Variables and Methods from Superclass

A subclass can access and use *public* members (variables and methods) of the superclass. However, private members are hidden and cannot be directly accessed. In the `Car` class, it can use the `engine` and `wheels` (assuming they are public) but not any *private* variables in `Vehicle`.

### Inherited methods can be overridden; instance variables cannot be overridden

Sometimes, a subclass might need to provide a different implementation for an inherited method. This is called overriding. For example, a `RaceCar` class might override the `move()` method from `Car` to include features like acceleration.

Redefining instance variables (changing their values) is possible, but it's not technically overriding. It's generally better to add new instance variables in the subclass for specific needs.

```java
public class RaceCar extends Car {
  private int horsepower;

  @Override // indicates method is overriding
  public void move() {
    super.move(); // call the original move() from Car
    System.out.println("️ Accelerating with " + horsepower + " horsepower!");
  }
}
```

### Use the IS-A test to verify inheritance hierarchy

This means if `X extends Y`, then you should be able to say "An X IS-A Y". In our example, a `Car` is a type of `Vehicle`. This makes sense because a Car inherits all the properties of a Vehicle and adds its own.

### The IS-A relationship works in only one direction

A `Car` is an `Vehicle`, but not all `Vehicles` are `Cars`. This clarifies that inheritance is a specific relationship. A subclass inherits from a superclass, not the other way around.

### When a method is overridden, the overridden version is called

When you call a method on an object of the subclass, the subclass's version (if it exists) is executed. This is called runtime polymorphism. Imagine creating a `RaceCar` object and calling `move()`. The `RaceCar`'s overridden `move()` method with the additional acceleration message will be called.

### Transitive inheritance

This point builds on the previous ones. If `B extends A` and `C extends B`, then `B` inherits from `A` and `C` inherits from both `B` and `A`. This creates a chain of inheritance where `C` can access public members of both `A` and `B`.

### Keeping The Contract: Rules for Overriding

1. **Inheritance:**  The subclass (child class) must inherit the method from the superclass (parent class) in order to override it. Methods that are not inherited cannot be overridden.

2. **Method Signature:** The overriding method must have the same name and parameter list (number, order, and type of parameters) as the method it overrides in the superclass. This ensures that calls to the method are routed correctly based on the object's type at runtime (polymorphism).

3. **Return Type:** The overriding method can have the same return type or a subtype of the return type declared in the superclass. This allows for more specific return types in subclasses if needed. (Covariant return types introduced in Java 5.0)

4. **Access Modifier:** The access modifier (public, protected, private) of the overriding method cannot be more restrictive than the overridden method. For instance, a public method in the superclass cannot be overridden with a private method in the subclass.

5. **Final Methods:** Methods declared as `final` in the superclass cannot be overridden in subclasses. This prevents unintended changes to core functionalities.

6. **Static vs Instance Methods:** Static methods cannot be overridden but can be redeclared in subclasses. Instance methods, on the other hand, are the ones that can be overridden.

7. **Exceptions:** The overriding method can throw any unchecked exceptions, regardless of whether the overridden method throws exceptions or not. However, it cannot throw new or broader checked exceptions than the ones declared by the overridden method.

8. **Using `super` Keyword:** You can use the `super` keyword within the overriding method to call the overridden method from the superclass. This can be useful if you want to extend the functionality of the superclass method while adding your own specific behavior.

### Overloading a method

Method overloading is nothing more than having two methods with the same name but different argument lists. Period. There’s no polymorphism involved with overloaded methods!

1. **The return types can be different:** You’re free to change the return types in overloaded methods, as long as the argument lists are different.

2. **You can’t change ONLY the return type:** If only the return type is different, it’s not a valid over*load*—the compiler will assume you’re trying to over*ride* the method. And even *that* won’t be legal unless the return type is a subtype of the return type declared in the superclass. To overload a method, you MUST change the argument list, although you can change the return type to anything.
3. **You can vary the access levels in any direction:** You’re free to overload a method with a method that’s more restrictive. It doesn’t matter, since the new method isn’t obligated to fulfill the contract of the overloaded method.
