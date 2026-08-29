<!-- TOC START -->
**Table of Contents** — 9 subtopics · 84 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [OOP Concepts (Inheritance & Polymorphism)](#oop-concepts-inheritance--polymorphism-45) | 45 |
| 2 | [Java Programming & Methods](#java-programming--methods-11) | 11 |
| 3 | [Class Design & Object-Oriented Modeling](#class-design--object-oriented-modeling-7) | 7 |
| 4 | [Encapsulation & Access Modifiers](#encapsulation--access-modifiers-6) | 6 |
| 5 | [Constructors & Destructors](#constructors--destructors-5) | 5 |
| 6 | [Output Tracing & Recursion](#output-tracing--recursion-3) | 3 |
| 7 | [Exception Handling](#exception-handling-3) | 3 |
| 8 | [C++ OOP Concepts & Friend Functions](#c-oop-concepts--friend-functions-2) | 2 |
| 9 | [Interfaces & Abstract Classes](#interfaces--abstract-classes-2) | 2 |

<!-- TOC END -->

---

## OOP Concepts (Inheritance & Polymorphism) (45)

1. Explain the concepts of Inheritance and Polymorphism in Java. Write a Java program to demonstrate method overriding. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer: Inheritance is the mechanism by which one class acquires the members of another class, expressing an "is-a" relationship and allowing code to be reused. Polymorphism is the ability of one interface to take many forms, so that the same method call behaves differently depending on the object it acts upon.

   Inheritance is the mechanism by which one class acquires the data members and member functions of another class. The class that is inherited from is called the base, parent or superclass, and the class that inherits is called the derived, child or subclass. It expresses an "is-a" relationship: a Dog is an Animal, a SavingsAccount is an Account.

   Advantages:
   - Reuse of code: common members are written once in the base class and are available to every derived class.
   - Extensibility: new functionality is added in a derived class without touching or retesting the base class.
   - It enables run-time polymorphism, because a base-class reference can hold a derived-class object.
   - It makes the design match the real-world hierarchy, so the code is easier to understand and maintain.
   - It reduces duplication, which reduces the chance of inconsistent bug fixes.

   Types of inheritance:

   - Single inheritance: one derived class inherits from one base class.
     A -> B

   - Multilevel inheritance: a derived class itself becomes the base of another class, forming a chain.
     A -> B -> C

   - Hierarchical inheritance: several derived classes inherit from one common base class.
     A -> B, A -> C, A -> D

   - Multiple inheritance: one derived class inherits from more than one base class.
     A, B -> C
     Supported by C++ and Python. Java does not support it for classes, in order to avoid the diamond problem, but it allows a class to implement several interfaces.

   - Hybrid inheritance: a combination of two or more of the above, for example hierarchical together with multiple inheritance. This is the arrangement in which the diamond problem arises.

   Example in Java:

   ```java
   class Vehicle {
       String brand;
       void start() { System.out.println(brand + " is starting"); }
   }

   class Car extends Vehicle {
       int doors;
       void openBoot() { System.out.println("Boot opened"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Car c = new Car();
           c.brand = "Toyota";
           c.doors = 4;
           c.start();       // inherited from Vehicle
           c.openBoot();    // its own method
       }
   }
   ```

   Access rules: public members of the base class remain public in the derived class, protected members are accessible inside the derived class, and private members are inherited but are not directly accessible; they can be reached only through public or protected methods of the base class.

   The keyword: extends in Java, and a colon with an access specifier in C++, for example class Car : public Vehicle.

   Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

   Types of polymorphism:

   Compile-time polymorphism (static polymorphism, early binding):
   - The compiler decides which version of the method to call, by examining the arguments at the call site.
   - Achieved through method overloading and operator overloading.
   - Faster, since no decision is made at run time.

   Run-time polymorphism (dynamic polymorphism, late binding):
   - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
   - Achieved through method overriding, and in C++ through virtual functions.
   - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

   Example of compile-time polymorphism (overloading):

   ```java
   class Area {
       double area(double r)           { return 3.1416 * r * r; }   // circle
       double area(double l, double b) { return l * b; }            // rectangle
       double area(int a)              { return a * a; }            // square
   }
   ```

   Example of run-time polymorphism (overriding):

   ```java
   class Shape {
       void draw() { System.out.println("Drawing a shape"); }
   }
   class Circle extends Shape {
       @Override void draw() { System.out.println("Drawing a circle"); }
   }
   class Rectangle extends Shape {
       @Override void draw() { System.out.println("Drawing a rectangle"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
           for (Shape s : shapes) {
               s.draw();      // the correct version is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Drawing a circle
   Drawing a rectangle
   Drawing a shape
   ```

   Advantages of polymorphism:
   - One interface can serve many implementations, so the calling code is simpler and shorter.
   - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
   - It reduces the need for long if-else or switch chains that test the type of an object.
   - It improves reusability, extensibility and maintainability.

   Java program demonstrating method overriding:

   ```java
   // Base class
   class Employee {
       protected String name;
       protected double basicSalary;

       Employee(String name, double basicSalary) {
           this.name = name;
           this.basicSalary = basicSalary;
       }

       // method to be overridden
       double calculateSalary() {
           return basicSalary;
       }

       void display() {
           System.out.println(name + " earns Tk " + calculateSalary());
       }
   }

   // Derived class 1
   class Manager extends Employee {
       private double bonus;

       Manager(String name, double basicSalary, double bonus) {
           super(name, basicSalary);
           this.bonus = bonus;
       }

       @Override
       double calculateSalary() {
           return basicSalary + bonus;
       }
   }

   // Derived class 2
   class Engineer extends Employee {
       private int overtimeHours;

       Engineer(String name, double basicSalary, int overtimeHours) {
           super(name, basicSalary);
           this.overtimeHours = overtimeHours;
       }

       @Override
       double calculateSalary() {
           return basicSalary + (overtimeHours * 500);
       }
   }

   public class OverrideDemo {
       public static void main(String[] args) {
           Employee[] staff = {
               new Employee("Rahim", 30000),
               new Manager("Karim", 50000, 15000),
               new Engineer("Jamal", 40000, 10)
           };

           for (Employee e : staff) {
               e.display();       // the correct calculateSalary() is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Rahim earns Tk 30000.0
   Karim earns Tk 65000.0
   Jamal earns Tk 45000.0
   ```

   Explanation of the output: the array is declared as Employee[], so the compiler only checks that Employee has a display() method. At run time the JVM examines the actual object in each slot and calls the overriding calculateSalary() belonging to that object's class. This is dynamic method dispatch, and it is what makes it possible to add a new kind of employee later without changing a single line of the loop.
2. **What is Object-Oriented Programming (OOP)? What are the main principles of OOP? What is the difference between Method Overloading and Method Overriding?** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer: Object-Oriented Programming (OOP) is a programming paradigm in which a program is organised around objects rather than around functions and logic. An object is a self-contained unit that bundles data (attributes) together with the operations that act on that data (methods), and the program is built by making such objects interact.

   The four principles (pillars) of OOP:

   - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

   - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

   - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

   - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

   Two supporting concepts often listed with them:
   - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
   - Object: an instance of a class, occupying memory and holding its own values for the data members.

   Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).

   Difference between Method Overloading and Method Overriding:

   | Point | Method Overloading | Method Overriding |
   |---|---|---|
   | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
   | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
   | Parameter list | Must differ in number, type or order | Must be exactly the same |
   | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
   | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
   | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
   | Access modifier | May be anything | Cannot be more restrictive than in the parent |
   | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
   | Private and final methods | Can be overloaded | Cannot be overridden |
   | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
   | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

   Example of overloading:

   ```java
   class Calculator {
       int add(int a, int b)            { return a + b; }
       double add(double a, double b)   { return a + b; }
       int add(int a, int b, int c)     { return a + b + c; }
   }
   ```

   The compiler chooses the version by looking at the arguments supplied at the call site.

   Example of overriding:

   ```java
   class Animal {
       void sound() { System.out.println("The animal makes a sound"); }
   }

   class Dog extends Animal {
       @Override
       void sound() { System.out.println("The dog barks"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Animal a = new Dog();   // reference of parent type, object of child type
           a.sound();              // prints "The dog barks"
       }
   }
   ```

   The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.
3. **What is runtime polymorphism and compile time polymorphism? Explain it's with example.** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)]*


   Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

   Types of polymorphism:

   Compile-time polymorphism (static polymorphism, early binding):
   - The compiler decides which version of the method to call, by examining the arguments at the call site.
   - Achieved through method overloading and operator overloading.
   - Faster, since no decision is made at run time.

   Run-time polymorphism (dynamic polymorphism, late binding):
   - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
   - Achieved through method overriding, and in C++ through virtual functions.
   - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

   Example of compile-time polymorphism (overloading):

   ```java
   class Area {
       double area(double r)           { return 3.1416 * r * r; }   // circle
       double area(double l, double b) { return l * b; }            // rectangle
       double area(int a)              { return a * a; }            // square
   }
   ```

   Example of run-time polymorphism (overriding):

   ```java
   class Shape {
       void draw() { System.out.println("Drawing a shape"); }
   }
   class Circle extends Shape {
       @Override void draw() { System.out.println("Drawing a circle"); }
   }
   class Rectangle extends Shape {
       @Override void draw() { System.out.println("Drawing a rectangle"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
           for (Shape s : shapes) {
               s.draw();      // the correct version is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Drawing a circle
   Drawing a rectangle
   Drawing a shape
   ```

   Advantages of polymorphism:
   - One interface can serve many implementations, so the calling code is simpler and shorter.
   - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
   - It reduces the need for long if-else or switch chains that test the type of an object.
   - It improves reusability, extensibility and maintainability.
4. **What is polymorphism?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

   Types of polymorphism:

   Compile-time polymorphism (static polymorphism, early binding):
   - The compiler decides which version of the method to call, by examining the arguments at the call site.
   - Achieved through method overloading and operator overloading.
   - Faster, since no decision is made at run time.

   Run-time polymorphism (dynamic polymorphism, late binding):
   - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
   - Achieved through method overriding, and in C++ through virtual functions.
   - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

   Example of compile-time polymorphism (overloading):

   ```java
   class Area {
       double area(double r)           { return 3.1416 * r * r; }   // circle
       double area(double l, double b) { return l * b; }            // rectangle
       double area(int a)              { return a * a; }            // square
   }
   ```

   Example of run-time polymorphism (overriding):

   ```java
   class Shape {
       void draw() { System.out.println("Drawing a shape"); }
   }
   class Circle extends Shape {
       @Override void draw() { System.out.println("Drawing a circle"); }
   }
   class Rectangle extends Shape {
       @Override void draw() { System.out.println("Drawing a rectangle"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
           for (Shape s : shapes) {
               s.draw();      // the correct version is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Drawing a circle
   Drawing a rectangle
   Drawing a shape
   ```

   Advantages of polymorphism:
   - One interface can serve many implementations, so the calling code is simpler and shorter.
   - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
   - It reduces the need for long if-else or switch chains that test the type of an object.
   - It improves reusability, extensibility and maintainability.
5. **Explain OOP Feature.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: The four principles (pillars) of OOP:

   - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

   - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

   - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

   - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

   Two supporting concepts often listed with them:
   - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
   - Object: an instance of a class, occupying memory and holding its own values for the data members.

   Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).

   Additional features usually listed:
   - Message passing: objects communicate by invoking one another's methods, which keeps them loosely coupled.
   - Dynamic binding: the code associated with a call is not known until run time, which is what makes overriding useful.
   - Reusability: existing classes are reused through inheritance and composition instead of being rewritten.
   - Modularity: each class is a self-contained module that can be developed and tested independently.
   - Data security: private members cannot be reached from outside the class, so invalid states are prevented.
   - Extensibility: new behaviour is added by writing new classes rather than by editing existing ones.
6. **Write a program using any object-oriented language (e.g., C++ / Java / Python) to represent a Bank Account. Your program should include:**
 * **A class BankAccount with data members for account holder's name, account number, and balance.**
 * **Member functions to deposit() money, withdraw() money (ensuring sufficient balance), and display() account details.**
**Demonstrate the concept of encapsulation by keeping data member's private and providing appropriate public methods for accessing and modifying them.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*


   Answer: The program below models a bank account in Java. All data members are private, so they cannot be reached directly from outside the class, and every access goes through public methods. This is encapsulation.

   ```java
   class BankAccount {
       // Data members are private: this is encapsulation
       private String accountHolderName;
       private String accountNumber;
       private double balance;

       // Constructor
       public BankAccount(String name, String accNo, double initialBalance) {
           this.accountHolderName = name;
           this.accountNumber = accNo;
           this.balance = (initialBalance >= 0) ? initialBalance : 0;
       }

       // Getters: controlled read access
       public String getAccountHolderName() { return accountHolderName; }
       public String getAccountNumber()     { return accountNumber; }
       public double getBalance()           { return balance; }

       // Setter with validation: controlled write access
       public void setAccountHolderName(String name) {
           if (name != null && !name.trim().isEmpty()) {
               this.accountHolderName = name;
           } else {
               System.out.println("Invalid name. Not changed.");
           }
       }

       // Deposit money
       public void deposit(double amount) {
           if (amount <= 0) {
               System.out.println("Deposit amount must be positive.");
               return;
           }
           balance += amount;
           System.out.println("Deposited Tk " + amount + ". New balance: Tk " + balance);
       }

       // Withdraw money, ensuring sufficient balance
       public void withdraw(double amount) {
           if (amount <= 0) {
               System.out.println("Withdrawal amount must be positive.");
           } else if (amount > balance) {
               System.out.println("Insufficient balance. Available: Tk " + balance);
           } else {
               balance -= amount;
               System.out.println("Withdrew Tk " + amount + ". New balance: Tk " + balance);
           }
       }

       // Display account details
       public void display() {
           System.out.println("--------------------------------");
           System.out.println("Account Holder : " + accountHolderName);
           System.out.println("Account Number : " + accountNumber);
           System.out.println("Balance        : Tk " + balance);
           System.out.println("--------------------------------");
       }
   }

   public class BankDemo {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount("Rahim Uddin", "0123456789", 5000);

           acc.display();
           acc.deposit(2500);
           acc.withdraw(1000);
           acc.withdraw(20000);      // rejected: insufficient balance
           acc.deposit(-500);        // rejected: invalid amount
           acc.display();

           // acc.balance = 1000000;   // compile error: balance is private
           System.out.println("Balance read through the getter: Tk " + acc.getBalance());
       }
   }
   ```

   Output:
   ```
   --------------------------------
   Account Holder : Rahim Uddin
   Account Number : 0123456789
   Balance        : Tk 5000.0
   --------------------------------
   Deposited Tk 2500.0. New balance: Tk 7500.0
   Withdrew Tk 1000.0. New balance: Tk 6500.0
   Insufficient balance. Available: Tk 6500.0
   Deposit amount must be positive.
   --------------------------------
   Account Holder : Rahim Uddin
   Account Number : 0123456789
   Balance        : Tk 6500.0
   --------------------------------
   Balance read through the getter: Tk 6500.0
   ```

   How encapsulation is demonstrated:
   - The three data members are declared private, so a statement such as acc.balance = 1000000; will not compile. The balance cannot be corrupted from outside.
   - Every change to the balance passes through deposit() or withdraw(), which validate the amount and check for sufficient funds. The object can therefore never enter an invalid state.
   - Read access is given through getters, but there is deliberately no setBalance() method, because the balance must only change through a transaction.
   - The internal representation can be changed later, for example from double to BigDecimal, without affecting any code that uses the class, because the public interface stays the same.
7. **b) What is polymorphism in the context of an object-oriented paradigm? Explain the method of overloading and method of overriding with suitable examples.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*


   Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

   Types of polymorphism:

   Compile-time polymorphism (static polymorphism, early binding):
   - The compiler decides which version of the method to call, by examining the arguments at the call site.
   - Achieved through method overloading and operator overloading.
   - Faster, since no decision is made at run time.

   Run-time polymorphism (dynamic polymorphism, late binding):
   - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
   - Achieved through method overriding, and in C++ through virtual functions.
   - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

   Example of compile-time polymorphism (overloading):

   ```java
   class Area {
       double area(double r)           { return 3.1416 * r * r; }   // circle
       double area(double l, double b) { return l * b; }            // rectangle
       double area(int a)              { return a * a; }            // square
   }
   ```

   Example of run-time polymorphism (overriding):

   ```java
   class Shape {
       void draw() { System.out.println("Drawing a shape"); }
   }
   class Circle extends Shape {
       @Override void draw() { System.out.println("Drawing a circle"); }
   }
   class Rectangle extends Shape {
       @Override void draw() { System.out.println("Drawing a rectangle"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
           for (Shape s : shapes) {
               s.draw();      // the correct version is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Drawing a circle
   Drawing a rectangle
   Drawing a shape
   ```

   Advantages of polymorphism:
   - One interface can serve many implementations, so the calling code is simpler and shorter.
   - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
   - It reduces the need for long if-else or switch chains that test the type of an object.
   - It improves reusability, extensibility and maintainability.

   Method overloading and method overriding compared:

   | Point | Method Overloading | Method Overriding |
   |---|---|---|
   | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
   | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
   | Parameter list | Must differ in number, type or order | Must be exactly the same |
   | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
   | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
   | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
   | Access modifier | May be anything | Cannot be more restrictive than in the parent |
   | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
   | Private and final methods | Can be overloaded | Cannot be overridden |
   | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
   | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

   Example of overloading:

   ```java
   class Calculator {
       int add(int a, int b)            { return a + b; }
       double add(double a, double b)   { return a + b; }
       int add(int a, int b, int c)     { return a + b + c; }
   }
   ```

   The compiler chooses the version by looking at the arguments supplied at the call site.

   Example of overriding:

   ```java
   class Animal {
       void sound() { System.out.println("The animal makes a sound"); }
   }

   class Dog extends Animal {
       @Override
       void sound() { System.out.println("The dog barks"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Animal a = new Dog();   // reference of parent type, object of child type
           a.sound();              // prints "The dog barks"
       }
   }
   ```

   The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.
8. **Explain the concept of polymorphism in Object-oriented Programming with example?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*


   Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

   Types of polymorphism:

   Compile-time polymorphism (static polymorphism, early binding):
   - The compiler decides which version of the method to call, by examining the arguments at the call site.
   - Achieved through method overloading and operator overloading.
   - Faster, since no decision is made at run time.

   Run-time polymorphism (dynamic polymorphism, late binding):
   - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
   - Achieved through method overriding, and in C++ through virtual functions.
   - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

   Example of compile-time polymorphism (overloading):

   ```java
   class Area {
       double area(double r)           { return 3.1416 * r * r; }   // circle
       double area(double l, double b) { return l * b; }            // rectangle
       double area(int a)              { return a * a; }            // square
   }
   ```

   Example of run-time polymorphism (overriding):

   ```java
   class Shape {
       void draw() { System.out.println("Drawing a shape"); }
   }
   class Circle extends Shape {
       @Override void draw() { System.out.println("Drawing a circle"); }
   }
   class Rectangle extends Shape {
       @Override void draw() { System.out.println("Drawing a rectangle"); }
   }

   public class Demo {
       public static void main(String[] args) {
           Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
           for (Shape s : shapes) {
               s.draw();      // the correct version is chosen at run time
           }
       }
   }
   ```

   Output:
   ```
   Drawing a circle
   Drawing a rectangle
   Drawing a shape
   ```

   Advantages of polymorphism:
   - One interface can serve many implementations, so the calling code is simpler and shorter.
   - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
   - It reduces the need for long if-else or switch chains that test the type of an object.
   - It improves reusability, extensibility and maintainability.
9. **Write down the difference between Structure and Class.** *[BCIC Assistant Programmer 14.02.2025 compact it 1324 (ET: BUET)]*


   Answer:

   | Point | Structure | Class |
   |---|---|---|
   | Keyword | struct | class |
   | Default access specifier | public | private |
   | Default inheritance access | public | private |
   | Purpose | Grouping related data items | Modelling a complete entity with data and behaviour |
   | Member functions | Allowed in C++, not allowed in C | Allowed |
   | Data hiding | Not enforced by default | Enforced by default |
   | Inheritance | Supported in C++, not in C | Supported |
   | Constructor and destructor | Allowed in C++, not in C | Allowed |
   | Access specifiers | Allowed in C++, not in C | Allowed |
   | Memory allocation | Usually on the stack | On the heap in Java and C#, on either in C++ |
   | In Java and C# | A struct is a value type (C# only); Java has no struct | A class is a reference type |
   | Typical use | Plain data containers, for example a Point or a Date | Full objects, for example a BankAccount or an Employee |

   Important note for C++: technically the only difference between struct and class in C++ is the default access level, which is public for a struct and private for a class. Everything else, including member functions, constructors, inheritance and polymorphism, is available to both. The difference is therefore one of convention: struct is used for simple data aggregates and class for objects with behaviour and invariants to protect.

   Example:

   ```cpp
   struct Point {          // members are public by default
       int x;
       int y;
   };

   class Rectangle {       // members are private by default
       int length;
       int breadth;
   public:
       Rectangle(int l, int b) : length(l), breadth(b) {}
       int area() { return length * breadth; }
   };

   int main() {
       Point p;
       p.x = 10;           // allowed: public by default
       p.y = 20;

       Rectangle r(5, 4);
       // r.length = 100;  // error: length is private
       cout << r.area();   // 20
       return 0;
   }
   ```

   In C the difference is far greater: a C structure can hold only data, with no functions, no access control, no constructors and no inheritance.
10. **What is Polymorphism? Discuss about different types of Polymorphism with example?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 296 (ET: BIBM)]*


    Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

    Types of polymorphism:

    Compile-time polymorphism (static polymorphism, early binding):
    - The compiler decides which version of the method to call, by examining the arguments at the call site.
    - Achieved through method overloading and operator overloading.
    - Faster, since no decision is made at run time.

    Run-time polymorphism (dynamic polymorphism, late binding):
    - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
    - Achieved through method overriding, and in C++ through virtual functions.
    - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

    Example of compile-time polymorphism (overloading):

    ```java
    class Area {
        double area(double r)           { return 3.1416 * r * r; }   // circle
        double area(double l, double b) { return l * b; }            // rectangle
        double area(int a)              { return a * a; }            // square
    }
    ```

    Example of run-time polymorphism (overriding):

    ```java
    class Shape {
        void draw() { System.out.println("Drawing a shape"); }
    }
    class Circle extends Shape {
        @Override void draw() { System.out.println("Drawing a circle"); }
    }
    class Rectangle extends Shape {
        @Override void draw() { System.out.println("Drawing a rectangle"); }
    }

    public class Demo {
        public static void main(String[] args) {
            Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
            for (Shape s : shapes) {
                s.draw();      // the correct version is chosen at run time
            }
        }
    }
    ```

    Output:
    ```
    Drawing a circle
    Drawing a rectangle
    Drawing a shape
    ```

    Advantages of polymorphism:
    - One interface can serve many implementations, so the calling code is simpler and shorter.
    - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
    - It reduces the need for long if-else or switch chains that test the type of an object.
    - It improves reusability, extensibility and maintainability.
11. **Explain how encapsulation and inheritance are advantageous in object oriented programming.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 420 (ET: BIBM)]*


    Answer:

    Advantages of encapsulation:

    - Data hiding and security: the internal state is declared private, so it cannot be read or altered directly from outside the class. A bank balance, for example, cannot be set to an arbitrary value by another part of the program.
    - Control over data: every change passes through a method that can validate it. A setAge() method can reject a negative age, and a withdraw() method can reject an amount greater than the balance, so the object never enters an invalid state.
    - Flexibility to change the implementation: the internal representation can be replaced without affecting any code that uses the class, as long as the public methods keep the same signatures. This is what makes long-term maintenance possible.
    - Read-only or write-only members: providing a getter without a setter gives a read-only property; providing a setter without a getter gives a write-only one, such as a password.
    - Easier debugging: if a value becomes wrong, the search is limited to the few methods that can modify it, rather than to the entire program.
    - Modularity and loose coupling: each class becomes a self-contained unit that can be developed, tested and reused independently, because the rest of the program depends only on its public interface.
    - Reusability: a well-encapsulated class can be dropped into another program without carrying hidden dependencies.

    Advantages of inheritance:

    - Reusability of code: common attributes and methods are written once in the base class and are automatically available to every derived class. This is the single largest saving in a large system.
    - Reduced duplication: because the shared code exists in one place, a bug is fixed once rather than in many copies, and the copies cannot drift out of step.
    - Extensibility: a new derived class adds new behaviour without modifying, recompiling or retesting the base class. This supports the open-closed principle: open for extension, closed for modification.
    - It enables run-time polymorphism: a base-class reference can hold a derived-class object, so a single loop can process many different types. Without inheritance there would be no dynamic method dispatch.
    - Natural modelling of the real world: an Account hierarchy with SavingsAccount and CurrentAccount mirrors how the business itself is organised, which makes the code far easier for a new developer to understand.
    - Method overriding: a subclass can specialise inherited behaviour while keeping the same interface.
    - Easier maintenance: a change to shared behaviour is made in the base class and takes effect everywhere at once.

    How they work together: encapsulation protects each class from the outside, and inheritance lets classes share what they have in common. Encapsulation makes inheritance safe, because a derived class works through the protected and public interface of its parent rather than reaching into its private data. Together they produce code that is secure, reusable and easy to extend.

    A caution worth stating: inheritance should express a genuine "is-a" relationship. Using it merely to reuse a few lines of code produces fragile hierarchies, and in such cases composition, that is holding an object of another class as a member, is the better choice.
12. **(খ) Function Overloading উদাহরণসহ ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


    Answer: Function Overloading হলো এমন একটি বৈশিষ্ট্য, যেখানে একই নামে একাধিক ফাংশন সংজ্ঞায়িত করা যায়, যদি তাদের প্যারামিটারের সংখ্যা, ধরন বা ক্রম ভিন্ন হয়। কম্পাইলার কল করার সময় দেওয়া আর্গুমেন্ট দেখে সিদ্ধান্ত নেয় কোন সংস্করণটি চালানো হবে।

    এটি কম্পাইল-টাইম পলিমরফিজম বা স্ট্যাটিক বাইন্ডিংয়ের উদাহরণ, কারণ সিদ্ধান্তটি প্রোগ্রাম চালানোর আগেই কম্পাইলেশনের সময় নেওয়া হয়।

    শর্তসমূহ:
    - প্যারামিটারের সংখ্যা ভিন্ন হতে হবে, অথবা
    - প্যারামিটারের ডেটা টাইপ ভিন্ন হতে হবে, অথবা
    - প্যারামিটারের ক্রম ভিন্ন হতে হবে।
    - কেবল রিটার্ন টাইপ ভিন্ন হলে ওভারলোডিং হয় না; কম্পাইলার তা আলাদা করতে পারে না এবং ত্রুটি দেয়।

    উদাহরণ (C++):

    ```cpp
    #include <iostream>
    using namespace std;

    class Calculator {
    public:
        // প্যারামিটারের সংখ্যা ভিন্ন
        int add(int a, int b)            { return a + b; }
        int add(int a, int b, int c)     { return a + b + c; }

        // ডেটা টাইপ ভিন্ন
        double add(double a, double b)   { return a + b; }

        // ক্রম ভিন্ন
        void show(int a, double b)  { cout << "int first: "    << a << ", " << b << endl; }
        void show(double a, int b)  { cout << "double first: " << a << ", " << b << endl; }
    };

    int main() {
        Calculator c;
        cout << c.add(5, 10)        << endl;   // 15   -> int সংস্করণ
        cout << c.add(5, 10, 15)    << endl;   // 30   -> তিন প্যারামিটারের সংস্করণ
        cout << c.add(2.5, 3.5)     << endl;   // 6    -> double সংস্করণ
        c.show(10, 2.5);
        c.show(2.5, 10);
        return 0;
    }
    ```

    আউটপুট:
    ```
    15
    30
    6
    int first: 10, 2.5
    double first: 2.5, 10
    ```

    সুবিধা:
    - একই যৌক্তিক কাজের জন্য একই নাম ব্যবহার করা যায়, তাই নাম মনে রাখা সহজ। যেমন add() নামটিই যথেষ্ট, addInt(), addDouble(), addThree() লিখতে হয় না।
    - কোড পড়তে ও বুঝতে সুবিধা হয় এবং প্রোগ্রামের সামঞ্জস্য বজায় থাকে।
    - কনস্ট্রাক্টর ওভারলোডিংয়ের মাধ্যমে একই ক্লাসের অবজেক্ট বিভিন্নভাবে তৈরি করা যায়।

    উল্লেখযোগ্য: জাভাতেও ফাংশন বা মেথড ওভারলোডিং সমর্থিত, তবে অপারেটর ওভারলোডিং সমর্থিত নয় (কেবল + অপারেটরটি স্ট্রিংয়ের জন্য পূর্বনির্ধারিতভাবে ওভারলোড করা আছে)। C++ ও Python উভয় ধরনের ওভারলোডিং সমর্থন করে।
13. **Write down the advantages of OOP over traditional structured programming language** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 527 (ET: MIST)]*


    Answer: | Point | Procedural / Structured Programming | Object-Oriented Programming |
    |---|---|---|
    | Basic unit | The function or procedure | The object |
    | Approach | Top-down: the problem is broken into functions | Bottom-up: objects are identified and then made to interact |
    | Focus | On the procedure, that is on what is done | On the data and the objects that own it |
    | Data and function | Kept separate; data is passed to functions | Bound together inside a class |
    | Data security | Weak; global data is visible to every function | Strong; data is private and reached only through methods |
    | Data hiding | Not supported | Supported through encapsulation and access specifiers |
    | Code reuse | Only by calling the same function again | Through inheritance and composition, and by extending existing classes |
    | Handling change | A change to a data structure may require changes in many functions | A change is confined inside the class |
    | Suitability | Small and medium programs | Large and complex systems |
    | Overloading | Not supported | Supported |
    | Inheritance and polymorphism | Not available | Available |
    | Real-world modelling | Poor | Natural, since objects correspond to real entities |
    | Examples | C, Pascal, FORTRAN, COBOL, BASIC | C++, Java, Python, C#, Ruby, Smalltalk |

    Why OOP is preferred for large systems: it localises change. If the internal representation of an account balance is altered, only the Account class must be modified, and every other part of the program that uses the public methods continues to work. In a procedural program the same change could require edits in dozens of functions.

    Specific advantages of OOP over traditional structured programming:

    - Better data security through encapsulation, since data is private and cannot be corrupted by unrelated code.
    - Code reuse through inheritance, so common behaviour is written once.
    - Easier maintenance, because a change is confined to one class instead of spreading through many functions.
    - Natural modelling of real-world entities, which makes large systems easier to design and to understand.
    - Extensibility through polymorphism: new types can be added without modifying existing code.
    - Support for large team development, since each class can be assigned, written and tested independently.
    - Reduced complexity, because a large problem is decomposed into self-contained objects.
    - Better suited to graphical user interfaces, simulations and event-driven systems, where entities have both state and behaviour.

    Limitations that should also be mentioned: OOP programs are usually larger, they can run slightly slower because of dynamic dispatch, the design phase takes longer, and for a small utility program the extra structure is unnecessary overhead.
14. **Write down the Principle of OOP. What is Polymorphism? Write the name of 3 OOP language.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).

    What polymorphism is:

    Polymorphism means "many forms". It is the ability of a single interface, method name or operator to behave differently depending on the object it acts on or the arguments given to it. It exists in two forms: compile-time polymorphism, achieved through method overloading and operator overloading, and run-time polymorphism, achieved through method overriding and virtual functions.

    Names of three OOP languages:
    - Java
    - C++
    - Python

    Others: C#, Ruby, Smalltalk, Objective-C, Swift, Kotlin and PHP.
15. **(b) What is the diamond problem of multiple inheritance in C++?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 487 (ET: N/A)]*


    Answer: The diamond problem is the ambiguity that arises in multiple inheritance when a class inherits from two classes that themselves inherit from a common base class. The inheritance graph is shaped like a diamond, which gives the problem its name.

    The structure:

    ```
             A
            / \
           B   C
            \ /
             D
    ```

    Class A is the common base. B and C both inherit from A. D inherits from both B and C.

    The problem: D receives two separate copies of every member of A, one through B and one through C. When D refers to a member of A, the compiler cannot tell which copy is meant, so the reference is ambiguous. Worse, the constructor of A is called twice, and memory is wasted on the duplicate members.

    Demonstration in C++:

    ```cpp
    #include <iostream>
    using namespace std;

    class A {
    public:
        int value;
        void show() { cout << "Class A, value = " << value << endl; }
    };

    class B : public A { };
    class C : public A { };

    class D : public B, public C { };

    int main() {
        D d;
        // d.value = 10;   // error: request for member 'value' is ambiguous
        // d.show();       // error: request for member 'show' is ambiguous

        d.B::value = 10;   // works: explicitly choose the copy inherited through B
        d.C::value = 20;   // a completely separate copy
        d.B::show();       // Class A, value = 10
        d.C::show();       // Class A, value = 20
        return 0;
    }
    ```

    Two copies of value exist, which is not what a programmer normally intends.

    Solution in C++: virtual inheritance.

    ```cpp
    class A {
    public:
        int value;
        void show() { cout << "value = " << value << endl; }
    };

    class B : virtual public A { };    // virtual base
    class C : virtual public A { };    // virtual base

    class D : public B, public C { };

    int main() {
        D d;
        d.value = 10;      // no ambiguity now: only one copy of A exists
        d.show();          // value = 10
        return 0;
    }
    ```

    With the keyword virtual, only one shared instance of A is created no matter how many paths lead to it, so the ambiguity disappears and no memory is wasted. The constructor of A is then called once, by the most derived class D.

    How other languages avoid the problem:
    - Java does not allow a class to extend more than one class. A class may implement several interfaces, but before Java 8 interfaces held no implementation, so no ambiguity could arise. Since Java 8 interfaces may have default methods, and if two interfaces provide the same default method the class is required to override it explicitly and may choose one with InterfaceName.super.method().
    - C# takes the same approach as Java.
    - Python allows full multiple inheritance and resolves the order deterministically using the C3 linearisation algorithm, exposed as the Method Resolution Order (MRO), which can be inspected with ClassName.__mro__.

    Related terms: the diamond problem is also called the "deadly diamond of death".
16. **(a) Define function overloading and function overriding with examples.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*


    Answer: Function overloading and function overriding are the two mechanisms that give polymorphism in object-oriented programming.

        Function overloading:
        - Two or more functions in the same scope share the same name but differ in the number, type or order of their parameters.
        - The compiler decides at compile time which one to call, by matching the arguments at the call site. This is compile-time or static polymorphism.
        - Inheritance is not required.
        - The return type alone cannot distinguish two overloads.

        Example of function overloading:

        ```cpp
        #include <iostream>
        using namespace std;

        class Area {
        public:
            double calculate(double radius) {                 // circle
                return 3.1416 * radius * radius;
            }
            double calculate(double length, double breadth) { // rectangle
                return length * breadth;
            }
            double calculate(double a, double b, double c) {  // triangle by Heron
                double s = (a + b + c) / 2;
                return sqrt(s * (s - a) * (s - b) * (s - c));
            }
        };

        int main() {
            Area obj;
            cout << obj.calculate(5.0)            << endl;   // 78.54  -> circle
            cout << obj.calculate(4.0, 6.0)       << endl;   // 24     -> rectangle
            cout << obj.calculate(3.0, 4.0, 5.0)  << endl;   // 6      -> triangle
            return 0;
        }
        ```

        Function overriding:
        - A derived class provides its own definition of a function that already exists in its base class, with exactly the same name, parameters and return type.
        - The version that runs is decided at run time from the actual type of the object, not the type of the reference. This is run-time or dynamic polymorphism.
        - Inheritance is required, and in C++ the base-class function must be declared virtual for dynamic dispatch to occur.

        Example of function overriding:

        ```cpp
        #include <iostream>
        using namespace std;

        class Shape {
        public:
            virtual void draw() {                    // virtual is essential in C++
                cout << "Drawing a generic shape" << endl;
            }
            virtual ~Shape() {}
        };

        class Circle : public Shape {
        public:
            void draw() override {
                cout << "Drawing a circle" << endl;
            }
        };

        class Square : public Shape {
        public:
            void draw() override {
                cout << "Drawing a square" << endl;
            }
        };

        int main() {
            Shape* s;

            Circle c;
            Square q;

            s = &c;  s->draw();      // Drawing a circle
            s = &q;  s->draw();      // Drawing a square
            return 0;
        }
        ```

        Comparison:

    | Point | Method Overloading | Method Overriding |
        |---|---|---|
        | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
        | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
        | Parameter list | Must differ in number, type or order | Must be exactly the same |
        | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
        | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
        | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
        | Access modifier | May be anything | Cannot be more restrictive than in the parent |
        | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
        | Private and final methods | Can be overloaded | Cannot be overridden |
        | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
        | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

        Example of overloading:

        ```java
        class Calculator {
            int add(int a, int b)            { return a + b; }
            double add(double a, double b)   { return a + b; }
            int add(int a, int b, int c)     { return a + b + c; }
        }
        ```

        The compiler chooses the version by looking at the arguments supplied at the call site.

        Example of overriding:

        ```java
        class Animal {
            void sound() { System.out.println("The animal makes a sound"); }
        }

        class Dog extends Animal {
            @Override
            void sound() { System.out.println("The dog barks"); }
        }

        public class Demo {
            public static void main(String[] args) {
                Animal a = new Dog();   // reference of parent type, object of child type
                a.sound();              // prints "The dog barks"
            }
        }
        ```

        The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.
17. **What is virtual function with example?** *[BITAC Assistant Programmer 27.10.2023 compact it 560 (ET: BUTEX)], [Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 506 (ET: N/A)]*


    Answer: A virtual function is a member function of a base class that is declared with the keyword virtual and is intended to be redefined (overridden) in a derived class. When it is called through a base-class pointer or reference, the version belonging to the actual object is executed, not the version belonging to the pointer type. This is run-time polymorphism, and the mechanism behind it is dynamic binding.

    Why it is needed: without the keyword virtual, C++ decides at compile time which function to call, using only the declared type of the pointer. The derived version would then never run through a base pointer, and polymorphism would be impossible.

    Rules:
    - It must be a member function, declared virtual in the base class.
    - It cannot be static.
    - It is accessed through a pointer or reference to the base class.
    - The signature in the derived class must match exactly.
    - A class with a virtual function should also have a virtual destructor, otherwise deleting a derived object through a base pointer causes undefined behaviour and leaks resources.

    Example:

    ```cpp
    #include <iostream>
    using namespace std;

    class Shape {
    public:
        virtual void draw() {                       // virtual function
            cout << "Drawing a generic shape" << endl;
        }
        virtual double area() { return 0; }
        virtual ~Shape() {}                         // virtual destructor
    };

    class Circle : public Shape {
        double r;
    public:
        Circle(double radius) : r(radius) {}
        void draw() override { cout << "Drawing a circle" << endl; }
        double area() override { return 3.1416 * r * r; }
    };

    class Rectangle : public Shape {
        double l, b;
    public:
        Rectangle(double len, double br) : l(len), b(br) {}
        void draw() override { cout << "Drawing a rectangle" << endl; }
        double area() override { return l * b; }
    };

    int main() {
        Shape* shapes[3];
        shapes[0] = new Circle(5);
        shapes[1] = new Rectangle(4, 6);
        shapes[2] = new Shape();

        for (int i = 0; i < 3; i++) {
            shapes[i]->draw();
            cout << "Area = " << shapes[i]->area() << endl;
        }

        for (int i = 0; i < 3; i++) delete shapes[i];
        return 0;
    }
    ```

    Output:
    ```
    Drawing a circle
    Area = 78.54
    Drawing a rectangle
    Area = 24
    Drawing a generic shape
    Area = 0
    ```

    Without the keyword virtual the output would be "Drawing a generic shape" three times, because the choice would be made from the pointer type alone.

    How it works internally: a class containing virtual functions gets a hidden table of function pointers called the virtual table (vtable), and every object of that class gets a hidden pointer to it (vptr). A call through a base pointer is compiled into a lookup in the vtable, so the address of the correct function is found at run time. This costs one extra indirection, which is the small price of dynamic dispatch.

    Pure virtual function and abstract class:

    ```cpp
    class Shape {
    public:
        virtual void draw() = 0;      // pure virtual: no body
    };
    ```

    A pure virtual function has no implementation in the base class and makes the class abstract, so no object of it can be created. Every concrete derived class is then obliged to provide an implementation. This is how an interface is expressed in C++.

    Note on Java: in Java every non-static, non-final, non-private method is virtual by default, so no keyword is needed. The keyword final is used to prevent overriding, which is the opposite convention to C++.
18. **How many classes can be used in Hybrid Inheritance?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


    Answer: Hybrid inheritance is a combination of two or more of the basic types of inheritance, such as hierarchical inheritance combined with multiple inheritance. There is no fixed number of classes prescribed for it; any number may be involved, provided the arrangement mixes at least two inheritance types.

    The minimum, however, is four classes, because the simplest hybrid arrangement is the diamond, which requires one base class, two intermediate classes and one final derived class.

    The standard diamond form:

    ```
             A          (base class)
            / \
           B   C        (hierarchical inheritance from A)
            \ /
             D          (multiple inheritance from B and C)
    ```

    Here A to B and A to C is hierarchical inheritance, and B and C to D is multiple inheritance. The combination of the two is hybrid inheritance, and four classes are needed.

    Other hybrid arrangements:
    - Single plus multiple: A to B (single), then B and C to D (multiple), which also needs four classes.
    - Multilevel plus hierarchical: A to B to C, and also B to D, which needs four classes.
    - Larger systems may involve many more classes in the same pattern.

    Answer in short: at least four classes, and in general any number, depending on how the basic types are combined.

    Language support:
    - C++ supports hybrid inheritance fully, but the diamond form creates the ambiguity known as the diamond problem, which is solved by declaring the intermediate classes with virtual inheritance.
    - Java does not support hybrid inheritance through classes, because it does not allow multiple class inheritance. It can be achieved using interfaces, since a class may implement any number of interfaces.
    - Python supports it and resolves the order using the C3 linearisation algorithm, exposed as the Method Resolution Order.
19. **What is Abstraction and Polymorphism expalin with example?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*


    Answer:

        Abstraction:

        Abstraction is the principle of showing only the essential features of an object to the outside world while hiding the internal implementation details. It answers the question "what does this object do", not "how does it do it".

        - A person driving a car uses the steering wheel, the accelerator and the brake without knowing how the engine, the gearbox or the braking system work internally. The controls are the abstraction; the machinery is the hidden implementation.
        - In code it is implemented with abstract classes and interfaces, which declare method signatures without bodies, leaving the implementation to the concrete classes.
        - Benefit: it reduces complexity for the user of a class, and it allows the implementation to be changed later without breaking any code that depends on the interface.

        Example of abstraction in Java:

        ```java
        abstract class Shape {
            abstract double area();               // what: every shape has an area
            abstract double perimeter();          // how: left to each subclass

            void describe() {                     // a concrete method is also allowed
                System.out.println("Area = " + area() + ", Perimeter = " + perimeter());
            }
        }

        class Circle extends Shape {
            private double r;
            Circle(double r) { this.r = r; }
            double area()      { return Math.PI * r * r; }
            double perimeter() { return 2 * Math.PI * r; }
        }

        class Rectangle extends Shape {
            private double l, b;
            Rectangle(double l, double b) { this.l = l; this.b = b; }
            double area()      { return l * b; }
            double perimeter() { return 2 * (l + b); }
        }

        public class AbstractionDemo {
            public static void main(String[] args) {
                // Shape s = new Shape();       // error: an abstract class cannot be instantiated
                Shape s1 = new Circle(5);
                Shape s2 = new Rectangle(4, 6);
                s1.describe();
                s2.describe();
            }
        }
        ```

        The user of Shape knows that every shape has area() and perimeter(), but need not know the formula used by any particular shape.

        Difference from encapsulation, which is often confused with it:
        - Abstraction hides complexity and is a design-level concern; it is achieved with abstract classes and interfaces.
        - Encapsulation hides data and is an implementation-level concern; it is achieved with access specifiers such as private.

        Polymorphism:

    Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

        Types of polymorphism:

        Compile-time polymorphism (static polymorphism, early binding):
        - The compiler decides which version of the method to call, by examining the arguments at the call site.
        - Achieved through method overloading and operator overloading.
        - Faster, since no decision is made at run time.

        Run-time polymorphism (dynamic polymorphism, late binding):
        - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
        - Achieved through method overriding, and in C++ through virtual functions.
        - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

        Example of compile-time polymorphism (overloading):

        ```java
        class Area {
            double area(double r)           { return 3.1416 * r * r; }   // circle
            double area(double l, double b) { return l * b; }            // rectangle
            double area(int a)              { return a * a; }            // square
        }
        ```

        Example of run-time polymorphism (overriding):

        ```java
        class Shape {
            void draw() { System.out.println("Drawing a shape"); }
        }
        class Circle extends Shape {
            @Override void draw() { System.out.println("Drawing a circle"); }
        }
        class Rectangle extends Shape {
            @Override void draw() { System.out.println("Drawing a rectangle"); }
        }

        public class Demo {
            public static void main(String[] args) {
                Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
                for (Shape s : shapes) {
                    s.draw();      // the correct version is chosen at run time
                }
            }
        }
        ```

        Output:
        ```
        Drawing a circle
        Drawing a rectangle
        Drawing a shape
        ```

        Advantages of polymorphism:
        - One interface can serve many implementations, so the calling code is simpler and shorter.
        - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
        - It reduces the need for long if-else or switch chains that test the type of an object.
        - It improves reusability, extensibility and maintainability.
20. **(খ) কী কী ধারণার উপর ভিত্তি করে OOP প্রতিষ্ঠিত? ধারণাগুলো ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*


    Answer: অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং চারটি মৌলিক ধারণার উপর প্রতিষ্ঠিত। এগুলোকে OOP এর চারটি স্তম্ভ বলা হয়।

    - এনক্যাপসুলেশন (Encapsulation): তথ্য এবং সেই তথ্যের ওপর কাজ করা ফাংশনগুলোকে একটি একক এককে, অর্থাৎ ক্লাসে, আবদ্ধ করা এবং বাইরের জগত থেকে অভ্যন্তরীণ অবস্থা আড়াল করা। ডেটা মেম্বারগুলোকে private ঘোষণা করা হয় এবং কেবল public গেটার ও সেটার মেথডের মাধ্যমে সেগুলোতে পৌঁছানো যায়। ফলে ভুল বা অবৈধ মান বসানো ঠেকানো যায় এবং ভবিষ্যতে অভ্যন্তরীণ বাস্তবায়ন বদলালেও ব্যবহারকারীর কোড ভাঙে না।

    - অ্যাবস্ট্রাকশন (Abstraction): কেবল প্রয়োজনীয় বৈশিষ্ট্য প্রকাশ করা এবং অভ্যন্তরীণ জটিলতা আড়াল করা। গাড়ি চালানোর সময় চালক স্টিয়ারিং ও প্যাডেল ব্যবহার করেন, ইঞ্জিন কীভাবে কাজ করে তা জানার দরকার হয় না। প্রোগ্রামিংয়ে এটি abstract class ও interface এর মাধ্যমে বাস্তবায়িত হয়, যা "কী করা হবে" ঘোষণা করে কিন্তু "কীভাবে করা হবে" তা বলে না।

    - ইনহেরিটেন্স (Inheritance): একটি নতুন ক্লাস পুরোনো একটি ক্লাসের বৈশিষ্ট্য ও আচরণ উত্তরাধিকার সূত্রে পেয়ে যায়। এটি "is-a" সম্পর্ক প্রকাশ করে, যেমন কুকুর একটি প্রাণী। এর সবচেয়ে বড় সুবিধা কোড পুনর্ব্যবহার। প্রকারভেদ: single, multilevel, hierarchical, multiple ও hybrid।

    - পলিমরফিজম (Polymorphism): একই ইন্টারফেস বা নাম বিভিন্ন পরিস্থিতিতে ভিন্ন আচরণ করা। কম্পাইল-টাইম পলিমরফিজম হয় method overloading ও operator overloading এর মাধ্যমে, আর রান-টাইম পলিমরফিজম হয় method overriding ও virtual function এর মাধ্যমে।

    সহায়ক ধারণাসমূহ:

    - ক্লাস (Class): একটি নকশা বা টেমপ্লেট, যা একই ধরনের বস্তুর ডেটা মেম্বার ও মেম্বার ফাংশন সংজ্ঞায়িত করে। ক্লাস ঘোষণা করলে কোনো মেমোরি বরাদ্দ হয় না।

    - অবজেক্ট (Object): ক্লাসের একটি বাস্তব উদাহরণ বা ইনস্ট্যান্স, যা মেমোরিতে জায়গা দখল করে এবং ডেটা মেম্বারগুলোর নিজস্ব মান ধারণ করে।

    - মেসেজ পাসিং (Message Passing): অবজেক্টগুলো একে অপরের মেথড কল করে যোগাযোগ করে, ফলে তারা পরস্পর থেকে শিথিলভাবে যুক্ত থাকে।

    - ডাইনামিক বাইন্ডিং (Dynamic Binding): কোন মেথডটি চালানো হবে তা প্রোগ্রাম চালানোর সময় নির্ধারিত হয়, কম্পাইলেশনের সময় নয়। এটিই মেথড ওভাররাইডিংকে কার্যকর করে তোলে।

    এই ধারণাগুলোর সম্মিলিত ফল: নিরাপদ, পুনর্ব্যবহারযোগ্য, সহজে সম্প্রসারণযোগ্য ও রক্ষণাবেক্ষণযোগ্য কোড, যা বড় সফটওয়্যার প্রকল্পে অপরিহার্য।
21. **(গ) Inheritance কী? উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*


    Answer: ইনহেরিটেন্স (Inheritance) বা উত্তরাধিকার হলো এমন একটি প্রক্রিয়া, যার মাধ্যমে একটি ক্লাস অন্য একটি ক্লাসের ডেটা মেম্বার ও মেম্বার ফাংশন অর্জন করে। যে ক্লাস থেকে অর্জন করা হয় তাকে বলে base class, parent class বা superclass, আর যে ক্লাস অর্জন করে তাকে বলে derived class, child class বা subclass।

    এটি একটি "is-a" সম্পর্ক প্রকাশ করে। যেমন একটি সঞ্চয়ী হিসাব একটি ব্যাংক হিসাব, একটি কুকুর একটি প্রাণী।

    প্রধান সুবিধা:
    - কোড পুনর্ব্যবহার: সাধারণ বৈশিষ্ট্যগুলো একবার বেস ক্লাসে লিখলেই সব ডেরাইভড ক্লাসে পাওয়া যায়।
    - পুনরাবৃত্তি হ্রাস: একই কোড বারবার লিখতে হয় না, তাই একটি বাগ একবারই সারালে সব জায়গায় ঠিক হয়ে যায়।
    - সম্প্রসারণযোগ্যতা: বেস ক্লাস না বদলেই নতুন ডেরাইভড ক্লাস যোগ করা যায়।
    - রান-টাইম পলিমরফিজম সম্ভব হয়, কারণ বেস ক্লাসের রেফারেন্স ডেরাইভড ক্লাসের অবজেক্ট ধারণ করতে পারে।
    - বাস্তব জগতের শ্রেণিবিন্যাসের সঙ্গে কোডের মিল থাকে, ফলে বোঝা ও রক্ষণাবেক্ষণ সহজ হয়।

    প্রকারভেদ:
    - Single Inheritance: একটি ডেরাইভড ক্লাস একটি বেস ক্লাস থেকে উত্তরাধিকার পায়। (A → B)
    - Multilevel Inheritance: একটি ডেরাইভড ক্লাস নিজেই আরেকটির বেস হয়। (A → B → C)
    - Hierarchical Inheritance: একাধিক ডেরাইভড ক্লাস একই বেস ক্লাস থেকে উত্তরাধিকার পায়। (A → B, A → C)
    - Multiple Inheritance: একটি ডেরাইভড ক্লাস একাধিক বেস ক্লাস থেকে উত্তরাধিকার পায়। (A, B → C) — C++ ও Python সমর্থন করে, Java করে না।
    - Hybrid Inheritance: উপরের দুই বা ততোধিকের সমন্বয়।

    উদাহরণ (Java):

    ```java
    // বেস ক্লাস
    class Account {
        protected String holderName;
        protected double balance;

        Account(String name, double balance) {
            this.holderName = name;
            this.balance = balance;
        }

        void deposit(double amount) {
            balance += amount;
            System.out.println("Deposited: " + amount + ", Balance: " + balance);
        }

        void display() {
            System.out.println(holderName + " -> Balance: " + balance);
        }
    }

    // ডেরাইভড ক্লাস
    class SavingsAccount extends Account {
        private double interestRate;

        SavingsAccount(String name, double balance, double rate) {
            super(name, balance);          // বেস ক্লাসের কনস্ট্রাক্টর কল
            this.interestRate = rate;
        }

        void addInterest() {               // নিজস্ব নতুন মেথড
            double interest = balance * interestRate / 100;
            balance += interest;
            System.out.println("Interest added: " + interest);
        }
    }

    public class InheritanceDemo {
        public static void main(String[] args) {
            SavingsAccount s = new SavingsAccount("Rahim", 10000, 5);
            s.deposit(5000);      // বেস ক্লাস থেকে উত্তরাধিকারসূত্রে পাওয়া
            s.addInterest();      // নিজস্ব মেথড
            s.display();          // বেস ক্লাস থেকে পাওয়া
        }
    }
    ```

    আউটপুট:
    ```
    Deposited: 5000.0, Balance: 15000.0
    Interest added: 750.0
    Rahim -> Balance: 15750.0
    ```

    অ্যাক্সেসের নিয়ম: বেস ক্লাসের public মেম্বার ডেরাইভড ক্লাসে public থাকে, protected মেম্বার ডেরাইভড ক্লাসের ভেতরে ব্যবহার করা যায়, আর private মেম্বার উত্তরাধিকারে যায় কিন্তু সরাসরি ব্যবহার করা যায় না; সেগুলোতে পৌঁছাতে হলে বেস ক্লাসের public বা protected মেথড ব্যবহার করতে হয়।

    কীওয়ার্ড: Java তে extends, আর C++ এ কোলন চিহ্নসহ অ্যাক্সেস স্পেসিফায়ার, যেমন class SavingsAccount : public Account।
22. **(ক) অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং কী? এটা কেন দরকার? অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর মৌলিক ধারণাগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


    Answer: অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং (OOP) হলো এমন একটি প্রোগ্রামিং পদ্ধতি, যেখানে প্রোগ্রামকে ফাংশন ও যুক্তির বদলে অবজেক্টকে কেন্দ্র করে সাজানো হয়। অবজেক্ট হলো এমন একটি স্বয়ংসম্পূর্ণ একক, যা তথ্য (attribute) এবং সেই তথ্যের ওপর কাজ করা ফাংশন (method) দুটোই ধারণ করে। প্রোগ্রাম তৈরি হয় এমন অবজেক্টগুলোর পারস্পরিক যোগাযোগের মাধ্যমে।

        কেন OOP দরকার:

        - বড় ও জটিল সফটওয়্যার ব্যবস্থাপনা: প্রথাগত প্রোসিডিউরাল প্রোগ্রামিংয়ে হাজার হাজার লাইনের প্রোগ্রামে গ্লোবাল ডেটা সব ফাংশনের নাগালে থাকে, ফলে ভুল খুঁজে বের করা প্রায় অসম্ভব হয়ে পড়ে। OOP প্রোগ্রামকে ছোট ছোট স্বয়ংসম্পূর্ণ অবজেক্টে ভাগ করে দেয়।
        - তথ্যের নিরাপত্তা: এনক্যাপসুলেশনের মাধ্যমে ডেটা private রাখা হয়, তাই বাইরের কোনো কোড সরাসরি তা বদলাতে পারে না। ব্যাংকের ব্যালেন্স ইচ্ছেমতো বসিয়ে দেওয়া সম্ভব হয় না।
        - কোড পুনর্ব্যবহার: ইনহেরিটেন্সের মাধ্যমে আগের লেখা ক্লাস পুনরায় ব্যবহার করা যায়, তাই উন্নয়নের সময় ও খরচ দুটোই কমে।
        - সহজ রক্ষণাবেক্ষণ: কোনো পরিবর্তন একটি ক্লাসের ভেতরেই সীমাবদ্ধ থাকে, সারা প্রোগ্রামে ছড়িয়ে পড়ে না।
        - বাস্তব জগতের সঙ্গে সাদৃশ্য: ছাত্র, হিসাব, গাড়ি — বাস্তবের প্রতিটি সত্তাকে সরাসরি অবজেক্ট হিসেবে প্রকাশ করা যায়, ফলে নকশা বোঝা সহজ হয়।
        - সম্প্রসারণযোগ্যতা: পলিমরফিজমের কারণে পুরোনো কোড না বদলে নতুন শ্রেণি যোগ করা যায়।
        - দলগত উন্নয়ন: বিভিন্ন ডেভেলপার আলাদা আলাদা ক্লাস নিয়ে একই সঙ্গে কাজ করতে পারেন।

        OOP এর মৌলিক ধারণাসমূহ:

    The four principles (pillars) of OOP:

        - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

        - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

        - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

        - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

        Two supporting concepts often listed with them:
        - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
        - Object: an instance of a class, occupying memory and holding its own values for the data members.

        Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
23. **(গ) Overloading এবং overriding এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


    Answer: Overloading এবং Overriding এর মধ্যে পার্থক্য:

    | Point | Method Overloading | Method Overriding |
        |---|---|---|
        | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
        | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
        | Parameter list | Must differ in number, type or order | Must be exactly the same |
        | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
        | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
        | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
        | Access modifier | May be anything | Cannot be more restrictive than in the parent |
        | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
        | Private and final methods | Can be overloaded | Cannot be overridden |
        | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
        | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

        Example of overloading:

        ```java
        class Calculator {
            int add(int a, int b)            { return a + b; }
            double add(double a, double b)   { return a + b; }
            int add(int a, int b, int c)     { return a + b + c; }
        }
        ```

        The compiler chooses the version by looking at the arguments supplied at the call site.

        Example of overriding:

        ```java
        class Animal {
            void sound() { System.out.println("The animal makes a sound"); }
        }

        class Dog extends Animal {
            @Override
            void sound() { System.out.println("The dog barks"); }
        }

        public class Demo {
            public static void main(String[] args) {
                Animal a = new Dog();   // reference of parent type, object of child type
                a.sound();              // prints "The dog barks"
            }
        }
        ```

        The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.

        সংক্ষেপে মূল পার্থক্য: ওভারলোডিং একই ক্লাসের ভেতরে ঘটে এবং কম্পাইলেশনের সময় সিদ্ধান্ত হয়; ওভাররাইডিং প্যারেন্ট ও চাইল্ড ক্লাসের মধ্যে ঘটে এবং প্রোগ্রাম চালানোর সময় সিদ্ধান্ত হয়।
24. **What is Polymorphism? Java language এর আলোকে ব্যাখ্যা কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*


    Answer: Polymorphism শব্দটি এসেছে গ্রিক poly (বহু) ও morph (রূপ) থেকে, অর্থাৎ "বহুরূপিতা"। অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ে এর অর্থ হলো একই নাম বা ইন্টারফেস বিভিন্ন পরিস্থিতিতে ভিন্ন আচরণ করা।

    Java ভাষার আলোকে দুই প্রকার:

    ১. কম্পাইল-টাইম পলিমরফিজম (Static Polymorphism):
    - Method Overloading এর মাধ্যমে অর্জিত হয়।
    - একই ক্লাসে একই নামের একাধিক মেথড থাকে, কিন্তু প্যারামিটারের সংখ্যা, ধরন বা ক্রম ভিন্ন হয়।
    - কম্পাইলার কোন মেথডটি চালানো হবে তা কম্পাইলেশনের সময়েই ঠিক করে ফেলে, তাই একে static binding বা early binding বলা হয়।
    - উল্লেখ্য, Java তে অপারেটর ওভারলোডিং সমর্থিত নয় (কেবল + অপারেটরটি String এর জন্য পূর্বনির্ধারিতভাবে ওভারলোড করা)।

    ```java
    class Calculator {
        int add(int a, int b)              { return a + b; }
        int add(int a, int b, int c)       { return a + b + c; }
        double add(double a, double b)     { return a + b; }
    }

    public class OverloadDemo {
        public static void main(String[] args) {
            Calculator c = new Calculator();
            System.out.println(c.add(5, 10));         // 15
            System.out.println(c.add(5, 10, 15));     // 30
            System.out.println(c.add(2.5, 3.5));      // 6.0
        }
    }
    ```

    ২. রান-টাইম পলিমরফিজম (Dynamic Polymorphism):
    - Method Overriding এর মাধ্যমে অর্জিত হয়।
    - সাবক্লাস তার সুপারক্লাসের কোনো মেথডের নিজস্ব সংস্করণ লেখে, একই নাম ও একই প্যারামিটার নিয়ে।
    - কোন সংস্করণটি চলবে তা নির্ধারিত হয় রেফারেন্সের ধরন দেখে নয়, বরং প্রকৃত অবজেক্টের ধরন দেখে, এবং সেটি প্রোগ্রাম চালানোর সময়। একে dynamic method dispatch বলা হয়।
    - Java তে সব non-static, non-final, non-private মেথড ডিফল্টভাবেই virtual, তাই আলাদা কোনো কীওয়ার্ড লাগে না।

    ```java
    class Animal {
        void sound() { System.out.println("The animal makes a sound"); }
    }

    class Dog extends Animal {
        @Override
        void sound() { System.out.println("The dog barks"); }
    }

    class Cat extends Animal {
        @Override
        void sound() { System.out.println("The cat meows"); }
    }

    public class OverrideDemo {
        public static void main(String[] args) {
            Animal[] animals = { new Dog(), new Cat(), new Animal() };
            for (Animal a : animals) {
                a.sound();      // প্রকৃত অবজেক্ট অনুযায়ী সঠিক মেথড চলে
            }
        }
    }
    ```

    আউটপুট:
    ```
    The dog barks
    The cat meows
    The animal makes a sound
    ```

    Java তে পলিমরফিজমের অন্যান্য রূপ:
    - Interface এর মাধ্যমে: একই ইন্টারফেস বহু ক্লাস বাস্তবায়ন করতে পারে, এবং ইন্টারফেসের রেফারেন্স দিয়ে যেকোনো বাস্তবায়নকারী অবজেক্ট ব্যবহার করা যায়।
    - Abstract class এর মাধ্যমে: abstract মেথড প্রতিটি সাবক্লাস নিজের মতো করে বাস্তবায়ন করে।
    - Upcasting: Animal a = new Dog(); এভাবে চাইল্ড অবজেক্টকে প্যারেন্ট রেফারেন্সে রাখা।

    সুবিধা: একই কোড দিয়ে বহু ধরনের অবজেক্ট পরিচালনা করা যায়, নতুন সাবক্লাস যোগ করলে পুরোনো কোড বদলাতে হয় না, এবং দীর্ঘ if-else বা switch এড়ানো যায়।
25. **(a) What is Polymorphism? Distinguish between compile time and runtime polymorphisms.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*


    Answer: Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

    Types of polymorphism:

    Compile-time polymorphism (static polymorphism, early binding):
    - The compiler decides which version of the method to call, by examining the arguments at the call site.
    - Achieved through method overloading and operator overloading.
    - Faster, since no decision is made at run time.

    Run-time polymorphism (dynamic polymorphism, late binding):
    - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
    - Achieved through method overriding, and in C++ through virtual functions.
    - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

    Example of compile-time polymorphism (overloading):

    ```java
    class Area {
        double area(double r)           { return 3.1416 * r * r; }   // circle
        double area(double l, double b) { return l * b; }            // rectangle
        double area(int a)              { return a * a; }            // square
    }
    ```

    Example of run-time polymorphism (overriding):

    ```java
    class Shape {
        void draw() { System.out.println("Drawing a shape"); }
    }
    class Circle extends Shape {
        @Override void draw() { System.out.println("Drawing a circle"); }
    }
    class Rectangle extends Shape {
        @Override void draw() { System.out.println("Drawing a rectangle"); }
    }

    public class Demo {
        public static void main(String[] args) {
            Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
            for (Shape s : shapes) {
                s.draw();      // the correct version is chosen at run time
            }
        }
    }
    ```

    Output:
    ```
    Drawing a circle
    Drawing a rectangle
    Drawing a shape
    ```

    Advantages of polymorphism:
    - One interface can serve many implementations, so the calling code is simpler and shorter.
    - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
    - It reduces the need for long if-else or switch chains that test the type of an object.
    - It improves reusability, extensibility and maintainability.

    Distinction between compile-time and run-time polymorphism, summarised:

    | Point | Compile-time polymorphism | Run-time polymorphism |
    |---|---|---|
    | Also called | Static polymorphism, early binding | Dynamic polymorphism, late binding |
    | Achieved by | Method overloading, operator overloading | Method overriding, virtual functions |
    | When resolved | At compile time, by the compiler | At run time, by the JVM or the vtable lookup |
    | Basis of the decision | The number, type and order of the arguments | The actual class of the object at run time |
    | Inheritance required | No | Yes |
    | Speed | Faster, no run-time lookup | Slightly slower, one extra indirection |
    | Flexibility | Less | More; new subclasses can be added without changing existing code |
    | In C++ | Works without any keyword | Requires the keyword virtual in the base class |
    | In Java | Works without any keyword | Works by default; final prevents it |
    | Example | add(int, int) and add(double, double) | Animal a = new Dog(); a.sound(); |
26. **Write down the principle of OOP?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)], [BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
27. **Write down the properties/function of OOP?** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
28. **Write down the main feature of Object Oriented Programming (OOP).** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
29. **Write a Java code with a case where you have to mentioned functionalities with override method.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 757 (ET: N/A)]*


    Answer: The program below models a payroll system in which each kind of employee overrides the salary calculation and the display of details.

    ```java
    // Base class
    class Employee {
        protected String name;
        protected int id;
        protected double basicSalary;

        public Employee(String name, int id, double basicSalary) {
            this.name = name;
            this.id = id;
            this.basicSalary = basicSalary;
        }

        // methods to be overridden
        public double calculateSalary() {
            return basicSalary;
        }

        public String getDesignation() {
            return "General Employee";
        }

        public void displayDetails() {
            System.out.println("ID: " + id + " | Name: " + name
                    + " | Post: " + getDesignation()
                    + " | Salary: Tk " + calculateSalary());
        }
    }

    // Subclass 1
    class Manager extends Employee {
        private double bonus;

        public Manager(String name, int id, double basicSalary, double bonus) {
            super(name, id, basicSalary);
            this.bonus = bonus;
        }

        @Override
        public double calculateSalary() {
            return basicSalary + bonus + (basicSalary * 0.20);   // 20 per cent allowance
        }

        @Override
        public String getDesignation() {
            return "Manager";
        }
    }

    // Subclass 2
    class Developer extends Employee {
        private int overtimeHours;
        private static final double OVERTIME_RATE = 500;

        public Developer(String name, int id, double basicSalary, int overtimeHours) {
            super(name, id, basicSalary);
            this.overtimeHours = overtimeHours;
        }

        @Override
        public double calculateSalary() {
            return basicSalary + (overtimeHours * OVERTIME_RATE);
        }

        @Override
        public String getDesignation() {
            return "Software Developer";
        }
    }

    // Subclass 3
    class Intern extends Employee {
        public Intern(String name, int id) {
            super(name, id, 10000);      // fixed stipend
        }

        @Override
        public double calculateSalary() {
            return basicSalary;          // no allowance, no overtime
        }

        @Override
        public String getDesignation() {
            return "Intern";
        }
    }

    public class PayrollDemo {
        public static void main(String[] args) {
            Employee[] staff = {
                new Manager("Rahim Uddin", 101, 60000, 15000),
                new Developer("Karim Ahmed", 102, 45000, 12),
                new Intern("Jamal Hossain", 103),
                new Employee("Salma Begum", 104, 30000)
            };

            double total = 0;
            System.out.println("=========== MONTHLY PAYROLL ===========");
            for (Employee e : staff) {
                e.displayDetails();          // the overridden versions are chosen at run time
                total += e.calculateSalary();
            }
            System.out.println("=======================================");
            System.out.println("Total payroll: Tk " + total);
        }
    }
    ```

    Output:
    ```
    =========== MONTHLY PAYROLL ===========
    ID: 101 | Name: Rahim Uddin | Post: Manager | Salary: Tk 87000.0
    ID: 102 | Name: Karim Ahmed | Post: Software Developer | Salary: Tk 51000.0
    ID: 103 | Name: Jamal Hossain | Post: Intern | Salary: Tk 10000.0
    ID: 104 | Name: Salma Begum | Post: General Employee | Salary: Tk 30000.0
    =======================================
    Total payroll: Tk 178000.0
    ```

    Explanation of the overriding:
    - calculateSalary() and getDesignation() are declared in Employee and redefined in each subclass with the same name, parameters and return type. This is method overriding.
    - The @Override annotation is not compulsory, but it makes the compiler check that a method really is overriding something, which catches spelling mistakes in the method name.
    - The array is declared as Employee[], so the compiler only verifies that Employee has the methods being called. At run time the JVM inspects the actual object and dispatches to that object's version. This is dynamic method dispatch.
    - displayDetails() is written once in the base class, yet it prints the correct designation and salary for every kind of employee, because the calls it makes are themselves resolved at run time.
    - A new class such as Consultant can be added later without changing a single line of PayrollDemo, which is the practical value of run-time polymorphism.
