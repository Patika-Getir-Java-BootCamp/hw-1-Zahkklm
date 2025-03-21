# Homework #1

## 1. Why do we need to use OOP? Some major OOP languages?

### Why use OOP?
- **Modularity**: Code is organized into classes and objects, making it easier to maintain and modify.
- **Reusability**: Through inheritance and composition, you can reuse existing code.
- **Encapsulation**: Hides internal state and functionality, exposing only what’s necessary.
- **Polymorphism**: Allows a single interface to control different underlying forms (methods or classes).
- **Abstraction**: Simplifies complex realities by modeling classes appropriate to the problem.

### Major OOP Languages
- **Java**
- **C++**
- **C#**
- **Python** (though it supports multiple paradigms, including OOP)
- **Ruby**
- **JavaScript** (prototypal inheritance)

---

## 2. Interface vs Abstract Class

### Interface
- Contains only abstract methods (in older Java versions) and static/final fields.
- A class can implement multiple interfaces.
- Defines a contract (what methods must be implemented), but not how they are implemented (though Java 8+ allows default methods).

### Abstract Class
- Can contain both abstract and concrete methods.
- Can have instance variables and constructors.
- A class can only extend one abstract class (single inheritance).
- Useful when you want to share common state and behavior among subclasses.

---

## 3. Why do we need `equals` and `hashCode`? When to override?

- **`equals`**: Determines logical equality between objects. By default, `equals` in `Object` checks reference equality (i.e., same memory address). You override it to define equality based on object fields.
- **`hashCode`**: Used in hash-based collections like `HashMap`, `HashSet`, etc. If two objects are equal according to `equals`, they must have the same `hashCode`.
- **When to override**: 
  - When you need to compare objects logically (e.g., same “value” or same fields) rather than by memory reference.
  - Always override `hashCode` if you override `equals` to maintain the contract between them.

---

## 4. Diamond Problem in Java? How to fix it?

- **What is it?**  
  In multiple inheritance scenarios (like C++), a class can inherit from two classes that share a common base class, creating ambiguity for methods/fields. Java avoids multiple class inheritance, so this typically arises with interfaces that have default methods.
- **How to fix**:  
  Java requires you to explicitly override the conflicting default methods in your class, providing your own implementation (or choosing one of the parent interface’s default methods).

---

## 5. Why do we need a Garbage Collector? How does it run?

- **Why needed**:  
  - Automates memory management.  
  - Frees developers from manual memory allocation/deallocation.  
  - Prevents memory leaks and dangling pointers.
- **How it runs**:
  - The JVM’s garbage collector periodically scans objects that are no longer reachable from any live references and reclaims their memory.
  - Different GC algorithms (e.g., Mark-Sweep, G1, etc.) vary in performance and strategy.

---

## 6. Java `static` Keyword Usage

- **`static` field**: Shared among all instances of a class.
- **`static` method**: Belongs to the class, not tied to any instance, can be called without creating an object.
- **`static` block**: Used for static initialization of a class.
- **`static` inner class**: A nested class that doesn’t require an instance of the outer class.

---

## 7. Immutability: What Does It Mean? Where, How, and Why to Use It?

- **Meaning**: An immutable object’s state cannot be changed after construction.
- **Where**:
  - Commonly used in data transfer objects, value objects, and thread-safe designs.
- **How**:
  - Declare fields as `private final`.
  - Provide no setters (or any methods that modify fields).
  - Initialize fields in the constructor.
- **Why**:
  - Simplifies reasoning about code, especially in multi-threaded environments.
  - Reduces bugs related to changing state.

---

## 8. Composition and Aggregation: Meanings and Differences

- **Composition**:
  - Strong form of relationship: “has-a” with ownership.
  - If the container object is destroyed, the composed objects are also destroyed.
  - Example: A `Car` has an `Engine` (the engine cannot exist independently of the car).

- **Aggregation**:
  - Weaker form of relationship: “has-a” without ownership.
  - If the container object is destroyed, the contained object can still exist elsewhere.
  - Example: A `Team` has `Players`, but a player can exist on different teams.

---

## 9. Cohesion and Coupling: Meanings and Differences

- **Cohesion**:
  - The degree to which the elements inside a module/class belong together.
  - High cohesion means the class focuses on a single task or closely related tasks.

- **Coupling**:
  - The degree of interdependence between modules/classes.
  - Low coupling means changes in one class have minimal impact on other classes.

### Ideal Scenario
- **High cohesion** and **low coupling**.

---

## 10. Heap and Stack: Meanings and Differences

- **Stack**:
  - Memory area for method execution and local variables.
  - Grows/shrinks with method calls/returns.
  - Variables stored on the stack have a short lifetime (method scope).

- **Heap**:
  - Memory area for dynamic allocation of objects.
  - Objects live on the heap until they are no longer referenced (then garbage collected).
  - More flexible, but also more expensive to manage.

---

## 11. Exception: What Is It? Types of Exceptions?

- **What**: An exception is an event that disrupts the normal flow of a program’s execution.
- **Types**:
  1. **Checked Exceptions**: Subclass of `Exception` (excluding `RuntimeException`). Must be either caught or declared in the method signature using `throws`.
     - Example: `IOException`, `SQLException`.
  2. **Unchecked Exceptions**: Subclass of `RuntimeException`. Not required to be caught or declared.
     - Example: `NullPointerException`, `ArrayIndexOutOfBoundsException`.
  3. **Error**: Serious problems that are usually not handled by typical applications.
     - Example: `OutOfMemoryError`.

---

## 12. How to Summarize “Clean Code” as Short as Possible?

- **Clean code**: Code that is **readable, maintainable, and efficient**, following consistent conventions, simple design, and meaningful naming, with minimal duplication.

---

## 13. What Is Method Hiding in Java?

- **Method hiding** occurs when a **static method** in a subclass has the same signature as a static method in the superclass.  
- It’s not the same as overriding (which applies to instance methods). Instead, the subclass’s static method **hides** the superclass’s static method.

---

## 14. Difference Between Abstraction and Polymorphism in Java

- **Abstraction**:
  - Focuses on **what** a class or method does, rather than **how** it does it.
  - Achieved through abstract classes and interfaces.
  - Reduces complexity by hiding implementation details.

- **Polymorphism**:
  - Allows objects to be represented as instances of their parent type (or interface) and to behave differently based on their actual (runtime) type.
  - Achieved primarily through **method overriding** (dynamic binding).
  - Promotes flexibility in code by allowing different implementations to be swapped in.




