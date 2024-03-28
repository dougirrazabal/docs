# Head First Java 3rd Edition

Make it Stick

- **Java is Pass by value**
- **Wash Cat**
- **threads wait() notify()**

## 1. Breaking the Surface

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

### Bullet Points

- Variables come in two flavors: primitive and reference.
- Variables must always be declared with a name and a type.
- A primitive variable value is the bits representing the value (5, ‘a’, true, 3.1416, etc.).
- A reference variable value is the bits representing a way to get to an object on the heap.
- A reference variable is like a remote control. Using the dot operator (.) on a reference variable is like pressing a button on the remote control to access a method or instance variable.
- A reference variable has a value of ``null`` when it is not referencing any object.
- An array is always an object, even if the array is declared to hold primitives. There is no such thing as a primitive array, only an array that *holds* primitives.

## 4. Methods *Use* Instance Variables How Objects Behave

**State affects behavior,** *behavior affects state.* We know that objects have **state** and **behavior**, represented by **instance variables** and **methods**.

Depending on your programming background and personal preferences, *you* might use the term *arguments* or perhaps *parameters* for the values passed into a method. Although there *are* formal computer science distinctions that people who wear lab coats (and who will almost certainly not read this book) make, we have bigger fish to fry in this book. So *you* can call them whatever you like (arguments, donuts, hair - balls, etc.) but we’re doing it like this:

A caller **passes** arguments. A method **takes** parameters.

Arguments are the things you pass into the methods. An **argument** (a value like 2, Foo, or a reference to a Dog) lands face-down into a...wait for it...**parameter**. And a parameter is nothing more than a local variable. A variable with a type and a name that can be used inside the body of the method.