30. **(ক) Procedural Oriented ও Object Oriented Programming Languages মধ্যে পার্থক্য কি? উভয় Language এর ২টি করে উদাহরণ দিন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*


    Answer: | Point | Procedural / Structured Programming | Object-Oriented Programming |
    |---|---|---|
    | Basic unit | The function or procedure | The object |
    | Approach | Top-down: the problem is broken into functions | Bottom-up: objects are identified and then made to interact |
    | Focus | On the procedure, that is on what is done | On the data and the objects that own it |
    | Data and function | Kept separate; data is passed to functions | Bound together inside a class |
    | Data security | Weak; global data is visible to every function | Strong; data is private and reached only through methods |
    | Data hiding | Not supported | Supported through encapsulation and access specifiers |
    | Code reuse | Only by calling the same function again | Through inheritance and composition, and by extending existing classes |
    | Handling change | A change to a data structure may require changes in many functions | A change is confined inside the class |
    | Suitability | Small and medium programs | Large and complex systems |
    | Overloading | Not supported | Supported |
    | Inheritance and polymorphism | Not available | Available |
    | Real-world modelling | Poor | Natural, since objects correspond to real entities |
    | Examples | C, Pascal, FORTRAN, COBOL, BASIC | C++, Java, Python, C#, Ruby, Smalltalk |

    Why OOP is preferred for large systems: it localises change. If the internal representation of an account balance is altered, only the Account class must be modified, and every other part of the program that uses the public methods continues to work. In a procedural program the same change could require edits in dozens of functions.

    উভয় ভাষার দুটি করে উদাহরণ:
    - প্রোসিডিউরাল ওরিয়েন্টেড: C এবং Pascal (এছাড়া FORTRAN, COBOL, BASIC)
    - অবজেক্ট ওরিয়েন্টেড: Java এবং C++ (এছাড়া Python, C#, Ruby, Smalltalk)

    উল্লেখযোগ্য: C++ ও Python কে বলা হয় মাল্টি-প্যারাডাইম ভাষা, কারণ এগুলোতে প্রোসিডিউরাল ও অবজেক্ট ওরিয়েন্টেড দুই পদ্ধতিতেই প্রোগ্রাম লেখা যায়। Java প্রায় সম্পূর্ণ অবজেক্ট ওরিয়েন্টেড, তবে এতে int ও double এর মতো প্রিমিটিভ টাইপ থাকায় একে বিশুদ্ধ OOP ভাষা বলা হয় না; Smalltalk কে বিশুদ্ধ OOP ভাষা ধরা হয়।
31. **(i) Object Oriented Programming এর যেকোন দুটি বৈশিষ্ট্য উদাহরণসহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 781 (ET: N/A)]*


    Answer: OOP এর যেকোনো দুটি বৈশিষ্ট্য উদাহরণসহ নিচে ব্যাখ্যা করা হলো।

    বৈশিষ্ট্য ১ — এনক্যাপসুলেশন (Encapsulation):

    তথ্য এবং সেই তথ্যের ওপর কাজ করা মেথডগুলোকে একটি ক্লাসের ভেতরে আবদ্ধ করা এবং বাইরের জগত থেকে অভ্যন্তরীণ অবস্থা আড়াল করাকে এনক্যাপসুলেশন বলে। ডেটা মেম্বারগুলো private ঘোষণা করা হয় এবং কেবল public মেথডের মাধ্যমে সেগুলোতে পৌঁছানো যায়।

    ```java
    class BankAccount {
        private double balance;          // বাইরে থেকে সরাসরি ছোঁয়া যাবে না

        public BankAccount(double initial) {
            this.balance = (initial >= 0) ? initial : 0;
        }

        public void deposit(double amount) {
            if (amount > 0) {
                balance += amount;
            } else {
                System.out.println("Invalid amount");
            }
        }

        public boolean withdraw(double amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                return true;
            }
            System.out.println("Insufficient balance or invalid amount");
            return false;
        }

        public double getBalance() {      // কেবল পড়ার সুযোগ, লেখার নয়
            return balance;
        }
    }

    public class Demo {
        public static void main(String[] args) {
            BankAccount acc = new BankAccount(5000);
            // acc.balance = 1000000;     // কম্পাইল ত্রুটি: balance private
            acc.deposit(2000);
            acc.withdraw(10000);          // প্রত্যাখ্যাত
            System.out.println("Balance: " + acc.getBalance());   // 7000.0
        }
    }
    ```

    সুবিধা: ব্যালেন্স কখনো অবৈধ মানে পৌঁছাতে পারে না, কারণ প্রতিটি পরিবর্তন যাচাইয়ের মধ্য দিয়ে যায়। ভবিষ্যতে ভেতরের ডেটা টাইপ বদলালেও ব্যবহারকারীর কোড অপরিবর্তিত থাকে।

    বৈশিষ্ট্য ২ — পলিমরফিজম (Polymorphism):

    একই নাম বা ইন্টারফেস বিভিন্ন পরিস্থিতিতে ভিন্ন আচরণ করাকে পলিমরফিজম বলে। এটি দুই ধরনের: কম্পাইল-টাইম (method overloading) ও রান-টাইম (method overriding)।

    ```java
    class Shape {
        void draw() { System.out.println("Drawing a shape"); }
    }

    class Circle extends Shape {
        @Override void draw() { System.out.println("Drawing a circle"); }
    }

    class Triangle extends Shape {
        @Override void draw() { System.out.println("Drawing a triangle"); }
    }

    public class PolyDemo {
        public static void main(String[] args) {
            Shape[] shapes = { new Circle(), new Triangle(), new Shape() };
            for (Shape s : shapes) {
                s.draw();      // প্রকৃত অবজেক্ট অনুযায়ী সঠিক সংস্করণ চলে
            }
        }
    }
    ```

    আউটপুট:
    ```
    Drawing a circle
    Drawing a triangle
    Drawing a shape
    ```

    সুবিধা: একটিমাত্র লুপ দিয়ে বহু ধরনের অবজেক্ট পরিচালনা করা যায়। ভবিষ্যতে Rectangle নামে নতুন শ্রেণি যোগ করলেও এই লুপের একটি লাইনও বদলাতে হবে না।

    অন্য দুটি বৈশিষ্ট্য, সংক্ষেপে: ইনহেরিটেন্স (এক ক্লাস অন্য ক্লাসের বৈশিষ্ট্য অর্জন করে, ফলে কোড পুনর্ব্যবহৃত হয়) এবং অ্যাবস্ট্রাকশন (কেবল প্রয়োজনীয় অংশ দেখানো, জটিলতা আড়াল করা)।
32. **(i) Object Oriented Programming এ Static binding and Dynamic binding কি? ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*


    Answer: Static Binding ও Dynamic Binding বলতে বোঝায় কোন মেথড বা ফাংশন কলটির সঙ্গে কোন প্রকৃত কোড যুক্ত হবে, সেই সিদ্ধান্ত কখন নেওয়া হয়।

    Static Binding (Early Binding / Compile-time Binding):
    - সিদ্ধান্তটি কম্পাইলেশনের সময়েই নেওয়া হয়।
    - কম্পাইলার রেফারেন্স বা পয়েন্টারের ঘোষিত ধরন দেখে ঠিক করে ফেলে কোন কোড চলবে।
    - কোন কোন ক্ষেত্রে ঘটে: static মেথড, private মেথড, final মেথড, ভেরিয়েবল, এবং method overloading।
    - সুবিধা: দ্রুত, কারণ চালানোর সময় কোনো অনুসন্ধান লাগে না; কম্পাইলার আগেই ত্রুটি ধরতে পারে।
    - সীমাবদ্ধতা: নমনীয়তা কম।

    ```java
    class Parent {
        static void show() { System.out.println("Parent static method"); }
        private void secret() { System.out.println("Parent private method"); }
    }

    class Child extends Parent {
        static void show() { System.out.println("Child static method"); }
    }

    public class StaticBindingDemo {
        public static void main(String[] args) {
            Parent p = new Child();
            p.show();      // আউটপুট: Parent static method
        }
    }
    ```

    ব্যাখ্যা: p এর ঘোষিত ধরন Parent, তাই কম্পাইলার Parent এর static মেথডটিই বেছে নেয়, যদিও প্রকৃত অবজেক্ট Child। static মেথড ওভাররাইড হয় না, কেবল hide হয়।

    Dynamic Binding (Late Binding / Run-time Binding):
    - সিদ্ধান্তটি প্রোগ্রাম চালানোর সময় নেওয়া হয়।
    - রেফারেন্সের ধরন নয়, বরং প্রকৃত অবজেক্টের ধরন দেখে সঠিক মেথড নির্বাচন করা হয়।
    - কোন ক্ষেত্রে ঘটে: method overriding, অর্থাৎ রান-টাইম পলিমরফিজম। C++ এ এর জন্য virtual কীওয়ার্ড লাগে; Java তে সব সাধারণ মেথড ডিফল্টভাবেই virtual।
    - সুবিধা: নমনীয়তা ও সম্প্রসারণযোগ্যতা; নতুন সাবক্লাস যোগ করলেও পুরোনো কোড বদলাতে হয় না।
    - সীমাবদ্ধতা: সামান্য ধীর, কারণ virtual table এ একটি অতিরিক্ত অনুসন্ধান লাগে।

    ```java
    class Animal {
        void sound() { System.out.println("Animal makes a sound"); }
    }

    class Dog extends Animal {
        @Override void sound() { System.out.println("Dog barks"); }
    }

    public class DynamicBindingDemo {
        public static void main(String[] args) {
            Animal a = new Dog();
            a.sound();     // আউটপুট: Dog barks
        }
    }
    ```

    ব্যাখ্যা: a এর ঘোষিত ধরন Animal, কিন্তু প্রকৃত অবজেক্ট Dog। মেথডটি ওভাররাইড করা হয়েছে, তাই চালানোর সময় JVM প্রকৃত অবজেক্ট দেখে Dog এর সংস্করণটি চালায়।

    তুলনামূলক সারণি:

    | বিষয় | Static Binding | Dynamic Binding |
    |---|---|---|
    | অন্য নাম | Early binding | Late binding |
    | সিদ্ধান্ত কখন | কম্পাইলেশনের সময় | প্রোগ্রাম চালানোর সময় |
    | সিদ্ধান্তের ভিত্তি | রেফারেন্সের ঘোষিত ধরন | প্রকৃত অবজেক্টের ধরন |
    | কোন ক্ষেত্রে | static, private, final মেথড ও overloading | overriding ও virtual function |
    | গতি | দ্রুত | তুলনামূলক ধীর |
    | নমনীয়তা | কম | বেশি |
    | পলিমরফিজমের ধরন | কম্পাইল-টাইম | রান-টাইম |
    | অভ্যন্তরীণ কৌশল | সরাসরি ফাংশন কল | virtual table এ অনুসন্ধান |
33. **Complete the following java program.** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*
```java
class A{
    int alpha;
    int beta;
    public A(int alpha, int beta){
        this.alpha = alpha;
        this.beta = beta;
    }
    public void display(){
        System.out.println("Alpha"+alpha+ "\nBeta"+beta);
    }
}
class Gamma extends A{
    int gamma;
    public Gamma(int alpha, int beta, int gamma){
        super(alpha, beta);
        this.gamma = gamma;
    }
    @Override
    public void display(){
        super.display();
        System.out.println("Gamma"+gamma);
    }
}
public class main{
    public static void main(String[]args){
        Gamma g = new Gamma(3,30,10);
        g.display();
    }
}
```


    Answer: The program is already complete and syntactically correct. It demonstrates single inheritance, constructor chaining with super(), and method overriding with a call to super.display().

    The completed program, with a small correction to the printing so that the labels are readable:

    ```java
    class A {
        int alpha;
        int beta;

        public A(int alpha, int beta) {
            this.alpha = alpha;      // 'this' distinguishes the field from the parameter
            this.beta  = beta;
        }

        public void display() {
            System.out.println("Alpha = " + alpha);
            System.out.println("Beta  = " + beta);
        }
    }

    class Gamma extends A {
        int gamma;

        public Gamma(int alpha, int beta, int gamma) {
            super(alpha, beta);      // must be the first statement: calls A's constructor
            this.gamma = gamma;
        }

        @Override
        public void display() {
            super.display();         // run the parent version first
            System.out.println("Gamma = " + gamma);
        }
    }

    public class Main {
        public static void main(String[] args) {
            Gamma g = new Gamma(3, 30, 10);
            g.display();
        }
    }
    ```

    Output of the program as originally written:
    ```
    Alpha3
    Beta30
    Gamma10
    ```

    Output of the corrected version:
    ```
    Alpha = 3
    Beta  = 30
    Gamma = 10
    ```

    Step-by-step explanation:
    - new Gamma(3, 30, 10) invokes the Gamma constructor with alpha = 3, beta = 30, gamma = 10.
    - The first statement, super(alpha, beta), calls the constructor of class A, which sets the inherited fields alpha to 3 and beta to 30. Java requires super() to be the first statement in a constructor, because the parent part of the object must be initialised before the child part.
    - Control then returns to the Gamma constructor, which sets gamma to 10.
    - g.display() calls the Gamma version, because Gamma overrides display().
    - Inside it, super.display() explicitly invokes the version in A, which prints alpha and beta.
    - Then the Gamma version prints gamma.

    Concepts demonstrated:
    - Inheritance, with class Gamma extends A.
    - Constructor chaining using super(), so that the base class initialises its own fields.
    - Method overriding, marked with the @Override annotation.
    - Calling the parent implementation from the child with super.method(), which extends the parent behaviour rather than replacing it.
    - The this keyword, used to distinguish a field from a parameter of the same name.

    Note on style: in Java a public class must be declared in a file of the same name, and the convention is to begin a class name with a capital letter, so main should be renamed Main and stored in Main.java.
34. **Write a C/C++ Program that has a Class Account, Subclass Savings Account, Current Account etc with related hierarchy way.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 834 (ET: N/A)]*


    Answer: The program below builds an account hierarchy in C++, with a base class Account and two derived classes SavingsAccount and CurrentAccount, using virtual functions for run-time polymorphism.

    ```cpp
    #include <iostream>
    #include <string>
    #include <iomanip>
    using namespace std;

    // ---------- Base class ----------
    class Account {
    protected:
        string holderName;
        string accountNumber;
        double balance;

    public:
        Account(string name, string accNo, double initial)
            : holderName(name), accountNumber(accNo), balance(initial >= 0 ? initial : 0) {}

        void deposit(double amount) {
            if (amount <= 0) {
                cout << "Deposit amount must be positive." << endl;
                return;
            }
            balance += amount;
            cout << "Deposited Tk " << amount << ". Balance: Tk " << balance << endl;
        }

        // virtual, because each account type withdraws under different rules
        virtual void withdraw(double amount) {
            if (amount <= 0) {
                cout << "Invalid amount." << endl;
            } else if (amount > balance) {
                cout << "Insufficient balance." << endl;
            } else {
                balance -= amount;
                cout << "Withdrew Tk " << amount << ". Balance: Tk " << balance << endl;
            }
        }

        virtual double calculateInterest() { return 0; }
        virtual string accountType() { return "General Account"; }

        virtual void display() {
            cout << fixed << setprecision(2);
            cout << "--------------------------------------" << endl;
            cout << "Type    : " << accountType() << endl;
            cout << "Holder  : " << holderName << endl;
            cout << "Acc No  : " << accountNumber << endl;
            cout << "Balance : Tk " << balance << endl;
            cout << "Interest: Tk " << calculateInterest() << endl;
        }

        virtual ~Account() {}      // virtual destructor is essential
    };

    // ---------- Derived class 1 ----------
    class SavingsAccount : public Account {
        double interestRate;
        double minimumBalance;

    public:
        SavingsAccount(string name, string accNo, double initial, double rate)
            : Account(name, accNo, initial), interestRate(rate), minimumBalance(500) {}

        void withdraw(double amount) override {
            if (amount <= 0) {
                cout << "Invalid amount." << endl;
            } else if (balance - amount < minimumBalance) {
                cout << "Cannot withdraw. Minimum balance of Tk "
                     << minimumBalance << " must be maintained." << endl;
            } else {
                balance -= amount;
                cout << "Withdrew Tk " << amount << ". Balance: Tk " << balance << endl;
            }
        }

        double calculateInterest() override {
            return balance * interestRate / 100;
        }

        string accountType() override { return "Savings Account"; }
    };

    // ---------- Derived class 2 ----------
    class CurrentAccount : public Account {
        double overdraftLimit;

    public:
        CurrentAccount(string name, string accNo, double initial, double limit)
            : Account(name, accNo, initial), overdraftLimit(limit) {}

        void withdraw(double amount) override {
            if (amount <= 0) {
                cout << "Invalid amount." << endl;
            } else if (amount > balance + overdraftLimit) {
                cout << "Exceeds overdraft limit of Tk " << overdraftLimit << endl;
            } else {
                balance -= amount;
                cout << "Withdrew Tk " << amount << ". Balance: Tk " << balance << endl;
            }
        }

        double calculateInterest() override { return 0; }   // current accounts earn none

        string accountType() override { return "Current Account"; }
    };

    // ---------- Main ----------
    int main() {
        Account* accounts[2];
        accounts[0] = new SavingsAccount("Rahim Uddin", "SB-1001", 10000, 5.0);
        accounts[1] = new CurrentAccount("Karim Traders", "CA-2001", 20000, 50000);

        for (int i = 0; i < 2; i++) {
            accounts[i]->display();
            accounts[i]->deposit(5000);
            accounts[i]->withdraw(60000);    // each applies its own rule
            cout << endl;
        }

        for (int i = 0; i < 2; i++) delete accounts[i];
        return 0;
    }
    ```

    Output:
    ```
    --------------------------------------
    Type    : Savings Account
    Holder  : Rahim Uddin
    Acc No  : SB-1001
    Balance : Tk 10000.00
    Interest: Tk 500.00
    Deposited Tk 5000. Balance: Tk 15000
    Cannot withdraw. Minimum balance of Tk 500.00 must be maintained.

    --------------------------------------
    Type    : Current Account
    Holder  : Karim Traders
    Acc No  : CA-2001
    Balance : Tk 20000.00
    Interest: Tk 0.00
    Deposited Tk 5000. Balance: Tk 25000
    Withdrew Tk 60000. Balance: Tk -35000
    ```

    Points demonstrated:
    - Hierarchical inheritance: two classes derive from one common base.
    - Encapsulation: balance is protected, so it is reachable inside the hierarchy but not from outside.
    - Run-time polymorphism: withdraw(), calculateInterest() and accountType() are virtual, so the version belonging to the actual object runs even though the pointer is of type Account*.
    - Constructor chaining through the initialisation list, which passes the common data up to the base class.
    - A virtual destructor, without which deleting a derived object through a base pointer would be undefined behaviour.
    - Business rules differ correctly: the savings account enforces a minimum balance and pays interest, while the current account allows an overdraft and pays none.
35. **Write the definition of Inheritance, Polymorphism with coding example.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 835 (ET: N/A)]*


    Answer: Inheritance is the mechanism by which one class acquires the data members and member functions of another class. The class that is inherited from is called the base, parent or superclass, and the class that inherits is called the derived, child or subclass. It expresses an "is-a" relationship: a Dog is an Animal, a SavingsAccount is an Account.

        Advantages:
        - Reuse of code: common members are written once in the base class and are available to every derived class.
        - Extensibility: new functionality is added in a derived class without touching or retesting the base class.
        - It enables run-time polymorphism, because a base-class reference can hold a derived-class object.
        - It makes the design match the real-world hierarchy, so the code is easier to understand and maintain.
        - It reduces duplication, which reduces the chance of inconsistent bug fixes.

        Types of inheritance:

        - Single inheritance: one derived class inherits from one base class.
          A -> B

        - Multilevel inheritance: a derived class itself becomes the base of another class, forming a chain.
          A -> B -> C

        - Hierarchical inheritance: several derived classes inherit from one common base class.
          A -> B, A -> C, A -> D

        - Multiple inheritance: one derived class inherits from more than one base class.
          A, B -> C
          Supported by C++ and Python. Java does not support it for classes, in order to avoid the diamond problem, but it allows a class to implement several interfaces.

        - Hybrid inheritance: a combination of two or more of the above, for example hierarchical together with multiple inheritance. This is the arrangement in which the diamond problem arises.

        Example in Java:

        ```java
        class Vehicle {
            String brand;
            void start() { System.out.println(brand + " is starting"); }
        }

        class Car extends Vehicle {
            int doors;
            void openBoot() { System.out.println("Boot opened"); }
        }

        public class Demo {
            public static void main(String[] args) {
                Car c = new Car();
                c.brand = "Toyota";
                c.doors = 4;
                c.start();       // inherited from Vehicle
                c.openBoot();    // its own method
            }
        }
        ```

        Access rules: public members of the base class remain public in the derived class, protected members are accessible inside the derived class, and private members are inherited but are not directly accessible; they can be reached only through public or protected methods of the base class.

        The keyword: extends in Java, and a colon with an access specifier in C++, for example class Car : public Vehicle.

    Polymorphism comes from the Greek words poly (many) and morph (form), so it means "many forms". In object-oriented programming it is the ability of a single interface, name or operation to behave differently depending on the object it acts upon or the arguments it is given.

        Types of polymorphism:

        Compile-time polymorphism (static polymorphism, early binding):
        - The compiler decides which version of the method to call, by examining the arguments at the call site.
        - Achieved through method overloading and operator overloading.
        - Faster, since no decision is made at run time.

        Run-time polymorphism (dynamic polymorphism, late binding):
        - The decision is deferred until the program is running, and is made from the actual type of the object rather than the type of the reference.
        - Achieved through method overriding, and in C++ through virtual functions.
        - Slightly slower, because a lookup through the virtual table is needed, but it is what makes extensible design possible.

        Example of compile-time polymorphism (overloading):

        ```java
        class Area {
            double area(double r)           { return 3.1416 * r * r; }   // circle
            double area(double l, double b) { return l * b; }            // rectangle
            double area(int a)              { return a * a; }            // square
        }
        ```

        Example of run-time polymorphism (overriding):

        ```java
        class Shape {
            void draw() { System.out.println("Drawing a shape"); }
        }
        class Circle extends Shape {
            @Override void draw() { System.out.println("Drawing a circle"); }
        }
        class Rectangle extends Shape {
            @Override void draw() { System.out.println("Drawing a rectangle"); }
        }

        public class Demo {
            public static void main(String[] args) {
                Shape[] shapes = { new Circle(), new Rectangle(), new Shape() };
                for (Shape s : shapes) {
                    s.draw();      // the correct version is chosen at run time
                }
            }
        }
        ```

        Output:
        ```
        Drawing a circle
        Drawing a rectangle
        Drawing a shape
        ```

        Advantages of polymorphism:
        - One interface can serve many implementations, so the calling code is simpler and shorter.
        - New subclasses can be added without changing the code that uses them, which supports the open-closed principle.
        - It reduces the need for long if-else or switch chains that test the type of an object.
        - It improves reusability, extensibility and maintainability.
36. **Explain method overloading and Method overriding with example.** *[RAKUB Programmer (PO) 12.10.2021 compact it 850-851 (ET: N/A)]*


    Answer: | Point | Method Overloading | Method Overriding |
    |---|---|---|
    | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
    | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
    | Parameter list | Must differ in number, type or order | Must be exactly the same |
    | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
    | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
    | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
    | Access modifier | May be anything | Cannot be more restrictive than in the parent |
    | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
    | Private and final methods | Can be overloaded | Cannot be overridden |
    | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
    | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

    Example of overloading:

    ```java
    class Calculator {
        int add(int a, int b)            { return a + b; }
        double add(double a, double b)   { return a + b; }
        int add(int a, int b, int c)     { return a + b + c; }
    }
    ```

    The compiler chooses the version by looking at the arguments supplied at the call site.

    Example of overriding:

    ```java
    class Animal {
        void sound() { System.out.println("The animal makes a sound"); }
    }

    class Dog extends Animal {
        @Override
        void sound() { System.out.println("The dog barks"); }
    }

    public class Demo {
        public static void main(String[] args) {
            Animal a = new Dog();   // reference of parent type, object of child type
            a.sound();              // prints "The dog barks"
        }
    }
    ```

    The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.
37. **OOP problem (Inheritance related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

38. **Object Oriented Programming (OOP) language -এর প্রধান বৈশিষ্ট্য গুলো কী কী? দুটি OOP language -এর নাম লিখুন।** *[41th BCS 2021 compact it 881 (ET: N/A)]*


    Answer: Object Oriented Programming ভাষার প্রধান বৈশিষ্ট্যসমূহ:

    The four principles (pillars) of OOP:

        - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

        - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

        - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

        - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

        Two supporting concepts often listed with them:
        - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
        - Object: an instance of a class, occupying memory and holding its own values for the data members.

        Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).

        দুটি OOP ভাষার নাম:
        - Java
        - C++

        অন্যান্য উল্লেখযোগ্য OOP ভাষা: Python, C#, Ruby, Smalltalk, Objective-C, Swift, Kotlin ও PHP।
39. **(b) What is function overloading and operator overloading. Give example.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892 (ET: N/A)]*


    Answer:

    Function overloading:
    - Two or more functions in the same scope have the same name but differ in the number, the type or the order of their parameters.
    - The compiler selects the correct one at compile time by matching the arguments at the call site, so it is compile-time polymorphism.
    - The return type alone cannot distinguish two overloads.

    Example of function overloading:

    ```cpp
    #include <iostream>
    using namespace std;

    class Print {
    public:
        void show(int i)          { cout << "Integer: " << i << endl; }
        void show(double d)       { cout << "Double: "  << d << endl; }
        void show(string s)       { cout << "String: "  << s << endl; }
        void show(int a, int b)   { cout << "Two integers: " << a << ", " << b << endl; }
    };

    int main() {
        Print p;
        p.show(10);            // Integer: 10
        p.show(3.14);          // Double: 3.14
        p.show("Hello");       // String: Hello
        p.show(5, 7);          // Two integers: 5, 7
        return 0;
    }
    ```

    Operator overloading:
    - An operator such as +, -, *, ==, << or [] is given an additional meaning for a user-defined type, so that objects of a class can be combined with the familiar operator syntax.
    - It makes user-defined types behave like built-in types, which greatly improves readability. Writing c3 = c1 + c2 is far clearer than c3 = c1.add(c2).
    - It is implemented by defining a function whose name is the keyword operator followed by the symbol.
    - Rules in C++: the precedence, associativity and number of operands of an operator cannot be changed; a new operator symbol cannot be invented; and a few operators cannot be overloaded, namely the scope resolution operator, the member selection operator, the size-of operator and the ternary conditional operator.

    Example of operator overloading:

    ```cpp
    #include <iostream>
    using namespace std;

    class Complex {
        double real, imag;
    public:
        Complex(double r = 0, double i = 0) : real(r), imag(i) {}

        // overloading the + operator
        Complex operator + (const Complex& c) {
            return Complex(real + c.real, imag + c.imag);
        }

        // overloading the - operator
        Complex operator - (const Complex& c) {
            return Complex(real - c.real, imag - c.imag);
        }

        // overloading the == operator
        bool operator == (const Complex& c) {
            return (real == c.real && imag == c.imag);
        }

        void display() {
            cout << real << (imag >= 0 ? " + " : " - ") << abs(imag) << "i" << endl;
        }
    };

    int main() {
        Complex c1(3, 4), c2(1, 2);

        Complex c3 = c1 + c2;      // becomes c1.operator+(c2)
        Complex c4 = c1 - c2;

        c3.display();              // 4 + 6i
        c4.display();              // 2 + 2i

        cout << (c1 == c2 ? "Equal" : "Not equal") << endl;   // Not equal
        return 0;
    }
    ```

    Comparison:

    | Point | Function overloading | Operator overloading |
    |---|---|---|
    | What is redefined | A function name | An operator symbol |
    | Purpose | One name for several related operations | Familiar operator syntax for user-defined types |
    | Binding | Compile time | Compile time |
    | Available in Java | Yes | No, except the built-in + for String |
    | Available in C++ | Yes | Yes |
    | Available in Python | Simulated with default arguments | Yes, through special methods such as __add__ |

    Note on Java: Java deliberately omits operator overloading, on the ground that it is often misused and makes code harder to read. C++ and Python support it fully.
40. **১. সাব-ক্লাস এর অপর নাম কি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: সাব-ক্লাস (Sub-class) এর অপর নাম:
    - ডেরাইভড ক্লাস (Derived class)
    - চাইল্ড ক্লাস (Child class)
    - এক্সটেন্ডেড ক্লাস (Extended class)

    এর বিপরীত ধারণাটির নামগুলো:
    - সুপার ক্লাস (Super class)
    - বেস ক্লাস (Base class)
    - প্যারেন্ট ক্লাস (Parent class)

    ব্যাখ্যা: ইনহেরিটেন্সে যে ক্লাস অন্য ক্লাসের বৈশিষ্ট্য ও আচরণ উত্তরাধিকারসূত্রে গ্রহণ করে, তাকে সাবক্লাস বা ডেরাইভড ক্লাস বলে। যে ক্লাস থেকে গ্রহণ করা হয়, তাকে সুপারক্লাস বা বেস ক্লাস বলে।

    উদাহরণ (Java):

    ```java
    class Animal { }                      // superclass / base class / parent class
    class Dog extends Animal { }          // subclass / derived class / child class
    ```

    উদাহরণ (C++):

    ```cpp
    class Animal { };                     // base class
    class Dog : public Animal { };        // derived class
    ```

    পরিভাষার ব্যবহার: Java ও Smalltalk এ সাধারণত superclass ও subclass বলা হয়; C++ এ base class ও derived class বলা হয়; আর সাধারণ কথ্য ভাষায় parent ও child class বলা হয়। তিনটিই একই অর্থে ব্যবহৃত।
41. **৮. অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর বৈশিষ্ট্য লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
42. **Inheritance is one of important issues for any object oriented programming language. The main advantage of Inheritance is the ability to reuse the code. Explain in brief different types of Inheritance.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 981 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer: Inheritance is the mechanism by which one class acquires the data members and member functions of another class. The class that is inherited from is called the base, parent or superclass, and the class that inherits is called the derived, child or subclass. It expresses an "is-a" relationship: a Dog is an Animal, a SavingsAccount is an Account.

    Advantages:
    - Reuse of code: common members are written once in the base class and are available to every derived class.
    - Extensibility: new functionality is added in a derived class without touching or retesting the base class.
    - It enables run-time polymorphism, because a base-class reference can hold a derived-class object.
    - It makes the design match the real-world hierarchy, so the code is easier to understand and maintain.
    - It reduces duplication, which reduces the chance of inconsistent bug fixes.

    Types of inheritance:

    - Single inheritance: one derived class inherits from one base class.
      A -> B

    - Multilevel inheritance: a derived class itself becomes the base of another class, forming a chain.
      A -> B -> C

    - Hierarchical inheritance: several derived classes inherit from one common base class.
      A -> B, A -> C, A -> D

    - Multiple inheritance: one derived class inherits from more than one base class.
      A, B -> C
      Supported by C++ and Python. Java does not support it for classes, in order to avoid the diamond problem, but it allows a class to implement several interfaces.

    - Hybrid inheritance: a combination of two or more of the above, for example hierarchical together with multiple inheritance. This is the arrangement in which the diamond problem arises.

    Example in Java:

    ```java
    class Vehicle {
        String brand;
        void start() { System.out.println(brand + " is starting"); }
    }

    class Car extends Vehicle {
        int doors;
        void openBoot() { System.out.println("Boot opened"); }
    }

    public class Demo {
        public static void main(String[] args) {
            Car c = new Car();
            c.brand = "Toyota";
            c.doors = 4;
            c.start();       // inherited from Vehicle
            c.openBoot();    // its own method
        }
    }
    ```

    Access rules: public members of the base class remain public in the derived class, protected members are accessible inside the derived class, and private members are inherited but are not directly accessible; they can be reached only through public or protected methods of the base class.

    The keyword: extends in Java, and a colon with an access specifier in C++, for example class Car : public Vehicle.
43. **Object Oriented Programming এর চারটি গুরুত্বপূর্ণ বৈশিষ্ট্য লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1020-1021 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: binding the data and the methods that operate on that data into a single unit called a class, and hiding the internal state from the outside world. Data members are declared private and are reached only through public getter and setter methods. This protects the object from invalid changes and makes it possible to alter the internal implementation without breaking the code that uses it.

    - Abstraction: showing only the essential features of an object and hiding the internal details. A driver uses the steering wheel and the pedals without knowing how the engine works. In code it is implemented with abstract classes and interfaces, which declare what an object can do without specifying how.

    - Inheritance: a new class (the derived or child class) acquires the properties and behaviour of an existing class (the base or parent class). It expresses an "is-a" relationship, promotes reuse of code, and allows a hierarchy to be built. Types are single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: the same interface behaving differently depending on the object or the arguments. The word means "many forms". It appears as compile-time polymorphism through method overloading and operator overloading, and as run-time polymorphism through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
44. **What are the difference between Structure Programming and Objest Oriented Progrmamming?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*


    Answer: | Point | Procedural / Structured Programming | Object-Oriented Programming |
    |---|---|---|
    | Basic unit | The function or procedure | The object |
    | Approach | Top-down: the problem is broken into functions | Bottom-up: objects are identified and then made to interact |
    | Focus | On the procedure, that is on what is done | On the data and the objects that own it |
    | Data and function | Kept separate; data is passed to functions | Bound together inside a class |
    | Data security | Weak; global data is visible to every function | Strong; data is private and reached only through methods |
    | Data hiding | Not supported | Supported through encapsulation and access specifiers |
    | Code reuse | Only by calling the same function again | Through inheritance and composition, and by extending existing classes |
    | Handling change | A change to a data structure may require changes in many functions | A change is confined inside the class |
    | Suitability | Small and medium programs | Large and complex systems |
    | Overloading | Not supported | Supported |
    | Inheritance and polymorphism | Not available | Available |
    | Real-world modelling | Poor | Natural, since objects correspond to real entities |
    | Examples | C, Pascal, FORTRAN, COBOL, BASIC | C++, Java, Python, C#, Ruby, Smalltalk |

    Why OOP is preferred for large systems: it localises change. If the internal representation of an account balance is altered, only the Account class must be modified, and every other part of the program that uses the public methods continues to work. In a procedural program the same change could require edits in dozens of functions.
45. **Object Oriented Programming এ Method Overloading and Method Overriding এর মধ্যে পার্থক্য কী?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*


    Answer: | Point | Method Overloading | Method Overriding |
    |---|---|---|
    | Definition | Two or more methods in the same class have the same name but different parameter lists | A subclass provides its own implementation of a method already defined in its superclass |
    | Where it occurs | Within one class (or between a class and its subclass) | Between a superclass and a subclass, so inheritance is required |
    | Parameter list | Must differ in number, type or order | Must be exactly the same |
    | Return type | May differ, but it alone cannot distinguish two overloads | Must be the same, or a covariant subtype |
    | Binding | Compile-time, also called static binding or early binding | Run-time, also called dynamic binding or late binding |
    | Type of polymorphism | Compile-time polymorphism | Run-time polymorphism |
    | Access modifier | May be anything | Cannot be more restrictive than in the parent |
    | Static methods | Can be overloaded | Cannot be overridden; they are hidden instead |
    | Private and final methods | Can be overloaded | Cannot be overridden |
    | Purpose | Convenience; one logical operation for different kinds of input | Specialisation; a subclass changes inherited behaviour |
    | Performance | Slightly faster, since the target is fixed at compile time | Slightly slower, since the target is resolved at run time |

    Example of overloading:

    ```java
    class Calculator {
        int add(int a, int b)            { return a + b; }
        double add(double a, double b)   { return a + b; }
        int add(int a, int b, int c)     { return a + b + c; }
    }
    ```

    The compiler chooses the version by looking at the arguments supplied at the call site.

    Example of overriding:

    ```java
    class Animal {
        void sound() { System.out.println("The animal makes a sound"); }
    }

    class Dog extends Animal {
        @Override
        void sound() { System.out.println("The dog barks"); }
    }

    public class Demo {
        public static void main(String[] args) {
            Animal a = new Dog();   // reference of parent type, object of child type
            a.sound();              // prints "The dog barks"
        }
    }
    ```

    The reference type is Animal, so the compiler accepts the call; but the object is a Dog, so at run time the JVM dispatches to the Dog version. This is dynamic method dispatch, the mechanism of run-time polymorphism.

## Java Programming & Methods (11)

1. **Write a Java Code which return a value.** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*

2. **Write a Java Code....** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*

3. **What does run Finalization do?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **What syntax is used for calling static methods in class?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

5. **Consider the following code:** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*
```java
Public class Class A {
    Public void m1() {}
    Public void m2(int i) {}
    Public void m3(int i) {}
    Public static void m4(int i) {}
}
Public class class B extends class A {
    Public static void m1(int i) {}
    Public void m2(int i) {}
    Public void m3(string s) {}
    Public static void m4(int i) {}
}
```
**Mention which of the methods overload, override and hied supper class methods. What about the remaining method?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 437 (ET: BIBM)]*

6. **অথবা, (ক) ‘Static’ কীওয়ার্ডটি ব্যাখ্যা করার জন্যে Static Variable এবং Static Method ব্যবহার করে একটি প্রোগ্রাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*

7. **Write a java program to counting the vowel and consonant into a given strings.** *[BOF Assistant Programmer 2022 compact it 735 (ET: MIST)]*

8. **Where will be the most chance of the grabage collector being invoked?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

9. **In Java program. Write the method in given box for the Electric bill calculation if unit is less then 100 then unit rate 4.0 take and after 100-unit rate is 5.50 and reaming unit rate is 6.00. [Bill rate 4.0 if unit<=100, Bill rate 5.50 if (unit>100 && unit<=200), Bill rate 6.00 for remaining units.]** *[BPDB Assistant Engineer (CSE) 2021 compact it 816-817 (ET: BUET)]*

10. **C# language এর একটি প্রোগ্রাম লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

11. **Write java program for calculate electricity bill using class and object.** *[Sundharban Gas Assistant Programmer 2020 compact it 1047-1048 (ET: N/A)]*

## Class Design & Object-Oriented Modeling (7)

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 425 (ET: BIBM)]*

2. **What are the built in classes?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

3. **অথবা, (ক) উদাহরণসহ Class এবং Object এর মধ্যে পার্থক্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

4. **(খ) উদাহরণসহ ক্লাস এবং অবজেক্ট এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

5. **Define Class and Object in C++ with example.** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

6. **What are the common activities on OOP design process?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*

7. **Write a programme to create an object of type batsman and calculate the average runs scored by the player.** *[RAKUB Programmer (PO) 12.10.2021 compact it 846-847 (ET: N/A)]*

## Encapsulation & Access Modifiers (6)

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

2. **Explain the various types of access specifiers.** *[DESCO Assistant Engineer 20.05.2023 compact it 579 (ET: DESCO)]*

3. **Which type of variable violates encapsulation rules?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

4. **Which members of base class cannot access to derived class?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

5. **What are the various Access Specification in C++? Explain their purpose with are example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*

6. **How many specifiers are used in C++ programing?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

## Constructors & Destructors (5)

1. **What is constructor function? Write the properties of it.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

2. **Define copy constructor. What Static binding and Dynamic binding?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

3. **What is the constructor invoked in OOP?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

4. **What is constructor?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

5. **(b) Why are constructor and destructor functions used in object oriented programming? Give examples of each function in C++ or java language.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

## Output Tracing & Recursion (3)

1. Consider the following Java program and determine the integer value printed by the execution of the main() method:
```java
class Test {
    static int x = 5;
    public static int fun(int n) {
        if (n <= 1) {
            return 1;
        }
        x = x + 2;
        return fun(n - 1) + x;
    }

    public static void main(String[] args) {
        System.out.println(fun(3));
    }
}
```
[SO IT 25-07-2026]

2. **(খ) কোন object-oriented programming language ব্যবহার করে একটি program লিখুন, যা recursive function ব্যবহার করে Fibonacci series প্রদান করবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **6.13 Consider the following Java program and determine the integer value printed by the execution of the main() method:** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*
```java
class Test {
    static int x = 5;
    public static int fun(int n) {
        if (n <= 1) {
            return 1;
        }
        x = x + 2;
        return fun(n - 1) + x;
    }
    public static void main(String[] args) {
        System.out.println(fun(3));
    }
}
```

## Exception Handling (3)

1. **(b) What is exception? Explain how it can be used for debugging a program.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

2. **What is difference between exception and error in Java?** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*

3. **What is exception handling? Write with an example.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

## C++ OOP Concepts & Friend Functions (2)

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1355 (ET: N/A)]*
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```

2. **(ক) Friend Function কী? উহার সুবিধা অসুবিধাগুলো লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

## Interfaces & Abstract Classes (2)

1. **Class/Interface implementation of code?** *[BCIC Assistant Programmer 14.02.2025 compact it 1329 (ET: BUET)]*

2. **An Abstract class Player with two sub classes Bowler and Batsman, Abstract class has one abstract method average, also have constructor and a string function that display name bowler or batsman. Batsman class implement abstract function average and display result, Batsman class have run and number match data. Now write a Java Program and show Batsman average run.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*
