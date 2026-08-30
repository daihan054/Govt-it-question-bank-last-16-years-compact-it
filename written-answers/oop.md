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

   - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

   - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

   - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

   - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

   - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

   - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

   - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

   - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

        - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

        - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

        - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

        - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
27. **Write down the properties/function of OOP?** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

    Two supporting concepts often listed with them:
    - Class: a blueprint or template that defines the data members and the member functions of a category of objects.
    - Object: an instance of a class, occupying memory and holding its own values for the data members.

    Also frequently mentioned: message passing (objects communicate by calling one another's methods) and dynamic binding (the method actually called is decided at run time).
28. **Write down the main feature of Object Oriented Programming (OOP).** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*


    Answer: The four principles (pillars) of OOP:

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

        - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

        - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

        - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

        - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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

    - Encapsulation: bundling the data, that is the attributes, and the methods that work on that data, into one unit called a class. It stops outside code from touching the parts directly, so nothing can be misused by accident. Data members are declared private and reached only through public methods. Example: a Car class keeps `speed` and `fuelLevel` private, and lets us change them only through `accelerate()`, `brake()` and `refuel()`. This keeps the data valid and lets us change the inside later without breaking anything outside.

    - Abstraction: hiding the complex inner details and showing only the essential features. We work with what an object does, not with how it does it. A driver uses the steering wheel and the pedals without knowing how the engine works. In code we do it with abstract classes and interfaces. Example: an Animal class holds the general properties of all animals, and the subclasses Dog and Cat write their own `makeSound()`.

    - Inheritance: a new class takes the properties and the behaviour of an existing class. The new one is the child or derived class, and the old one is the parent or base class. It expresses an "is-a" relationship and removes duplicate code. Example: a Vehicle parent class holds `make` and `model`. The child classes Car and Bike inherit those, and add their own, such as `num_doors` and `type_bike`. Types: single, multilevel, hierarchical, multiple and hybrid inheritance.

    - Polymorphism: objects of different classes can be treated as objects of one common parent class. One interface then stands for several different types. The word means "many forms". Example: Dog and Cat both inherit from Animal, and each writes `makeSound()` differently. A function that takes an Animal works with either one, without knowing which it got. It appears as compile-time polymorphism, through method overloading and operator overloading, and as run-time polymorphism, through method overriding and virtual functions.

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


   Answer: A method that returns a value must declare a return type other than void, and every path through it must end in a return statement of that type.

   ```java
   public class Calculator {

       // returns an int
       public int add(int a, int b) {
           return a + b;
       }

       // returns a double
       public double average(int[] numbers) {
           if (numbers == null || numbers.length == 0) {
               return 0.0;
           }
           int sum = 0;
           for (int n : numbers) {
               sum += n;
           }
           return (double) sum / numbers.length;
       }

       // returns a boolean
       public boolean isPrime(int n) {
           if (n < 2) return false;
           for (int i = 2; i * i <= n; i++) {
               if (n % i == 0) return false;
           }
           return true;
       }

       // returns a String
       public String grade(double marks) {
           if (marks >= 80) return "A+";
           else if (marks >= 70) return "A";
           else if (marks >= 60) return "A-";
           else if (marks >= 50) return "B";
           else if (marks >= 40) return "C";
           else return "F";
       }

       // returns an object
       public int[] sortAscending(int[] arr) {
           int[] copy = arr.clone();
           java.util.Arrays.sort(copy);
           return copy;
       }

       public static void main(String[] args) {
           Calculator c = new Calculator();

           int sum = c.add(15, 25);
           System.out.println("Sum: " + sum);

           int[] marks = {75, 82, 66, 91, 58};
           System.out.println("Average: " + c.average(marks));

           System.out.println("Is 17 prime? " + c.isPrime(17));
           System.out.println("Grade for 82 marks: " + c.grade(82));

           int[] sorted = c.sortAscending(marks);
           System.out.print("Sorted: ");
           for (int m : sorted) System.out.print(m + " ");
           System.out.println();
       }
   }
   ```

   Output:
   ```
   Sum: 40
   Average: 74.4
   Is 17 prime? true
   Grade for 82 marks: A+
   Sorted: 58 66 75 82 91
   ```

   Rules to remember:
   - The return type is written before the method name, for example public int add(...).
   - A method declared void must not return a value; a method with any other return type must return one on every path, or the code will not compile.
   - The returned value may be a primitive, an object, an array or null (for reference types).
   - A return statement immediately ends the method, so any code after it in the same block is unreachable and will not compile.
   - Java allows only one value to be returned. To return several, use an array, a collection or a small class that holds them.
2. **Write a Java Code....** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*


   Answer: A representative Java program that shows the main features of the language, namely a class, objects, encapsulation, a constructor, methods, an array and a loop.

   ```java
   import java.util.Scanner;

   class Student {
       // private data members: encapsulation
       private String name;
       private int roll;
       private double[] marks;

       // constructor
       public Student(String name, int roll, double[] marks) {
           this.name = name;
           this.roll = roll;
           this.marks = marks;
       }

       // method that returns a value
       public double getTotal() {
           double total = 0;
           for (double m : marks) {
               total += m;
           }
           return total;
       }

       public double getAverage() {
           return marks.length == 0 ? 0 : getTotal() / marks.length;
       }

       public String getGrade() {
           double avg = getAverage();
           if (avg >= 80) return "A+";
           else if (avg >= 70) return "A";
           else if (avg >= 60) return "A-";
           else if (avg >= 50) return "B";
           else if (avg >= 40) return "C";
           else return "F";
       }

       public void display() {
           System.out.printf("%-15s %-8d %-10.2f %-10.2f %s%n",
                   name, roll, getTotal(), getAverage(), getGrade());
       }
   }

   public class StudentDemo {
       public static void main(String[] args) {
           Student[] students = {
               new Student("Rahim Uddin",  101, new double[]{85, 78, 92, 88}),
               new Student("Karim Ahmed",  102, new double[]{65, 70, 58, 72}),
               new Student("Salma Begum",  103, new double[]{45, 52, 38, 60})
           };

           System.out.printf("%-15s %-8s %-10s %-10s %s%n",
                   "Name", "Roll", "Total", "Average", "Grade");
           System.out.println("--------------------------------------------------------");

           for (Student s : students) {
               s.display();
           }
       }
   }
   ```

   Output:
   ```
   Name            Roll     Total      Average    Grade
   --------------------------------------------------------
   Rahim Uddin     101      343.00     85.75      A+
   Karim Ahmed     102      265.00     66.25      A-
   Salma Begum     103      195.00     48.75      C
   ```

   Features demonstrated:
   - Class and object: Student is the blueprint, and three objects are created from it.
   - Encapsulation: the fields are private and are reached only through public methods.
   - Constructor: it initialises each object at the moment of creation.
   - Methods with return values: getTotal(), getAverage() and getGrade().
   - Arrays: an array of marks inside each object, and an array of objects in main.
   - The enhanced for loop, and formatted output with printf.
3. **What does run Finalization do?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: runFinalization() is a method of the java.lang.System and java.lang.Runtime classes. Calling it suggests to the Java Virtual Machine that it should run the finalize() methods of any objects that have been found to be unreachable but whose finalizers have not yet been executed.

   Signatures:
   ```java
   public static void System.runFinalization()
   public void Runtime.getRuntime().runFinalization()
   ```

   What it does:
   - The garbage collector identifies objects that are no longer reachable and queues them for finalization. Their finalize() methods are then run by a separate finalizer thread, but the JVM gives no guarantee about when.
   - runFinalization() asks the JVM to make a best effort to run those pending finalizers immediately, so that resources held by discarded objects are released sooner.

   Important limitations:
   - It is only a request, not a command. The JVM may ignore it entirely, exactly as it may ignore System.gc().
   - It does not itself collect garbage; it only runs finalizers for objects already found unreachable. To increase the chance of anything happening, System.gc() is normally called first.
   - There is no guarantee that any particular object's finalize() will run, or that it will run before the program exits.

   ```java
   class Resource {
       private String name;
       Resource(String name) { this.name = name; }

       @Override
       protected void finalize() throws Throwable {
           System.out.println("Finalizing: " + name);
           super.finalize();
       }
   }

   public class FinalizationDemo {
       public static void main(String[] args) {
           Resource r = new Resource("File handle");
           r = null;                 // the object is now unreachable

           System.gc();              // suggest garbage collection
           System.runFinalization(); // suggest running pending finalizers

           System.out.println("End of main");
       }
   }
   ```

   Why it should not be used in modern code:
   - finalize() was deprecated in Java 9 and removed from the language in Java 18, because it is unpredictable, it can resurrect objects, it delays garbage collection, and an exception thrown inside it is silently ignored.
   - The correct modern practice is deterministic resource management: implement AutoCloseable and use a try-with-resources block, or use java.lang.ref.Cleaner for a safety net.

   ```java
   class Resource implements AutoCloseable {
       @Override
       public void close() {
           System.out.println("Resource released deterministically");
       }
   }

   public class ModernDemo {
       public static void main(String[] args) {
           try (Resource r = new Resource()) {
               System.out.println("Using the resource");
           }   // close() is called automatically here, guaranteed
       }
   }
   ```

   In one sentence: runFinalization() requests the JVM to run pending finalizers of unreachable objects, but it guarantees nothing, and the entire finalization mechanism is now obsolete.
4. **What syntax is used for calling static methods in class?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: A static method belongs to the class itself rather than to any object of the class, so it is called using the class name followed by the dot operator.

   Syntax:
   ```
   ClassName.methodName(arguments);
   ```

   Example:

   ```java
   class MathUtil {
       // static method: belongs to the class
       public static int square(int n) {
           return n * n;
       }

       public static double circleArea(double r) {
           return Math.PI * r * r;
       }

       // instance method: belongs to an object
       public int cube(int n) {
           return n * n * n;
       }
   }

   public class StaticCallDemo {
       public static void main(String[] args) {
           // calling a static method with the class name
           System.out.println(MathUtil.square(5));          // 25
           System.out.println(MathUtil.circleArea(3));      // 28.27...

           // calling an instance method requires an object
           MathUtil m = new MathUtil();
           System.out.println(m.cube(3));                   // 27
       }
   }
   ```

   Points to note:
   - No object is needed. MathUtil.square(5) works without ever writing new MathUtil().
   - Calling it through an object reference, as in m.square(5), is legal but is bad practice; the compiler issues a warning because it hides the fact that the method is static.
   - Inside the same class the class name may be omitted, so square(5) is enough.
   - Well-known examples from the standard library: Math.sqrt(), Math.max(), Integer.parseInt(), String.valueOf(), Arrays.sort() and System.out.println(), where out is a static field of System.

   Rules for static methods:
   - They cannot use the keywords this or super, because there is no object.
   - They cannot access instance variables or call instance methods directly; they can only use static members, or work through an object passed to them.
   - They cannot be overridden, only hidden. If a subclass declares a static method with the same signature, the version called is decided at compile time from the reference type.
   - main() is declared static precisely so that the JVM can call it before any object exists.

   Static variables follow the same rule: ClassName.variableName.
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


   Answer: The two classes are analysed method by method. (The code as printed has capitalisation errors such as "Public" and "class A"; in correct Java the keywords are lower case and the classes would be A and B.)

   Class A declares:
   - public void m1()
   - public void m2(int i)
   - public void m3(int i)
   - public static void m4(int i)

   Class B extends A and declares:
   - public static void m1(int i)
   - public void m2(int i)
   - public void m3(String s)
   - public static void m4(int i)

   Classification:

   | Method in B | Relationship to A | Reason |
   |---|---|---|
   | public static void m1(int i) | Overloads A.m1() | The name is the same but the parameter list differs: A.m1() takes no argument, B.m1(int) takes one. Different signature means overloading, not overriding. Class B therefore has two usable methods named m1: the inherited m1() and its own m1(int). |
   | public void m2(int i) | Overrides A.m2(int) | The name, the parameter list and the return type are all identical, and both are instance methods. This is true overriding, so the call is resolved at run time. |
   | public void m3(String s) | Overloads A.m3(int) | The parameter type differs, int against String, so the signatures differ. B therefore has both m3(int), inherited, and m3(String), its own. |
   | public static void m4(int i) | Hides A.m4(int) | The signatures are identical and both methods are static. Static methods are never overridden; the subclass version hides the superclass version. Which one runs is decided at compile time from the declared type of the reference, not from the object. |

   What about the remaining method:
   - A.m1() is not touched by anything in B, so it is simply inherited unchanged and remains available on a B object.
   - A.m3(int) is likewise inherited unchanged, and coexists with B's m3(String).

   Complete set of methods available on an object of class B:
   - m1() inherited from A
   - m1(int) declared in B
   - m2(int) the overriding version in B
   - m3(int) inherited from A
   - m3(String) declared in B
   - m4(int) the hiding version in B

   Demonstration of the difference between overriding and hiding:

   ```java
   A obj = new B();
   obj.m2(5);     // runs B's m2  -> overriding, resolved at run time by the object type
   A.m4(5);       // runs A's m4  -> hiding, resolved at compile time by the class name
   B.m4(5);       // runs B's m4
   ```

   Key distinctions to state in an answer:
   - Overloading: same name, different parameter list, resolved at compile time, no inheritance needed.
   - Overriding: same name and same parameter list, instance methods, resolved at run time, inheritance required.
   - Hiding: same name and same parameter list, but static methods, resolved at compile time from the reference type.
6. **অথবা, (ক) ‘Static’ কীওয়ার্ডটি ব্যাখ্যা করার জন্যে Static Variable এবং Static Method ব্যবহার করে একটি প্রোগ্রাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*


   Answer: static কীওয়ার্ডটি বোঝায় যে সংশ্লিষ্ট সদস্যটি কোনো নির্দিষ্ট অবজেক্টের নয়, বরং সম্পূর্ণ ক্লাসের।

   Static Variable (ক্লাস ভেরিয়েবল):
   - ক্লাসের সব অবজেক্ট এই একটিমাত্র কপি ভাগাভাগি করে ব্যবহার করে।
   - ক্লাস প্রথমবার লোড হওয়ার সময় একবারই মেমোরি বরাদ্দ হয়, অবজেক্ট তৈরির সময় নয়।
   - কোনো অবজেক্টে এর মান বদলালে সব অবজেক্টের জন্যই বদলে যায়।
   - ব্যবহার: গণনা রাখা, ধ্রুবক সংরক্ষণ, প্রতিষ্ঠানের নামের মতো সবার জন্য অভিন্ন তথ্য।

   Static Method (ক্লাস মেথড):
   - অবজেক্ট তৈরি না করেই ক্লাসের নাম দিয়ে ডাকা যায়।
   - কেবল static সদস্য সরাসরি ব্যবহার করতে পারে; instance ভেরিয়েবল বা this ব্যবহার করতে পারে না।
   - ব্যবহার: ইউটিলিটি ফাংশন এবং static ভেরিয়েবল নিয়ে কাজ করা।

   প্রোগ্রাম:

   ```java
   class Student {
       // static variable: সব অবজেক্টের জন্য একটিই কপি
       private static int studentCount = 0;
       private static String instituteName = "Dhaka College";

       // instance variable: প্রতিটি অবজেক্টের নিজস্ব কপি
       private String name;
       private int roll;

       public Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
           studentCount++;            // প্রতিবার অবজেক্ট তৈরিতে বাড়ে
       }

       // static method: অবজেক্ট ছাড়াই ডাকা যায়
       public static int getStudentCount() {
           return studentCount;       // static সদস্য ব্যবহার করা যায়
           // return name;            // ত্রুটি: instance ভেরিয়েবল ব্যবহার করা যায় না
       }

       public static void setInstituteName(String newName) {
           instituteName = newName;   // পরিবর্তন সব অবজেক্টে প্রতিফলিত হয়
       }

       // instance method
       public void display() {
           System.out.println(name + " (Roll " + roll + ") - " + instituteName);
       }
   }

   public class StaticDemo {
       public static void main(String[] args) {

           // কোনো অবজেক্ট তৈরির আগেই static মেথড ডাকা যাচ্ছে
           System.out.println("Initial count: " + Student.getStudentCount());   // 0

           Student s1 = new Student("Rahim", 101);
           Student s2 = new Student("Karim", 102);
           Student s3 = new Student("Salma", 103);

           System.out.println("Total students: " + Student.getStudentCount()); // 3

           s1.display();
           s2.display();
           s3.display();

           // static ভেরিয়েবল বদলালে সব অবজেক্টে প্রভাব পড়ে
           Student.setInstituteName("Notre Dame College");
           System.out.println("--- After changing the institute name ---");
           s1.display();
           s2.display();
           s3.display();
       }
   }
   ```

   আউটপুট:
   ```
   Initial count: 0
   Total students: 3
   Rahim (Roll 101) - Dhaka College
   Karim (Roll 102) - Dhaka College
   Salma (Roll 103) - Dhaka College
   --- After changing the institute name ---
   Rahim (Roll 101) - Notre Dame College
   Karim (Roll 102) - Notre Dame College
   Salma (Roll 103) - Notre Dame College
   ```

   ব্যাখ্যা:
   - studentCount একটি static ভেরিয়েবল, তাই তিনটি অবজেক্ট মিলে একটিমাত্র কপি ব্যবহার করেছে এবং গণনা ৩ হয়েছে। এটি instance ভেরিয়েবল হলে প্রতিটি অবজেক্টে আলাদা কপি থাকত এবং প্রতিটির মান হতো ১।
   - instituteName একবার বদলাতেই তিনটি অবজেক্টেই পরিবর্তন দেখা গেছে, কারণ কপি একটিই।
   - getStudentCount() একটি static মেথড, তাই কোনো অবজেক্ট তৈরির আগেই Student.getStudentCount() লিখে ডাকা গেছে।
   - static মেথডের ভেতরে name ব্যবহার করা যায় না, কারণ কোন অবজেক্টের name তা নির্ধারণ করার উপায় নেই।

   অতিরিক্ত তথ্য: static block ক্লাস লোড হওয়ার সময় একবারই চলে এবং static ভেরিয়েবল আরম্ভ করতে ব্যবহৃত হয়। main() মেথডটিও static, কারণ JVM কোনো অবজেক্ট তৈরির আগেই একে ডাকে।
7. **Write a java program to counting the vowel and consonant into a given strings.** *[BOF Assistant Programmer 2022 compact it 735 (ET: MIST)]*


   Answer: The program counts the vowels and the consonants in a string given by the user.

   ```java
   import java.util.Scanner;

   public class VowelConsonantCounter {

       public static void main(String[] args) {
           Scanner sc = new Scanner(System.in);
           System.out.print("Enter a string: ");
           String input = sc.nextLine();

           int vowels = 0, consonants = 0, digits = 0, spaces = 0, others = 0;

           // convert once, so that both cases are handled
           String str = input.toLowerCase();

           for (int i = 0; i < str.length(); i++) {
               char ch = str.charAt(i);

               if (ch >= 'a' && ch <= 'z') {                 // it is a letter
                   if (ch == 'a' || ch == 'e' || ch == 'i'
                           || ch == 'o' || ch == 'u') {
                       vowels++;
                   } else {
                       consonants++;
                   }
               } else if (ch >= '0' && ch <= '9') {
                   digits++;
               } else if (ch == ' ') {
                   spaces++;
               } else {
                   others++;
               }
           }

           System.out.println("Vowels      : " + vowels);
           System.out.println("Consonants  : " + consonants);
           System.out.println("Digits      : " + digits);
           System.out.println("Spaces      : " + spaces);
           System.out.println("Other chars : " + others);

           sc.close();
       }
   }
   ```

   Sample run:
   ```
   Enter a string: Bangladesh is my country 2026
   Vowels      : 8
   Consonants  : 13
   Digits      : 4
   Spaces      : 4
   Other chars : 0
   ```

   Explanation:
   - The string is converted to lower case once with toLowerCase(), so that upper-case letters need not be tested separately.
   - charAt(i) reads each character in turn, and length() gives the number of characters.
   - A character is a letter if it lies between 'a' and 'z' after conversion. Among letters, the five vowels are tested first, and everything else is a consonant.
   - Digits, spaces and punctuation are counted separately, so they are not wrongly counted as consonants. This is the mistake most commonly made in this problem.

   Shorter version using a helper and the built-in Character class:

   ```java
   public class VowelCounterShort {
       public static void main(String[] args) {
           String str = "Bangladesh is my country";
           int v = 0, c = 0;
           for (char ch : str.toLowerCase().toCharArray()) {
               if (!Character.isLetter(ch)) continue;
               if ("aeiou".indexOf(ch) >= 0) v++;
               else c++;
           }
           System.out.println("Vowels: " + v + ", Consonants: " + c);
       }
   }
   ```

   Output:
   ```
   Vowels: 8, Consonants: 13
   ```
8. **Where will be the most chance of the grabage collector being invoked?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*


   Answer: The garbage collector is most likely to be invoked when the Java Virtual Machine is running short of free memory in the heap, in particular when an allocation request cannot be satisfied from the free space available.

   The situations in which it is most likely to run:

   - When the heap is nearly full and a new object must be allocated. This is by far the commonest trigger. If the young generation (the Eden space) fills, a minor collection runs; if the old generation fills, a major or full collection runs.
   - When many objects have just become unreachable, for example after a large data structure goes out of scope or a large collection is cleared, so there is a great deal of garbage to reclaim.
   - When a method that created many short-lived objects returns, since all of its local objects become unreachable at once. Most objects die young, which is the assumption behind generational collection.
   - When a reference is explicitly set to null and no other reference to the object remains.
   - When System.gc() or Runtime.getRuntime().gc() is called. This is only a request; the JVM is free to ignore it, and calling it in production code is discouraged because it can force an expensive full collection at a bad moment.
   - Just before an OutOfMemoryError is thrown. The JVM performs a full collection as a last attempt to find memory before giving up.
   - When the application is idle. Some collectors take the opportunity to run when the application threads are not busy.

   When an object becomes eligible for collection:
   - The reference is set to null: obj = null;
   - The reference is reassigned to another object.
   - The object was created inside a method and that method has returned.
   - Island of isolation: two or more objects refer to one another but nothing outside refers to any of them, so the whole group is unreachable.

   Important points to state in an answer:
   - Garbage collection in Java is automatic and non-deterministic. The programmer cannot force it or predict exactly when it will happen.
   - It reclaims heap memory only. Native resources such as file handles, sockets and database connections are not released by it, which is why they must be closed explicitly, ideally with try-with-resources.
   - Memory leaks are still possible in Java, whenever an unwanted object remains reachable, for example an entry left in a static collection or a listener that is never removed.

   Example:

   ```java
   public class GCDemo {
       public static void main(String[] args) {
           String s1 = new String("Hello");
           s1 = null;                 // the "Hello" object is now unreachable

           for (int i = 0; i < 100000; i++) {
               new StringBuilder("temp" + i);   // each becomes garbage immediately
           }
           // the heap fills rapidly here, so the collector is very likely to run

           System.gc();               // a request only, not a guarantee
       }
   }
   ```
9. **In Java program. Write the method in given box for the Electric bill calculation if unit is less then 100 then unit rate 4.0 take and after 100-unit rate is 5.50 and reaming unit rate is 6.00. [Bill rate 4.0 if unit<=100, Bill rate 5.50 if (unit>100 && unit<=200), Bill rate 6.00 for remaining units.]** *[BPDB Assistant Engineer (CSE) 2021 compact it 816-817 (ET: BUET)]*


   Answer: The bill is calculated in slabs: the first 100 units are charged at Tk 4.00, the units from 101 to 200 at Tk 5.50, and every unit beyond 200 at Tk 6.00.

   ```java
   import java.util.Scanner;

   class ElectricityBill {
       private String consumerName;
       private String meterNo;
       private int unitsConsumed;

       public ElectricityBill(String name, String meterNo, int units) {
           this.consumerName = name;
           this.meterNo = meterNo;
           this.unitsConsumed = units;
       }

       // the required method
       public double calculateBill() {
           double bill = 0;

           if (unitsConsumed <= 100) {
               bill = unitsConsumed * 4.00;
           } else if (unitsConsumed <= 200) {
               bill = (100 * 4.00) + ((unitsConsumed - 100) * 5.50);
           } else {
               bill = (100 * 4.00) + (100 * 5.50) + ((unitsConsumed - 200) * 6.00);
           }
           return bill;
       }

       public void display() {
           double bill = calculateBill();
           double vat = bill * 0.05;          // 5 per cent VAT
           System.out.println("=====================================");
           System.out.println("Consumer : " + consumerName);
           System.out.println("Meter No : " + meterNo);
           System.out.println("Units    : " + unitsConsumed);
           System.out.printf("Bill     : Tk %.2f%n", bill);
           System.out.printf("VAT (5%%) : Tk %.2f%n", vat);
           System.out.printf("Total    : Tk %.2f%n", bill + vat);
           System.out.println("=====================================");
       }
   }

   public class BillDemo {
       public static void main(String[] args) {
           ElectricityBill[] bills = {
               new ElectricityBill("Rahim Uddin",  "M-1001", 80),
               new ElectricityBill("Karim Ahmed",  "M-1002", 150),
               new ElectricityBill("Salma Begum",  "M-1003", 350)
           };

           for (ElectricityBill b : bills) {
               b.display();
           }
       }
   }
   ```

   Worked calculations:
   - 80 units: 80 x 4.00 = Tk 320.00
   - 150 units: (100 x 4.00) + (50 x 5.50) = 400 + 275 = Tk 675.00
   - 350 units: (100 x 4.00) + (100 x 5.50) + (150 x 6.00) = 400 + 550 + 900 = Tk 1850.00

   Output:
   ```
   =====================================
   Consumer : Rahim Uddin
   Meter No : M-1001
   Units    : 80
   Bill     : Tk 320.00
   VAT (5%) : Tk 16.00
   Total    : Tk 336.00
   =====================================
   Consumer : Karim Ahmed
   Meter No : M-1002
   Units    : 150
   Bill     : Tk 675.00
   VAT (5%) : Tk 33.75
   Total    : Tk 708.75
   =====================================
   Consumer : Salma Begum
   Meter No : M-1003
   Units    : 350
   Bill     : Tk 1850.00
   VAT (5%) : Tk 92.50
   Total    : Tk 1942.50
   =====================================
   ```

   Point to note: the rates are applied slab by slab, not to the whole consumption. A consumer using 150 units is not charged 150 x 5.50; the first 100 units remain at the lower rate. Applying the higher rate to the entire consumption is the commonest error in this problem, and it also produces an unfair jump in the bill at the slab boundary.
10. **C# language এর একটি প্রোগ্রাম লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*


    Answer: নিচে C# ভাষায় একটি প্রোগ্রাম দেওয়া হলো, যা ক্লাস, অবজেক্ট, এনক্যাপসুলেশন, প্রপার্টি, কনস্ট্রাক্টর, ইনহেরিটেন্স ও পলিমরফিজম দেখায়।

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace BankSystem
    {
        // বেস ক্লাস
        class Account
        {
            // প্রাইভেট ফিল্ড: এনক্যাপসুলেশন
            private double balance;

            // প্রপার্টি: C# এর নিজস্ব গেটার-সেটার পদ্ধতি
            public string HolderName { get; set; }
            public string AccountNo  { get; set; }

            public double Balance
            {
                get { return balance; }
                private set { balance = value; }    // বাইরে থেকে লেখা যাবে না
            }

            // কনস্ট্রাক্টর
            public Account(string name, string accNo, double initial)
            {
                HolderName = name;
                AccountNo  = accNo;
                Balance    = initial >= 0 ? initial : 0;
            }

            public void Deposit(double amount)
            {
                if (amount <= 0)
                {
                    Console.WriteLine("Deposit amount must be positive.");
                    return;
                }
                Balance += amount;
                Console.WriteLine($"Deposited Tk {amount}. Balance: Tk {Balance}");
            }

            // ভার্চুয়াল মেথড: সাবক্লাস ওভাররাইড করতে পারবে
            public virtual void Withdraw(double amount)
            {
                if (amount <= 0)
                    Console.WriteLine("Invalid amount.");
                else if (amount > Balance)
                    Console.WriteLine("Insufficient balance.");
                else
                {
                    Balance -= amount;
                    Console.WriteLine($"Withdrew Tk {amount}. Balance: Tk {Balance}");
                }
            }

            public virtual string AccountType() => "General Account";

            public void Display()
            {
                Console.WriteLine("-------------------------------------");
                Console.WriteLine($"Type    : {AccountType()}");
                Console.WriteLine($"Holder  : {HolderName}");
                Console.WriteLine($"Acc No  : {AccountNo}");
                Console.WriteLine($"Balance : Tk {Balance:F2}");
            }
        }

        // ডেরাইভড ক্লাস
        class SavingsAccount : Account
        {
            private const double MinimumBalance = 500;
            public double InterestRate { get; set; }

            public SavingsAccount(string name, string accNo, double initial, double rate)
                : base(name, accNo, initial)
            {
                InterestRate = rate;
            }

            public override void Withdraw(double amount)
            {
                if (Balance - amount < MinimumBalance)
                    Console.WriteLine($"Cannot withdraw. Minimum balance Tk {MinimumBalance} required.");
                else
                    base.Withdraw(amount);
            }

            public override string AccountType() => "Savings Account";
        }

        class Program
        {
            static void Main(string[] args)
            {
                List<Account> accounts = new List<Account>
                {
                    new Account("Rahim Uddin", "GA-1001", 10000),
                    new SavingsAccount("Karim Ahmed", "SB-2001", 8000, 5.0)
                };

                foreach (Account acc in accounts)
                {
                    acc.Display();
                    acc.Deposit(2000);
                    acc.Withdraw(9500);      // প্রতিটি নিজের নিয়ম প্রয়োগ করবে
                    Console.WriteLine();
                }
            }
        }
    }
    ```

    আউটপুট:
    ```
    -------------------------------------
    Type    : General Account
    Holder  : Rahim Uddin
    Acc No  : GA-1001
    Balance : Tk 10000.00
    Deposited Tk 2000. Balance: Tk 12000
    Withdrew Tk 9500. Balance: Tk 2500

    -------------------------------------
    Type    : Savings Account
    Holder  : Karim Ahmed
    Acc No  : SB-2001
    Balance : Tk 8000.00
    Deposited Tk 2000. Balance: Tk 10000
    Cannot withdraw. Minimum balance Tk 500 required.
    ```

    C# এর কয়েকটি নিজস্ব বৈশিষ্ট্য, যা এই প্রোগ্রামে দেখা যাচ্ছে:
    - Property: get ও set ব্যবহার করে সংক্ষেপে গেটার-সেটার লেখা যায়; জাভার মতো আলাদা মেথড লিখতে হয় না।
    - String interpolation: $"..." লিখে সরাসরি ভেরিয়েবল বসানো যায়।
    - virtual ও override কীওয়ার্ড: জাভার বিপরীতে C# এ ওভাররাইড করতে হলে বেস মেথডকে স্পষ্টভাবে virtual ঘোষণা করতে হয় এবং সাবক্লাসে override লিখতে হয়।
    - Expression-bodied member: => চিহ্ন দিয়ে এক লাইনের মেথড লেখা যায়।
    - base কীওয়ার্ড: জাভার super এর সমতুল্য।
    - namespace: কোড সংগঠিত রাখার জন্য।
11. **Write java program for calculate electricity bill using class and object.** *[Sundharban Gas Assistant Programmer 2020 compact it 1047-1048 (ET: N/A)]*


    Answer: The bill is calculated in slabs: the first 100 units are charged at Tk 4.00, the units from 101 to 200 at Tk 5.50, and every unit beyond 200 at Tk 6.00.

    ```java
    import java.util.Scanner;

    class ElectricityBill {
        private String consumerName;
        private String meterNo;
        private int unitsConsumed;

        public ElectricityBill(String name, String meterNo, int units) {
            this.consumerName = name;
            this.meterNo = meterNo;
            this.unitsConsumed = units;
        }

        // the required method
        public double calculateBill() {
            double bill = 0;

            if (unitsConsumed <= 100) {
                bill = unitsConsumed * 4.00;
            } else if (unitsConsumed <= 200) {
                bill = (100 * 4.00) + ((unitsConsumed - 100) * 5.50);
            } else {
                bill = (100 * 4.00) + (100 * 5.50) + ((unitsConsumed - 200) * 6.00);
            }
            return bill;
        }

        public void display() {
            double bill = calculateBill();
            double vat = bill * 0.05;          // 5 per cent VAT
            System.out.println("=====================================");
            System.out.println("Consumer : " + consumerName);
            System.out.println("Meter No : " + meterNo);
            System.out.println("Units    : " + unitsConsumed);
            System.out.printf("Bill     : Tk %.2f%n", bill);
            System.out.printf("VAT (5%%) : Tk %.2f%n", vat);
            System.out.printf("Total    : Tk %.2f%n", bill + vat);
            System.out.println("=====================================");
        }
    }

    public class BillDemo {
        public static void main(String[] args) {
            ElectricityBill[] bills = {
                new ElectricityBill("Rahim Uddin",  "M-1001", 80),
                new ElectricityBill("Karim Ahmed",  "M-1002", 150),
                new ElectricityBill("Salma Begum",  "M-1003", 350)
            };

            for (ElectricityBill b : bills) {
                b.display();
            }
        }
    }
    ```

    Worked calculations:
    - 80 units: 80 x 4.00 = Tk 320.00
    - 150 units: (100 x 4.00) + (50 x 5.50) = 400 + 275 = Tk 675.00
    - 350 units: (100 x 4.00) + (100 x 5.50) + (150 x 6.00) = 400 + 550 + 900 = Tk 1850.00

    Output:
    ```
    =====================================
    Consumer : Rahim Uddin
    Meter No : M-1001
    Units    : 80
    Bill     : Tk 320.00
    VAT (5%) : Tk 16.00
    Total    : Tk 336.00
    =====================================
    Consumer : Karim Ahmed
    Meter No : M-1002
    Units    : 150
    Bill     : Tk 675.00
    VAT (5%) : Tk 33.75
    Total    : Tk 708.75
    =====================================
    Consumer : Salma Begum
    Meter No : M-1003
    Units    : 350
    Bill     : Tk 1850.00
    VAT (5%) : Tk 92.50
    Total    : Tk 1942.50
    =====================================
    ```

    Point to note: the rates are applied slab by slab, not to the whole consumption. A consumer using 150 units is not charged 150 x 5.50; the first 100 units remain at the lower rate. Applying the higher rate to the entire consumption is the commonest error in this problem, and it also produces an unfair jump in the bill at the slab boundary.

## Class Design & Object-Oriented Modeling (7)

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 425 (ET: BIBM)]*


   Answer: Requirements for the Circle class:

   Data requirements (attributes):
   - centreX, centreY: the coordinates of the origin (centre) of the circle, of type double. They are needed because the circle must be translatable, and translation changes the position of the centre.
   - radius: the radius of the circle, of type double. It determines both the perimeter and the area.
   - PI: a constant, declared static and final, since it is the same for every circle.

   Method requirements (behaviour):
   - A constructor Circle(x, y, r) to create a circle at a given position with a given radius, with validation that the radius is not negative.
   - translate(dx, dy): move the circle by dx along the x axis and dy along the y axis. It changes only the centre, never the radius.
   - perimeter(): return 2 x PI x radius.
   - area(): return PI x radius x radius.
   - Getters and setters for the centre and the radius, so that the data can stay private (encapsulation).
   - display(): print the current state of the circle.

   Implementation:

   ```java
   class Circle {
       private static final double PI = 3.14159265358979;

       private double centreX;      // origin
       private double centreY;
       private double radius;

       public Circle(double x, double y, double r) {
           this.centreX = x;
           this.centreY = y;
           setRadius(r);
       }

       public void setRadius(double r) {
           if (r < 0) {
               System.out.println("Radius cannot be negative. Set to 0.");
               this.radius = 0;
           } else {
               this.radius = r;
           }
       }

       public double getRadius()  { return radius; }
       public double getCentreX() { return centreX; }
       public double getCentreY() { return centreY; }

       // translation: shift the circle by (dx, dy)
       public void translate(double dx, double dy) {
           this.centreX = this.centreX + dx;
           this.centreY = this.centreY + dy;
       }

       public double perimeter() {
           return 2 * PI * radius;
       }

       public double area() {
           return PI * radius * radius;
       }

       public void display() {
           System.out.printf("Centre (%.1f, %.1f), Radius %.1f, Perimeter %.2f, Area %.2f%n",
                   centreX, centreY, radius, perimeter(), area());
       }
   }

   public class GraphicsDemo {
       public static void main(String[] args) {
           Circle c = new Circle(0, 0, 5);
           c.display();

           c.translate(3, 4);       // move 3 right and 4 up
           c.display();

           c.translate(-1, 2);
           c.display();
       }
   }
   ```

   Output:
   ```
   Centre (0.0, 0.0), Radius 5.0, Perimeter 31.42, Area 78.54
   Centre (3.0, 4.0), Radius 5.0, Perimeter 31.42, Area 78.54
   Centre (2.0, 6.0), Radius 5.0, Perimeter 31.42, Area 78.54
   ```

   Note that translation changes the position but leaves the perimeter and the area unchanged, which is exactly what a rigid translation should do.

   Data flow of the translate method:

   ```mermaid
   flowchart LR
     IN[Input: dx, dy] --> CHK[Read current centreX and centreY]
     CHK --> CALC[Compute newX = centreX + dx and newY = centreY + dy]
     CALC --> UPD[Assign newX to centreX and newY to centreY]
     UPD --> OUT[Circle now positioned at the new centre]
   ```

   Step-by-step description of the data flow:
   - Input: the translation vector (dx, dy) enters the method as parameters.
   - Read: the current values of centreX and centreY are read from the object's state.
   - Compute: newX = centreX + dx and newY = centreY + dy.
   - Update: the computed values are written back into centreX and centreY.
   - Output: the object's state now describes the translated circle. Nothing is returned, and radius is not touched, so area() and perimeter() give the same results as before.

   Design points worth stating:
   - The radius is deliberately not involved in translation, because translation is a rigid motion; scaling would be a separate method.
   - The data members are private, so the only way to move the circle is through translate(), which guarantees that both coordinates are updated together and the object cannot be left in a half-moved state.
   - If the graphics package later needs rotation or scaling, they are added as new methods without disturbing the existing ones.
2. **What are the built in classes?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*


   Answer: Built-in classes are the ready-made classes supplied with the programming language in its standard library, so that a programmer need not write common functionality from scratch. They are also called predefined or library classes.

   Important built-in classes in Java, grouped by package:

   java.lang (imported automatically):
   - Object: the root of every class hierarchy in Java; every class inherits from it.
   - String: an immutable sequence of characters.
   - StringBuilder and StringBuffer: mutable strings, the second being thread-safe.
   - Math: static methods such as sqrt(), pow(), abs(), max(), min(), round() and random().
   - System: standard input, output and error streams, plus utility methods such as currentTimeMillis() and exit().
   - The wrapper classes Integer, Double, Float, Long, Short, Byte, Character and Boolean, which wrap primitive values as objects and provide conversion methods such as parseInt().
   - Thread: for concurrent execution.
   - Exception, RuntimeException and Throwable: the exception hierarchy.

   java.util:
   - Scanner: reads input from the keyboard or a file.
   - ArrayList, LinkedList, Vector: dynamic lists.
   - HashMap, TreeMap, LinkedHashMap: key-value collections.
   - HashSet, TreeSet: collections of unique elements.
   - Arrays: static methods such as sort(), binarySearch() and toString().
   - Collections: static methods for lists and sets.
   - Date, Calendar, and the modern LocalDate, LocalTime and LocalDateTime.
   - Random: random number generation.

   java.io and java.nio.file:
   - File, FileReader, FileWriter, BufferedReader, BufferedWriter, InputStreamReader, Files, Paths.

   java.sql:
   - Connection, Statement, PreparedStatement, ResultSet, DriverManager, for database access.

   java.net:
   - Socket, ServerSocket, URL, HttpURLConnection.

   javax.swing and java.awt:
   - JFrame, JButton, JLabel, JTextField and the rest of the graphical user interface toolkit.

   Example of using several built-in classes together:

   ```java
   import java.util.Scanner;
   import java.util.ArrayList;
   import java.util.Collections;

   public class BuiltInDemo {
       public static void main(String[] args) {
           Scanner sc = new Scanner(System.in);       // java.util.Scanner
           ArrayList<Integer> list = new ArrayList<>();  // java.util.ArrayList

           System.out.print("How many numbers? ");
           int n = sc.nextInt();

           for (int i = 0; i < n; i++) {
               list.add(sc.nextInt());
           }

           Collections.sort(list);                    // java.util.Collections
           System.out.println("Sorted: " + list);
           System.out.println("Maximum: " + Collections.max(list));
           System.out.println("Square root of the maximum: "
                   + Math.sqrt(Collections.max(list)));   // java.lang.Math

           String s = list.toString().toUpperCase();  // java.lang.String
           System.out.println(s);

           sc.close();
       }
   }
   ```

   Advantages of built-in classes:
   - They save development time, since common tasks are already solved.
   - They are thoroughly tested, optimised and reliable.
   - They are standard, so any Java programmer recognises them, which makes code portable and readable.
   - They are documented and maintained by the language vendor.

   The equivalent in C++ is the Standard Template Library, with classes such as string, vector, map, set and the iostream family.
3. **অথবা, (ক) উদাহরণসহ Class এবং Object এর মধ্যে পার্থক্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*


   Answer: | Point | Class | Object |
   |---|---|---|
   | Definition | A blueprint or template that describes the data members and member functions of a category of things | An actual instance of a class, created from that blueprint |
   | Nature | A logical entity; it is a description only | A physical entity; it exists in memory |
   | Memory | No memory is allocated when a class is declared | Memory is allocated when an object is created |
   | How many | Declared once | Many objects can be created from one class |
   | Creation | With the keyword class | With the keyword new in Java, or by declaring a variable of the class type in C++ |
   | Contains | Declarations of members | Actual values for those members |
   | Analogy | The architect's plan of a house | The houses actually built from that plan |
   | Example | class Student { ... } | Student s1 = new Student(); |

   Example:

   ```java
   class Student {                    // class: the blueprint
       String name;                   // data member
       int roll;
       double cgpa;

       void display() {               // member function
           System.out.println(name + " | Roll: " + roll + " | CGPA: " + cgpa);
       }
   }

   public class Demo {
       public static void main(String[] args) {
           Student s1 = new Student();     // object 1
           s1.name = "Rahim";
           s1.roll = 101;
           s1.cgpa = 3.75;

           Student s2 = new Student();     // object 2
           s2.name = "Karim";
           s2.roll = 102;
           s2.cgpa = 3.50;

           s1.display();
           s2.display();
       }
   }
   ```

   Output:
   ```
   Rahim | Roll: 101 | CGPA: 3.75
   Karim | Roll: 102 | CGPA: 3.5
   ```

   The class Student was written once, but two independent objects were created from it, each with its own copy of the data members.
4. **(খ) উদাহরণসহ ক্লাস এবং অবজেক্ট এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


   Answer: | Point | Class | Object |
   |---|---|---|
   | Definition | A blueprint or template that describes the data members and member functions of a category of things | An actual instance of a class, created from that blueprint |
   | Nature | A logical entity; it is a description only | A physical entity; it exists in memory |
   | Memory | No memory is allocated when a class is declared | Memory is allocated when an object is created |
   | How many | Declared once | Many objects can be created from one class |
   | Creation | With the keyword class | With the keyword new in Java, or by declaring a variable of the class type in C++ |
   | Contains | Declarations of members | Actual values for those members |
   | Analogy | The architect's plan of a house | The houses actually built from that plan |
   | Example | class Student { ... } | Student s1 = new Student(); |

   Example:

   ```java
   class Student {                    // class: the blueprint
       String name;                   // data member
       int roll;
       double cgpa;

       void display() {               // member function
           System.out.println(name + " | Roll: " + roll + " | CGPA: " + cgpa);
       }
   }

   public class Demo {
       public static void main(String[] args) {
           Student s1 = new Student();     // object 1
           s1.name = "Rahim";
           s1.roll = 101;
           s1.cgpa = 3.75;

           Student s2 = new Student();     // object 2
           s2.name = "Karim";
           s2.roll = 102;
           s2.cgpa = 3.50;

           s1.display();
           s2.display();
       }
   }
   ```

   Output:
   ```
   Rahim | Roll: 101 | CGPA: 3.75
   Karim | Roll: 102 | CGPA: 3.5
   ```

   The class Student was written once, but two independent objects were created from it, each with its own copy of the data members.
5. **Define Class and Object in C++ with example.** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*


   Answer: Class: a class is a user-defined data type that serves as a blueprint for objects. It groups together data members (variables) and member functions (methods) that operate on those data. Declaring a class allocates no memory; it only describes what an object of that type will contain.

      Object: an object is an instance of a class. It occupies memory and holds its own values for the data members. Many objects can be created from one class, and each has its own independent state.

      Example in C++:

      ```cpp
      #include <iostream>
      #include <string>
      using namespace std;

      class Student {                       // class definition: the blueprint
      private:                              // access specifier: encapsulation
          string name;
          int roll;
          double cgpa;

      public:
          // constructor
          Student(string n, int r, double c) {
              name = n;
              roll = r;
              cgpa = c;
          }

          // member functions
          void setCgpa(double c) {
              if (c >= 0 && c <= 4.0) cgpa = c;
              else cout << "Invalid CGPA" << endl;
          }

          double getCgpa() { return cgpa; }

          void display() {
              cout << "Name: " << name
                   << " | Roll: " << roll
                   << " | CGPA: " << cgpa << endl;
          }
      };

      int main() {
          // objects: instances of the class
          Student s1("Rahim Uddin", 101, 3.75);
          Student s2("Karim Ahmed", 102, 3.50);

          s1.display();
          s2.display();

          s2.setCgpa(3.80);        // change through a member function
          // s2.cgpa = 5.0;        // error: cgpa is private
          s2.display();

          cout << "Size of one object: " << sizeof(s1) << " bytes" << endl;
          return 0;
      }
      ```

      Output:
      ```
      Name: Rahim Uddin | Roll: 101 | CGPA: 3.75
      Name: Karim Ahmed | Roll: 102 | CGPA: 3.5
      Name: Karim Ahmed | Roll: 102 | CGPA: 3.8
      ```

      Difference between class and object:

   | Point | Class | Object |
      |---|---|---|
      | Definition | A blueprint or template that describes the data members and member functions of a category of things | An actual instance of a class, created from that blueprint |
      | Nature | A logical entity; it is a description only | A physical entity; it exists in memory |
      | Memory | No memory is allocated when a class is declared | Memory is allocated when an object is created |
      | How many | Declared once | Many objects can be created from one class |
      | Creation | With the keyword class | With the keyword new in Java, or by declaring a variable of the class type in C++ |
      | Contains | Declarations of members | Actual values for those members |
      | Analogy | The architect's plan of a house | The houses actually built from that plan |
      | Example | class Student { ... } | Student s1 = new Student(); |

   

      Points specific to C++:
      - Members are private by default in a class, and public by default in a struct.
      - An object may be created on the stack, as Student s1(...), or on the heap, as Student* p = new Student(...), in which case it must be freed with delete.
      - The size of an object is the sum of the sizes of its data members plus any padding; member functions are stored once for the whole class, not once per object.
6. **What are the common activities on OOP design process?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*


   Answer: The common activities in the object-oriented design process are the steps by which a problem statement is turned into a set of interacting classes.

   - Identify the objects and classes: read the requirements and pick out the nouns. Each significant noun that has both state and behaviour is a candidate class, for example Student, Account, Book, Invoice.

   - Identify the attributes: for each class, determine the data it must hold. These usually come from the descriptive nouns and adjectives in the requirements, for example a Student has a name, a roll number and a set of marks.

   - Identify the methods (responsibilities): determine what each class must be able to do. These usually come from the verbs in the requirements, for example deposit, withdraw, calculateGrade, issueBook.

   - Identify the relationships between classes:
     - Inheritance, an "is-a" relationship, for example SavingsAccount is an Account.
     - Association, a "uses-a" relationship, for example a Teacher teaches a Course.
     - Aggregation, a "has-a" relationship in which the parts can exist independently, for example a Department has Teachers.
     - Composition, a stronger "has-a" in which the parts cannot exist without the whole, for example a House has Rooms.
     - Dependency, in which one class temporarily uses another.

   - Determine the multiplicity of each relationship: one-to-one, one-to-many or many-to-many.

   - Build a class hierarchy: place common attributes and behaviour in a base class and specialise in derived classes, so that code is not duplicated.

   - Apply encapsulation: decide the access level of every member, keeping data private and exposing a minimal public interface.

   - Identify abstractions: decide which classes should be abstract, and which behaviour should be expressed as an interface so that several unrelated classes can provide it.

   - Design for polymorphism: identify the operations that different subclasses will perform differently, and declare them in the base class or interface so that client code can be written once.

   - Draw the design diagrams: a UML class diagram showing classes, attributes, methods and relationships; a use case diagram for the requirements; a sequence diagram for the interaction of objects over time; and a state diagram where objects have significant life cycles.

   - Define the interfaces between classes: fix the exact method signatures, so that different developers can work on different classes in parallel.

   - Review the design against principles: high cohesion within a class, low coupling between classes, and the SOLID principles, in particular the single responsibility principle and the open-closed principle.

   - Iterate and refine: object-oriented design is not a single pass. The model is revised as the requirements are better understood and as implementation reveals awkwardness.

   - Implement and test: write the classes, unit-test each one independently, then test the interactions.

   A simple worked identification: for the requirement "a library issues books to members, and a member may borrow up to five books at a time", the nouns Library, Book and Member become classes; issue and borrow become methods; the relationship between Member and Book is an association with multiplicity one to five; and the attribute "date of issue" belongs to the association itself, which suggests a fourth class, Loan.
7. **Write a programme to create an object of type batsman and calculate the average runs scored by the player.** *[RAKUB Programmer (PO) 12.10.2021 compact it 846-847 (ET: N/A)]*


   Answer: The program creates a Batsman class and calculates the batting average of a player.

   The batting average in cricket is defined as total runs divided by the number of times out, not by the number of innings played. Both are shown below.

   ```java
   class Batsman {
       private String name;
       private int matches;
       private int innings;
       private int totalRuns;
       private int notOuts;

       public Batsman(String name, int matches, int innings, int totalRuns, int notOuts) {
           this.name = name;
           this.matches = matches;
           this.innings = innings;
           this.totalRuns = totalRuns;
           this.notOuts = notOuts;
       }

       // official batting average: runs divided by dismissals
       public double battingAverage() {
           int dismissals = innings - notOuts;
           if (dismissals == 0) {
               return totalRuns;        // never dismissed
           }
           return (double) totalRuns / dismissals;
       }

       // simple average per innings
       public double runsPerInnings() {
           if (innings == 0) return 0;
           return (double) totalRuns / innings;
       }

       public void display() {
           System.out.printf("%-15s %-8d %-8d %-8d %-8d %-10.2f %-10.2f%n",
                   name, matches, innings, totalRuns, notOuts,
                   battingAverage(), runsPerInnings());
       }
   }

   public class BatsmanDemo {
       public static void main(String[] args) {
           Batsman[] players = {
               new Batsman("Tamim Iqbal",  241, 239, 8357, 11),
               new Batsman("Shakib Al Hasan", 247, 233, 7570, 32),
               new Batsman("Mushfiqur Rahim", 274, 254, 7795, 40)
           };

           System.out.printf("%-15s %-8s %-8s %-8s %-8s %-10s %-10s%n",
                   "Name", "Matches", "Innings", "Runs", "NotOut", "Average", "Per Inn");
           System.out.println("-------------------------------------------------------------------------");

           for (Batsman b : players) {
               b.display();
           }

           // finding the player with the highest average
           Batsman best = players[0];
           for (Batsman b : players) {
               if (b.battingAverage() > best.battingAverage()) {
                   best = b;
               }
           }
           System.out.println("-------------------------------------------------------------------------");
           System.out.print("Highest average: ");
           best.display();
       }
   }
   ```

   Sample output (the figures are illustrative):
   ```
   Name            Matches  Innings  Runs     NotOut   Average    Per Inn
   -------------------------------------------------------------------------
   Tamim Iqbal     241      239      8357     11       36.65      34.97
   Shakib Al Hasan 247      233      7570     32       37.66      32.49
   Mushfiqur Rahim 274      254      7795     40       36.43      30.69
   -------------------------------------------------------------------------
   Highest average: Shakib Al Hasan 247      233      7570     32       37.66      32.49
   ```

   Points demonstrated:
   - Class and object: Batsman is the blueprint, and an array of objects is created from it.
   - Encapsulation: all the data members are private, and the statistics are obtained only through methods.
   - The cast to double before the division, without which Java would perform integer division and discard the fractional part. This is the commonest error in average calculations.
   - A guard against division by zero, for a batsman who has never been dismissed.
   - The distinction between the official batting average and runs per innings, which is worth stating because they differ whenever there are not-outs.

## Encapsulation & Access Modifiers (6)

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*


   Answer: Java has three access specifier keywords, private, protected and public, and a fourth level called default which is obtained by writing no keyword at all. The visibility table asked for is given below, with Y for yes and N for no.

   Java has four levels of access, controlled by three keywords plus the default (no keyword at all).

   | Modifier | Same class | Same package, non-subclass | Same package, subclass | Different package, subclass | Different package, non-subclass |
   |---|---|---|---|---|---|
   | private | Y | N | N | N | N |
   | default (no keyword) | Y | Y | Y | N | N |
   | protected | Y | Y | Y | Y | N |
   | public | Y | Y | Y | Y | Y |

   Description of each:

   - private: the member is visible only inside the class where it is declared. Not even a subclass can see it. This is the strictest level. We use it for data members, and it is what makes encapsulation work. Example: a banking application keeps the account balance private.
   - default, also called package-private: we write no keyword at all. The member is visible to every class in the same package, but to nothing outside it. It gives more access than private, but less than protected. We use it for helper classes meant only for that package.
   - protected: visible inside the class, to every class in the same package, and to subclasses even if they are in a different package. It is used for members that a subclass must be able to use but that are not part of the public interface.
   - public: visible from everywhere. It is used for the methods that form the interface of the class.

   Rules:
   - A top-level class may be only public or default; it cannot be private or protected.
   - Constructors follow the same four levels. A private constructor prevents instantiation from outside, which is how the singleton pattern is implemented.
   - An overriding method may not reduce the visibility of the method it overrides; it may only keep it the same or widen it.
   Best practice:
   - Use private by default. It is the most restrictive.
   - Use default for utilities meant only for that package.
   - Use protected for inheritance hierarchies.
   - Use public only for the parts we truly mean to expose as an API.

   Filled answer in the Y and N form requested:

   | Accessible from | private | protected | public |
   |---|---|---|---|
   | Within the same class | Y | Y | Y |
   | From another class in the same package | N | Y | Y |
   | From a subclass in the same package | N | Y | Y |
   | From a subclass in a different package | N | Y | Y |
   | From a non-subclass in a different package | N | N | Y |
   | From anywhere in the program | N | N | Y |

   Example:

   ```java
   package university;

   public class Student {
       private   String password;    // only inside Student
                 String section;     // default: anywhere in package university
       protected int    roll;        // package plus subclasses anywhere
       public    String name;        // everywhere

       private void resetPassword() { }     // only inside Student
       public  void display() { }           // everywhere
   }
   ```
2. **Explain the various types of access specifiers.** *[DESCO Assistant Engineer 20.05.2023 compact it 579 (ET: DESCO)]*


   Answer: An access specifier (also called an access modifier) determines from where a class member can be reached. It is the mechanism by which encapsulation and data hiding are enforced.

   Java has four levels of access, controlled by three keywords plus the default (no keyword at all).

   | Modifier | Same class | Same package, non-subclass | Same package, subclass | Different package, subclass | Different package, non-subclass |
   |---|---|---|---|---|---|
   | private | Y | N | N | N | N |
   | default (no keyword) | Y | Y | Y | N | N |
   | protected | Y | Y | Y | Y | N |
   | public | Y | Y | Y | Y | Y |

   Description of each:

   - private: the member is visible only inside the class where it is declared. Not even a subclass can see it. This is the strictest level. We use it for data members, and it is what makes encapsulation work. Example: a banking application keeps the account balance private.
   - default, also called package-private: we write no keyword at all. The member is visible to every class in the same package, but to nothing outside it. It gives more access than private, but less than protected. We use it for helper classes meant only for that package.
   - protected: visible inside the class, to every class in the same package, and to subclasses even if they are in a different package. It is used for members that a subclass must be able to use but that are not part of the public interface.
   - public: visible from everywhere. It is used for the methods that form the interface of the class.

   Rules:
   - A top-level class may be only public or default; it cannot be private or protected.
   - Constructors follow the same four levels. A private constructor prevents instantiation from outside, which is how the singleton pattern is implemented.
   - An overriding method may not reduce the visibility of the method it overrides; it may only keep it the same or widen it.
   Best practice:
   - Use private by default. It is the most restrictive.
   - Use default for utilities meant only for that package.
   - Use protected for inheritance hierarchies.
   - Use public only for the parts we truly mean to expose as an API.

   In C++ there are three access specifiers, and no package-level concept:

   | Specifier | Same class | Derived class | Outside the class |
   |---|---|---|---|
   | private | Yes | No | No |
   | protected | Yes | Yes | No |
   | public | Yes | Yes | Yes |

   - private: accessible only inside the class and to its friend functions and friend classes. It is the default for a class.
   - protected: accessible inside the class and inside derived classes, but not from outside. It is used for members that subclasses need.
   - public: accessible from anywhere. It is the default for a struct.

   C++ also has inheritance access, which is written after the colon and controls how inherited members appear in the derived class:

   | Base member | public inheritance | protected inheritance | private inheritance |
   |---|---|---|---|
   | public | stays public | becomes protected | becomes private |
   | protected | stays protected | stays protected | becomes private |
   | private | not accessible | not accessible | not accessible |

   Example in C++:

   ```cpp
   class Base {
   private:
       int secret;          // only Base and its friends
   protected:
       int shared;          // Base and its derived classes
   public:
       int open;            // everyone
       void setAll(int a, int b, int c) { secret = a; shared = b; open = c; }
   };

   class Derived : public Base {
   public:
       void test() {
           // secret = 10;   // error: private in Base
           shared = 20;      // allowed: protected
           open   = 30;      // allowed: public
       }
   };

   int main() {
       Base b;
       // b.secret = 1;      // error
       // b.shared = 2;      // error
       b.open = 3;           // allowed
       return 0;
   }
   ```

   Purpose of access specifiers:
   - To enforce encapsulation, so that the internal state cannot be corrupted from outside.
   - To define a clear public interface, separating what a class promises from how it works.
   - To allow the implementation to be changed later without breaking client code.
   - To let a designer decide deliberately what a subclass may rely on.
3. **Which type of variable violates encapsulation rules?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: A public data member (a public instance variable) violates the rules of encapsulation.

   Reason:
   - Encapsulation requires that the internal state of an object be hidden and be changed only through methods that can validate the change. Declaring a data member public exposes it directly, so any part of the program may read or write it without any check.
   - The object can then be placed in an invalid state, for example a negative age or a negative account balance, and the class has no way to prevent it.
   - It also destroys the freedom to change the implementation later, because outside code now depends on the field itself rather than on a method.

   Example of the violation:

   ```java
   class BankAccount {
       public double balance;        // violates encapsulation
   }

   public class Demo {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount();
           acc.balance = -50000;     // nothing prevents this absurd value
       }
   }
   ```

   The correct form:

   ```java
   class BankAccount {
       private double balance;       // hidden

       public double getBalance() {
           return balance;
       }

       public void deposit(double amount) {
           if (amount > 0) {
               balance += amount;
           } else {
               System.out.println("Deposit must be positive");
           }
       }

       public boolean withdraw(double amount) {
           if (amount > 0 && amount <= balance) {
               balance -= amount;
               return true;
           }
           return false;
       }
   }
   ```

   Other cases that weaken encapsulation:
   - A public static mutable variable, which is effectively a global variable shared by the whole program.
   - A protected data member, which is weaker than private because every subclass, present and future, can change it directly.
   - A default (package-private) data member, which any class in the same package may alter.
   - A getter that returns a reference to a mutable internal object, such as an array or a collection. The caller can then modify the object's internals through that reference even though the field is private. The remedy is to return a copy or an unmodifiable view.

   ```java
   class Student {
       private int[] marks;
       public int[] getMarks() { return marks; }        // leaks the internal array
       public int[] getMarksSafe() { return marks.clone(); }   // correct
   }
   ```

   General rule: declare every data member private, and expose only the methods that are genuinely part of the interface.
4. **Which members of base class cannot access to derived class?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: The private members of a base class cannot be accessed by a derived class.

   Explanation:
   - Private members are inherited by the derived class, in the sense that they exist in memory as part of every derived object, but they are not accessible by name inside the derived class.
   - They can be reached only indirectly, through the public or protected methods that the base class itself provides.

   Accessibility of base class members in a derived class:

   | Base class member | Accessible in the derived class? |
   |---|---|
   | private | No |
   | protected | Yes |
   | public | Yes |
   | default (package-private, in Java) | Only if the derived class is in the same package |

   Example in Java:

   ```java
   class Base {
       private   int a = 10;
       protected int b = 20;
       public    int c = 30;

       public int getA() { return a; }     // the only legitimate route to 'a'
   }

   class Derived extends Base {
       void show() {
           // System.out.println(a);    // error: a has private access in Base
           System.out.println(b);       // allowed: protected
           System.out.println(c);       // allowed: public
           System.out.println(getA());  // allowed: reaches 'a' through a public method
       }
   }
   ```

   Example in C++:

   ```cpp
   class Base {
   private:
       int a;
   protected:
       int b;
   public:
       int c;
       int getA() { return a; }
   };

   class Derived : public Base {
   public:
       void show() {
           // a = 5;      // error: a is private
           b = 10;        // allowed
           c = 15;        // allowed
           cout << getA();  // allowed
       }
   };
   ```

   Two further points worth stating:
   - In C++, a friend function or a friend class of the base can access its private members, and this is not affected by inheritance.
   - Constructors and destructors are not inherited in either language, although a derived constructor must call a base constructor, explicitly or implicitly.

   Why the rule exists: it preserves encapsulation. If a derived class could reach the private data of its base directly, then any change to the base class's internal representation would break every subclass ever written, and the base class would lose all control over its own invariants.
5. **What are the various Access Specification in C++? Explain their purpose with are example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*


   Answer: C++ provides three access specifiers: private, protected and public.

   private:
   - Purpose: to hide the internal data of a class so that it cannot be read or written from outside. It is the mechanism of data hiding.
   - Accessible from: only within the same class, and from its friend functions and friend classes.
   - It is the default access level for a class, so any member declared before the first specifier is private.

   protected:
   - Purpose: to hide a member from the outside world while still making it available to derived classes. It is used for members that subclasses genuinely need in order to extend the behaviour of the base class.
   - Accessible from: within the same class, within derived classes, and from friends. Not from outside.

   public:
   - Purpose: to expose the interface of the class, that is the set of operations that the outside world is allowed to perform.
   - Accessible from: anywhere in the program.
   - It is the default access level for a struct.

   Summary table:

   | Accessible from | private | protected | public |
   |---|---|---|---|
   | Within the same class | Yes | Yes | Yes |
   | From a derived class | No | Yes | Yes |
   | From outside the class | No | No | Yes |
   | From a friend function or class | Yes | Yes | Yes |

   Example:

   ```cpp
   #include <iostream>
   using namespace std;

   class Employee {
   private:
       double salary;                 // hidden completely

   protected:
       int employeeId;                // hidden from outside, visible to subclasses

   public:
       string name;                   // part of the interface

       Employee(string n, int id, double s) {
           name = n;
           employeeId = id;
           setSalary(s);
       }

       // controlled access to the private member
       void setSalary(double s) {
           if (s >= 0) salary = s;
           else cout << "Salary cannot be negative" << endl;
       }

       double getSalary() { return salary; }
   };

   class Manager : public Employee {
   public:
       Manager(string n, int id, double s) : Employee(n, id, s) {}

       void showDetails() {
           cout << "Name: " << name << endl;          // public: allowed
           cout << "ID: "   << employeeId << endl;    // protected: allowed
           // cout << salary;                         // error: private
           cout << "Salary: " << getSalary() << endl; // allowed through a public method
       }
   };

   int main() {
       Manager m("Rahim Uddin", 101, 60000);
       m.showDetails();

       cout << m.name << endl;        // allowed: public
       // cout << m.employeeId;       // error: protected
       // cout << m.salary;           // error: private
       m.setSalary(-100);             // rejected by the validation
       return 0;
   }
   ```

   Output:
   ```
   Name: Rahim Uddin
   ID: 101
   Salary: 60000
   Rahim Uddin
   Salary cannot be negative
   ```

   Inheritance access in C++, which is a separate use of the same three keywords:

   | Base member | class D : public B | class D : protected B | class D : private B |
   |---|---|---|---|
   | public | remains public | becomes protected | becomes private |
   | protected | remains protected | remains protected | becomes private |
   | private | inaccessible | inaccessible | inaccessible |

   Public inheritance expresses an "is-a" relationship and is by far the most common; private inheritance expresses "implemented in terms of" and is rare.

   Design guidance: make data members private by default, expose behaviour through public methods, and use protected sparingly, because a protected member is part of the contract with every future subclass and is therefore almost as hard to change as a public one.
6. **How many specifiers are used in C++ programing?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


   Answer: Three access specifiers are used in C++ programming: private, protected and public.

   - private: accessible only within the same class and to its friends. It is the default for a class.
   - protected: accessible within the class, within derived classes, and to friends, but not from outside.
   - public: accessible from anywhere in the program. It is the default for a struct.

   Summary:

   | Accessible from | private | protected | public |
   |---|---|---|---|
   | Same class | Yes | Yes | Yes |
   | Derived class | No | Yes | Yes |
   | Outside the class | No | No | Yes |

   Point of comparison with Java: Java has four levels, because in addition to private, protected and public it has a default or package-private level that applies when no keyword is written. C++ has no such package concept, so it has only three.

   Note on the word "specifier" in C++: the standard also uses the term for other purposes, such as storage class specifiers (static, extern, mutable, thread_local) and type specifiers (const, volatile). If the question means access specifiers, the answer is three.

## Constructors & Destructors (5)

1. **What is constructor function? Write the properties of it.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*


   Answer: A constructor is a special member function of a class that is called automatically when an object is created. Its purpose is to initialise the object, so that it starts life in a valid state.

   Properties of a constructor:
   - Its name is exactly the same as the name of the class.
   - It has no return type at all, not even void.
   - It is invoked automatically at the moment an object is created; it is never called explicitly like an ordinary method.
   - It can be overloaded, so a class may have several constructors with different parameter lists.
   - It may take parameters, which is how initial values are supplied.
   - If no constructor is written, the compiler supplies a default one that takes no arguments. As soon as any constructor is written, that free default disappears.
   - It is normally public, so that objects can be created from outside. A private constructor prevents outside instantiation, which is how the singleton pattern is built.
   - It cannot be inherited, cannot be virtual in C++, and cannot be static or final.
   - In a derived class the base constructor runs first, and it is called with super(...) in Java or through the initialisation list in C++.

   Types of constructor:
   - Default constructor: takes no parameters and sets default values.
   - Parameterised constructor: takes arguments and sets the object from them.
   - Copy constructor: creates a new object as a copy of an existing one. In C++ its signature is ClassName(const ClassName& other).

   Example in C++:

   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
       string name;
       int roll;
       double cgpa;

   public:
       // default constructor
       Student() {
           name = "Unknown";
           roll = 0;
           cgpa = 0.0;
           cout << "Default constructor called" << endl;
       }

       // parameterised constructor
       Student(string n, int r, double c) : name(n), roll(r), cgpa(c) {
           cout << "Parameterised constructor called" << endl;
       }

       // copy constructor
       Student(const Student& s) {
           name = s.name;
           roll = s.roll;
           cgpa = s.cgpa;
           cout << "Copy constructor called" << endl;
       }

       // destructor
       ~Student() {
           cout << "Destructor called for " << name << endl;
       }

       void display() {
           cout << name << " | " << roll << " | " << cgpa << endl;
       }
   };

   int main() {
       Student s1;                              // default
       Student s2("Rahim", 101, 3.75);          // parameterised
       Student s3 = s2;                         // copy

       s1.display();
       s2.display();
       s3.display();
       return 0;
   }
   ```

   Output:
   ```
   Default constructor called
   Parameterised constructor called
   Copy constructor called
   Unknown | 0 | 0
   Rahim | 101 | 3.75
   Rahim | 101 | 3.75
   Destructor called for Rahim
   Destructor called for Rahim
   Destructor called for Unknown
   ```

   The destructors run in reverse order of construction, which is the rule in C++.
2. **Define copy constructor. What Static binding and Dynamic binding?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


   Answer:

   Copy constructor:

   A copy constructor is a constructor that creates a new object as a copy of an existing object of the same class. In C++ its signature is:

   ```cpp
   ClassName(const ClassName& other);
   ```

   The parameter must be passed by reference. If it were passed by value, creating that parameter would itself require a copy constructor, which would call itself endlessly.

   It is invoked in three situations:
   - When an object is initialised from another object: Student s2 = s1; or Student s2(s1);
   - When an object is passed to a function by value.
   - When an object is returned from a function by value.

   Why it must sometimes be written by hand: the compiler supplies a default copy constructor that copies each member one by one. This is called a shallow copy, and it is wrong whenever the class holds a pointer to dynamically allocated memory, because both objects would then point to the same block. When one object is destroyed the memory is freed, and the other is left with a dangling pointer; when the second is destroyed, the same memory is freed twice. Writing a copy constructor that allocates new memory and copies the contents is called a deep copy.

   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
       char* name;
       int roll;

   public:
       Student(const char* n, int r) {
           roll = r;
           name = new char[strlen(n) + 1];
           strcpy(name, n);
       }

       // deep copy constructor
       Student(const Student& s) {
           roll = s.roll;
           name = new char[strlen(s.name) + 1];   // separate memory
           strcpy(name, s.name);
           cout << "Copy constructor called" << endl;
       }

       ~Student() { delete[] name; }

       void setName(const char* n) { strcpy(name, n); }
       void display() { cout << name << " | " << roll << endl; }
   };

   int main() {
       Student s1("Rahim", 101);
       Student s2 = s1;          // copy constructor runs

       s2.setName("Karim");      // changing s2 must not affect s1

       s1.display();             // Rahim | 101
       s2.display();             // Karim | 101
       return 0;
   }
   ```

   With only the compiler's shallow copy, changing s2 would also change s1, and the program would crash on exit through a double free.

   Note on Java: Java has no copy constructor built into the language, but one can be written by hand, and the same shallow-versus-deep distinction applies to the clone() method.

   Static binding and dynamic binding:

   Binding means associating a method call with the actual code that will run.

   Static binding, also called early binding or compile-time binding:
   - The decision is made by the compiler, using the declared type of the reference or pointer.
   - It applies to static methods, private methods, final methods, variables, and to method overloading.
   - It is faster, because no lookup is needed at run time, but it is less flexible.

   Dynamic binding, also called late binding or run-time binding:
   - The decision is deferred until the program is running, and is made from the actual type of the object.
   - It applies to method overriding, that is to virtual functions in C++ and to ordinary instance methods in Java.
   - It is slightly slower, because it involves an indirection through the virtual table, but it is what makes run-time polymorphism and extensible design possible.

   ```java
   class Parent {
       static void staticMethod()   { System.out.println("Parent static"); }
       void instanceMethod()        { System.out.println("Parent instance"); }
   }

   class Child extends Parent {
       static void staticMethod()   { System.out.println("Child static"); }
       @Override
       void instanceMethod()        { System.out.println("Child instance"); }
   }

   public class BindingDemo {
       public static void main(String[] args) {
           Parent p = new Child();
           p.staticMethod();      // Parent static   -> static binding, by reference type
           p.instanceMethod();    // Child instance  -> dynamic binding, by object type
       }
   }
   ```

   | Point | Static binding | Dynamic binding |
   |---|---|---|
   | When resolved | Compile time | Run time |
   | Decided by | The declared type of the reference | The actual type of the object |
   | Applies to | static, private and final methods; overloading | Overriding; virtual functions |
   | Speed | Faster | Slightly slower |
   | Flexibility | Low | High |
   | Keyword in C++ | none | virtual |
3. **What is the constructor invoked in OOP?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*


   Answer: In object-oriented programming the constructor is invoked automatically at the moment an object is created. The programmer never calls it explicitly.

   The exact points at which it is invoked:

   - When an object is declared or allocated:
     - In C++: Student s1;  or  Student s2("Rahim", 101);  or  Student* p = new Student();
     - In Java: Student s = new Student();
     The keyword new is what triggers the constructor in Java.

   - When an object is created as a copy of another, the copy constructor is invoked. In C++ this happens in three situations: on initialisation from another object (Student s3 = s2;), when an object is passed to a function by value, and when an object is returned by value.

   - When a derived object is created, the base class constructor is invoked first, before the body of the derived constructor runs. In Java this is written as super(...) and must be the first statement; in C++ it is done through the member initialisation list. If it is not written, the compiler inserts a call to the no-argument base constructor.

   - When an object is a member of another class (composition), the member's constructor runs before the body of the enclosing class's constructor.

   - When an array of objects is created, the constructor runs once for every element.

   - When a temporary object is created during an expression.

   Order of invocation in an inheritance hierarchy:

   ```java
   class A {
       A() { System.out.println("Constructor of A"); }
   }
   class B extends A {
       B() { System.out.println("Constructor of B"); }
   }
   class C extends B {
       C() { System.out.println("Constructor of C"); }
   }

   public class Demo {
       public static void main(String[] args) {
           C obj = new C();
       }
   }
   ```

   Output:
   ```
   Constructor of A
   Constructor of B
   Constructor of C
   ```

   The base class is always constructed first, because the derived part of the object may depend on the base part being ready. Destructors run in exactly the reverse order.

   Which constructor is chosen: the compiler selects the overloaded constructor whose parameter list matches the arguments supplied, exactly as it does for an overloaded method. This is compile-time polymorphism.

   Two points often asked alongside:
   - A constructor cannot be called on an existing object; to reinitialise, an ordinary method must be used.
   - In Java one constructor may call another constructor of the same class using this(...), which must also be the first statement. This is called constructor chaining.
4. **What is constructor?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


   Answer: A constructor is a special member function of a class that is called automatically when an object is created. Its purpose is to initialise the object, so that it starts life in a valid state.

   Properties of a constructor:
   - Its name is exactly the same as the name of the class.
   - It has no return type at all, not even void.
   - It is invoked automatically at the moment an object is created; it is never called explicitly like an ordinary method.
   - It can be overloaded, so a class may have several constructors with different parameter lists.
   - It may take parameters, which is how initial values are supplied.
   - If no constructor is written, the compiler supplies a default one that takes no arguments. As soon as any constructor is written, that free default disappears.
   - It is normally public, so that objects can be created from outside. A private constructor prevents outside instantiation, which is how the singleton pattern is built.
   - It cannot be inherited, cannot be virtual in C++, and cannot be static or final.
   - In a derived class the base constructor runs first, and it is called with super(...) in Java or through the initialisation list in C++.

   Types of constructor:
   - Default constructor: takes no parameters and sets default values.
   - Parameterised constructor: takes arguments and sets the object from them.
   - Copy constructor: creates a new object as a copy of an existing one. In C++ its signature is ClassName(const ClassName& other).

   Example in C++:

   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
       string name;
       int roll;
       double cgpa;

   public:
       // default constructor
       Student() {
           name = "Unknown";
           roll = 0;
           cgpa = 0.0;
           cout << "Default constructor called" << endl;
       }

       // parameterised constructor
       Student(string n, int r, double c) : name(n), roll(r), cgpa(c) {
           cout << "Parameterised constructor called" << endl;
       }

       // copy constructor
       Student(const Student& s) {
           name = s.name;
           roll = s.roll;
           cgpa = s.cgpa;
           cout << "Copy constructor called" << endl;
       }

       // destructor
       ~Student() {
           cout << "Destructor called for " << name << endl;
       }

       void display() {
           cout << name << " | " << roll << " | " << cgpa << endl;
       }
   };

   int main() {
       Student s1;                              // default
       Student s2("Rahim", 101, 3.75);          // parameterised
       Student s3 = s2;                         // copy

       s1.display();
       s2.display();
       s3.display();
       return 0;
   }
   ```

   Output:
   ```
   Default constructor called
   Parameterised constructor called
   Copy constructor called
   Unknown | 0 | 0
   Rahim | 101 | 3.75
   Rahim | 101 | 3.75
   Destructor called for Rahim
   Destructor called for Rahim
   Destructor called for Unknown
   ```

   The destructors run in reverse order of construction, which is the rule in C++.
5. **(b) Why are constructor and destructor functions used in object oriented programming? Give examples of each function in C++ or java language.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*


   Answer: Constructors and destructors exist so that an object can be brought into a valid state automatically when it is created, and can release whatever it holds automatically when it is destroyed. Without them, initialisation and cleanup would have to be remembered and written by hand at every use, and forgetting either is one of the commonest causes of bugs and resource leaks.

   Why a constructor is used:
   - To initialise the data members at the moment of creation, so that no object ever exists in an undefined state.
   - To allocate the resources the object needs, such as dynamic memory, a file handle or a database connection.
   - To enforce the invariants of the class, by validating the arguments before storing them.
   - To make object creation concise and safe: the caller cannot forget to initialise, because the compiler calls the constructor automatically.
   - Overloaded constructors allow an object to be created in several different ways.

   Why a destructor is used:
   - To release the resources acquired by the object, such as freeing memory with delete, closing a file or closing a network connection.
   - To perform any final bookkeeping, such as decrementing an object counter or writing a log entry.
   - It is invoked automatically when the object goes out of scope or when delete is called, so cleanup cannot be forgotten.
   - Without it, a program that creates and destroys many objects would leak memory steadily until it exhausted the heap.

   Properties of a destructor in C++:
   - Its name is the class name preceded by a tilde, for example ~Student().
   - It takes no parameters and returns nothing, so it cannot be overloaded. A class has exactly one destructor.
   - It is called automatically, in reverse order of construction.
   - It should be declared virtual in any class intended to be used as a base class with polymorphism, otherwise deleting a derived object through a base pointer will not call the derived destructor.

   Example in C++:

   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class FileManager {
       char* buffer;
       string fileName;
       static int objectCount;

   public:
       // constructor: acquires the resource
       FileManager(string fname, int size) {
           fileName = fname;
           buffer = new char[size];        // dynamic memory acquired
           objectCount++;
           cout << "Constructor: " << fileName
                << " opened, buffer of " << size << " bytes allocated" << endl;
       }

       // destructor: releases the resource
       ~FileManager() {
           delete[] buffer;                // memory released
           objectCount--;
           cout << "Destructor: " << fileName
                << " closed, buffer released" << endl;
       }

       static int getCount() { return objectCount; }
   };

   int FileManager::objectCount = 0;

   int main() {
       cout << "Objects at start: " << FileManager::getCount() << endl;
       {
           FileManager f1("data.txt", 1024);
           FileManager f2("log.txt", 512);
           cout << "Objects inside the block: " << FileManager::getCount() << endl;
       }   // both destructors run automatically here, in reverse order

       cout << "Objects after the block: " << FileManager::getCount() << endl;
       return 0;
   }
   ```

   Output:
   ```
   Objects at start: 0
   Constructor: data.txt opened, buffer of 1024 bytes allocated
   Constructor: log.txt opened, buffer of 512 bytes allocated
   Objects inside the block: 2
   Destructor: log.txt closed, buffer released
   Destructor: data.txt closed, buffer released
   Objects after the block: 0
   ```

   Equivalent in Java:

   ```java
   class Student {
       private String name;
       private static int count = 0;

       // constructor
       public Student(String name) {
           this.name = name;
           count++;
           System.out.println("Constructor: object created for " + name);
       }

       public static int getCount() { return count; }
   }

   public class Demo {
       public static void main(String[] args) {
           Student s1 = new Student("Rahim");
           Student s2 = new Student("Karim");
           System.out.println("Total objects: " + Student.getCount());
       }
   }
   ```

   Important difference between the two languages: Java has no destructor. Memory is reclaimed automatically by the garbage collector, at an unpredictable time. The finalize() method existed for cleanup but was deprecated in Java 9 and removed in Java 18, because it gave no guarantees. The correct modern practice in Java is to implement AutoCloseable and use a try-with-resources block, which gives the deterministic cleanup that a C++ destructor provides:

   ```java
   class Resource implements AutoCloseable {
       Resource()          { System.out.println("Resource acquired"); }
       public void close() { System.out.println("Resource released"); }
   }

   public class TryDemo {
       public static void main(String[] args) {
           try (Resource r = new Resource()) {
               System.out.println("Using the resource");
           }   // close() is guaranteed to run here
       }
   }
   ```

   The C++ idiom in which a constructor acquires a resource and a destructor releases it is called RAII, Resource Acquisition Is Initialisation, and it is one of the most important patterns in the language.

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


   Answer: The value printed is 19.

   Step-by-step trace. The variable x is static, so there is one copy shared by every call, and it starts at 5.

   Call fun(3):
   - n = 3, which is greater than 1, so the recursion continues.
   - x = x + 2, so x becomes 7.
   - The statement is return fun(2) + x. Java evaluates the left operand first, so fun(2) is called before x is read.

   Call fun(2):
   - n = 2, which is greater than 1.
   - x = x + 2, so x becomes 9.
   - The statement is return fun(1) + x, and again fun(1) is evaluated first.

   Call fun(1):
   - n = 1, so the condition n <= 1 is true and the method returns 1 immediately. Note that x is not changed here.

   Return to fun(2):
   - fun(1) returned 1.
   - Now x is read, and its current value is 9.
   - fun(2) returns 1 + 9 = 10.

   Return to fun(3):
   - fun(2) returned 10.
   - Now x is read, and its current value is still 9, because no further increment has happened.
   - fun(3) returns 10 + 9 = 19.

   Output:
   ```
   19
   ```

   Summary table:

   | Call | Value of n | x after the increment | Value returned by the inner call | x when read | Result |
   |---|---|---|---|---|---|
   | fun(3) | 3 | 7 | 10 | 9 | 19 |
   | fun(2) | 2 | 9 | 1 | 9 | 10 |
   | fun(1) | 1 | not changed | none | not read | 1 |

   The two points that decide the answer:
   - x is declared static, so it is shared across all the recursive calls rather than each call having its own copy. If it were a local variable the answer would be different.
   - Java's evaluation order in the expression fun(n-1) + x is strictly left to right. The recursive call is completed first, and only then is x read. Because the deeper calls have already increased x to 9 by that time, the outer call adds 9 rather than the 7 it had just written. A reader who assumes that x is read before the recursive call would wrongly compute 10 + 7 = 17.
2. **(খ) কোন object-oriented programming language ব্যবহার করে একটি program লিখুন, যা recursive function ব্যবহার করে Fibonacci series প্রদান করবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: নিচে Java ভাষায় একটি প্রোগ্রাম দেওয়া হলো, যা recursive function ব্যবহার করে ফিবোনাচি ধারা তৈরি করে।

   ফিবোনাচি ধারার সংজ্ঞা:
   - F(0) = 0
   - F(1) = 1
   - F(n) = F(n-1) + F(n-2), যেখানে n বৃহত্তর বা সমান 2

   ধারাটি: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   ```java
   import java.util.Scanner;

   public class FibonacciRecursive {

       // recursive function
       public static int fibonacci(int n) {
           if (n == 0) {            // base case 1
               return 0;
           }
           if (n == 1) {            // base case 2
               return 1;
           }
           return fibonacci(n - 1) + fibonacci(n - 2);   // recursive case
       }

       public static void main(String[] args) {
           Scanner sc = new Scanner(System.in);
           System.out.print("How many terms? ");
           int terms = sc.nextInt();

           System.out.print("Fibonacci series: ");
           for (int i = 0; i < terms; i++) {
               System.out.print(fibonacci(i) + " ");
           }
           System.out.println();
           sc.close();
       }
   }
   ```

   নমুনা আউটপুট:
   ```
   How many terms? 10
   Fibonacci series: 0 1 1 2 3 5 8 13 21 34
   ```

   কার্যপ্রণালীর ব্যাখ্যা, fibonacci(4) এর জন্য:

   ```
   fibonacci(4)
   = fibonacci(3) + fibonacci(2)
   = [fibonacci(2) + fibonacci(1)] + [fibonacci(1) + fibonacci(0)]
   = [(fibonacci(1) + fibonacci(0)) + 1] + [1 + 0]
   = [(1 + 0) + 1] + 1
   = 2 + 1
   = 3
   ```

   গুরুত্বপূর্ণ দিক:
   - Base case অপরিহার্য। n == 0 ও n == 1 এই দুটি শর্ত না থাকলে ফাংশনটি অসীমবার নিজেকে ডাকতে থাকত এবং StackOverflowError ঘটত।
   - প্রতিটি রিকার্সিভ কল স্ট্যাকে একটি নতুন ফ্রেম তৈরি করে; base case এ পৌঁছালে ফ্রেমগুলো একে একে ফিরে আসে।

   দক্ষতার সমস্যা: সাধারণ রিকার্সিভ পদ্ধতিতে একই মান বারবার হিসাব হয়। fibonacci(5) নির্ণয়ে fibonacci(2) তিনবার এবং fibonacci(3) দুইবার হিসাব হয়। এর সময় জটিলতা O(2^n), তাই n = 40 এর বেশি হলে প্রোগ্রামটি অত্যন্ত ধীর হয়ে যায়।

   সমাধান ১ — Memoization (উপরের দিক থেকে):

   ```java
   public class FibonacciMemo {
       static long[] memo;

       public static long fibonacci(int n) {
           if (n <= 1) return n;
           if (memo[n] != -1) return memo[n];      // আগে হিসাব করা থাকলে তা-ই ফেরত
           memo[n] = fibonacci(n - 1) + fibonacci(n - 2);
           return memo[n];
       }

       public static void main(String[] args) {
           int terms = 50;
           memo = new long[terms + 1];
           java.util.Arrays.fill(memo, -1);

           for (int i = 0; i < terms; i++) {
               System.out.print(fibonacci(i) + " ");
           }
       }
   }
   ```

   এতে সময় জটিলতা O(2^n) থেকে কমে O(n) হয়ে যায়।

   সমাধান ২ — Iterative পদ্ধতি (সবচেয়ে দক্ষ):

   ```java
   public static long fibonacciIterative(int n) {
       if (n <= 1) return n;
       long a = 0, b = 1, c = 0;
       for (int i = 2; i <= n; i++) {
           c = a + b;
           a = b;
           b = c;
       }
       return c;
   }
   ```

   এর সময় জটিলতা O(n) এবং স্থান জটিলতা O(1), অর্থাৎ স্ট্যাকও ব্যবহার করতে হয় না।

   তুলনা:

   | পদ্ধতি | সময় জটিলতা | স্থান জটিলতা | মন্তব্য |
   |---|---|---|---|
   | সাধারণ রিকার্সন | O(2^n) | O(n) স্ট্যাক | সহজ ও সুস্পষ্ট, কিন্তু ধীর |
   | Memoization সহ রিকার্সন | O(n) | O(n) | দ্রুত, রিকার্সিভ কাঠামো অক্ষুণ্ন |
   | Iterative | O(n) | O(1) | সবচেয়ে দক্ষ |
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


   Answer: The value printed is 19.

   Step-by-step trace. The variable x is static, so there is one copy shared by every call, and it starts at 5.

   Call fun(3):
   - n = 3, which is greater than 1, so the recursion continues.
   - x = x + 2, so x becomes 7.
   - The statement is return fun(2) + x. Java evaluates the left operand first, so fun(2) is called before x is read.

   Call fun(2):
   - n = 2, which is greater than 1.
   - x = x + 2, so x becomes 9.
   - The statement is return fun(1) + x, and again fun(1) is evaluated first.

   Call fun(1):
   - n = 1, so the condition n <= 1 is true and the method returns 1 immediately. Note that x is not changed here.

   Return to fun(2):
   - fun(1) returned 1.
   - Now x is read, and its current value is 9.
   - fun(2) returns 1 + 9 = 10.

   Return to fun(3):
   - fun(2) returned 10.
   - Now x is read, and its current value is still 9, because no further increment has happened.
   - fun(3) returns 10 + 9 = 19.

   Output:
   ```
   19
   ```

   Summary table:

   | Call | Value of n | x after the increment | Value returned by the inner call | x when read | Result |
   |---|---|---|---|---|---|
   | fun(3) | 3 | 7 | 10 | 9 | 19 |
   | fun(2) | 2 | 9 | 1 | 9 | 10 |
   | fun(1) | 1 | not changed | none | not read | 1 |

   The two points that decide the answer:
   - x is declared static, so it is shared across all the recursive calls rather than each call having its own copy. If it were a local variable the answer would be different.
   - Java's evaluation order in the expression fun(n-1) + x is strictly left to right. The recursive call is completed first, and only then is x read. Because the deeper calls have already increased x to 9 by that time, the outer call adds 9 rather than the 7 it had just written. A reader who assumes that x is read before the recursive call would wrongly compute 10 + 7 = 17.

## Exception Handling (3)

1. **(b) What is exception? Explain how it can be used for debugging a program.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*


   Answer: An exception is an abnormal event that occurs during the execution of a program and disrupts its normal flow of instructions. Examples are dividing by zero, opening a file that does not exist, using a null reference, or accessing an array element beyond its bounds.

   In Java every exception is an object of a class that descends from java.lang.Throwable, whose two branches are Error and Exception.

   Hierarchy:
   ```
   Throwable
      |
      +-- Error                  (serious problems the program should not catch)
      |     +-- OutOfMemoryError, StackOverflowError
      |
      +-- Exception
            +-- IOException, SQLException, ClassNotFoundException   (checked)
            +-- RuntimeException                                    (unchecked)
                  +-- NullPointerException
                  +-- ArithmeticException
                  +-- ArrayIndexOutOfBoundsException
                  +-- NumberFormatException
   ```

   Checked exceptions must either be caught or be declared with throws, and the compiler enforces this. Unchecked exceptions, which descend from RuntimeException, need not be declared; they generally indicate programming errors.

   The five keywords:
   - try: encloses the code that might throw an exception.
   - catch: handles a particular type of exception.
   - finally: contains code that runs whether or not an exception occurred, and is used for cleanup.
   - throw: raises an exception explicitly.
   - throws: declares that a method may propagate an exception to its caller.

   How exceptions help in debugging a program:

   - The stack trace pinpoints the fault: when an exception is not caught, the JVM prints the exception type, the message and the complete chain of method calls with line numbers. This tells the developer exactly which line failed and how the program reached it, which is usually the hardest part of debugging.

   - The exception type identifies the category of fault: a NullPointerException says an object was never initialised, a NumberFormatException says the input was not a valid number, an ArrayIndexOutOfBoundsException says a loop bound is wrong. The name itself narrows the search.

   - The program fails at the point of the error rather than continuing with corrupt data. Without exceptions, an error such as a failed file open would return a special value that a careless programmer might ignore, and the real symptom would appear far from the real cause.

   - Custom exceptions carry domain meaning: a class such as InsufficientBalanceException makes a business rule violation immediately obvious in the log, instead of appearing as a mysterious negative number.

   - Logging inside a catch block records the state of the program at the moment of failure, which is often the only evidence available for a fault that occurs in production.

   - The finally block guarantees cleanup, so a file or a database connection is closed even when an error occurs, which prevents a second, misleading failure later.

   - Exception chaining preserves the original cause. Wrapping a low-level SQLException in a high-level DataAccessException while passing the original as the cause keeps the full trail visible.

   Example:

   ```java
   import java.util.Scanner;

   public class ExceptionDemo {

       static double divide(int a, int b) {
           if (b == 0) {
               throw new ArithmeticException("Division by zero attempted with a = " + a);
           }
           return (double) a / b;
       }

       public static void main(String[] args) {
           int[] numbers = {10, 20, 30};

           try {
               System.out.println(divide(100, 5));      // works: 20.0
               System.out.println(numbers[5]);          // throws
               System.out.println(divide(100, 0));      // never reached
           }
           catch (ArithmeticException e) {
               System.out.println("Arithmetic problem: " + e.getMessage());
           }
           catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Bad array index: " + e.getMessage());
               e.printStackTrace();      // prints the full trace for debugging
           }
           catch (Exception e) {
               System.out.println("Some other problem: " + e);
           }
           finally {
               System.out.println("This always runs: cleanup done");
           }

           System.out.println("Program continues normally");
       }
   }
   ```

   Output:
   ```
   20.0
   Bad array index: Index 5 out of bounds for length 3
   java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 3
       at ExceptionDemo.main(ExceptionDemo.java:16)
   This always runs: cleanup done
   Program continues normally
   ```

   The trace names the file, the method and the line, which is precisely what a developer needs.

   Good practice:
   - Catch the most specific exception first and the general Exception last; the reverse order will not compile.
   - Never write an empty catch block; swallowing an exception silently destroys the very information that makes debugging possible.
   - Do not use exceptions for ordinary control flow, because throwing and catching is expensive.
   - Prefer try-with-resources for anything that must be closed.
2. **What is difference between exception and error in Java?** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*


   Answer: In Java both Error and Exception are subclasses of java.lang.Throwable, but they represent very different kinds of problem.

   | Point | Error | Exception |
   |---|---|---|
   | Nature | A serious problem in the run-time environment itself | An abnormal condition that the application can reasonably anticipate |
   | Cause | Usually beyond the control of the program, such as exhaustion of memory or of the stack | Usually within the program or its inputs, such as bad data or a missing file |
   | Should it be caught | No; the application generally cannot recover | Yes; it should be caught and handled |
   | Recovery | Normally impossible | Normally possible |
   | Checked or unchecked | All errors are unchecked | Checked exceptions must be handled or declared; unchecked ones need not be |
   | Compiler enforcement | None | Checked exceptions are enforced by the compiler |
   | Package | java.lang | java.lang, java.io, java.sql and others |
   | Typical response | Let the program terminate and fix the underlying condition | Handle it, log it, retry, or report it to the user |
   | Examples | OutOfMemoryError, StackOverflowError, VirtualMachineError, NoClassDefFoundError, AssertionError | IOException, SQLException, ClassNotFoundException, NullPointerException, ArithmeticException, ArrayIndexOutOfBoundsException |

   The hierarchy:

   ```
   Throwable
      |
      +-- Error (unchecked, do not catch)
      |     +-- OutOfMemoryError
      |     +-- StackOverflowError
      |     +-- NoClassDefFoundError
      |
      +-- Exception
            +-- IOException          (checked)
            +-- SQLException         (checked)
            +-- ClassNotFoundException (checked)
            +-- RuntimeException     (unchecked)
                  +-- NullPointerException
                  +-- ArithmeticException
                  +-- ArrayIndexOutOfBoundsException
                  +-- NumberFormatException
                  +-- IllegalArgumentException
   ```

   Examples:

   ```java
   public class ErrorVsException {

       // causes StackOverflowError: infinite recursion
       static void recurse() {
           recurse();
       }

       public static void main(String[] args) {

           // Exception: anticipated and handled
           try {
               int[] arr = new int[3];
               arr[5] = 10;
           } catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Handled exception: " + e.getMessage());
           }

           try {
               int result = 10 / 0;
           } catch (ArithmeticException e) {
               System.out.println("Handled exception: " + e.getMessage());
           }

           // Error: technically catchable, but the program cannot really recover
           try {
               recurse();
           } catch (StackOverflowError e) {
               System.out.println("Caught an Error, but the state is unreliable");
           }
       }
   }
   ```

   Output:
   ```
   Handled exception: Index 5 out of bounds for length 3
   Handled exception: / by zero
   Caught an Error, but the state is unreliable
   ```

   Why an Error should not be caught: it signals that the JVM or the environment is in a condition the program cannot mend. Catching an OutOfMemoryError and continuing is dangerous, because the very act of handling it may need memory that is not there, and any data structure being built at the time may be half-formed. The correct response is to let the program stop and to fix the cause, for example by increasing the heap or by correcting the recursion.

   The distinction in one line: an Exception is a problem the program is expected to deal with; an Error is a problem that means the program can no longer be trusted to run.
3. **What is exception handling? Write with an example.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*


   Answer: Exception handling is the mechanism by which a program deals with abnormal events that occur during execution, so that it can respond to them in a controlled way instead of terminating abruptly.

   Purpose:
   - To keep the program running when a recoverable problem occurs.
   - To separate the code that does the work from the code that deals with failure, which keeps both readable.
   - To make sure resources such as files and connections are released even when something goes wrong.
   - To report meaningful information to the user and to the developer instead of a raw crash.

   The five keywords in Java:
   - try: encloses the statements that may throw an exception.
   - catch: handles a particular type of exception. A try may have several catch blocks.
   - finally: always executes, whether an exception occurred or not, and is used for cleanup.
   - throw: raises an exception explicitly, for example when a business rule is violated.
   - throws: declares in a method signature that the method may pass an exception on to its caller.

   General structure:

   ```java
   try {
       // code that might fail
   }
   catch (SpecificException e) {
       // handle that specific case
   }
   catch (Exception e) {
       // handle anything else
   }
   finally {
       // always runs: release resources
   }
   ```

   Complete example:

   ```java
   import java.util.Scanner;

   // a custom exception for a business rule
   class InsufficientBalanceException extends Exception {
       public InsufficientBalanceException(String message) {
           super(message);
       }
   }

   class BankAccount {
       private double balance;

       public BankAccount(double balance) {
           this.balance = balance;
       }

       public void withdraw(double amount) throws InsufficientBalanceException {
           if (amount <= 0) {
               throw new IllegalArgumentException("Amount must be positive");
           }
           if (amount > balance) {
               throw new InsufficientBalanceException(
                   "Insufficient balance. Available: Tk " + balance
                   + ", requested: Tk " + amount);
           }
           balance -= amount;
           System.out.println("Withdrawn Tk " + amount + ". Balance: Tk " + balance);
       }
   }

   public class ExceptionHandlingDemo {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount(5000);
           Scanner sc = new Scanner(System.in);

           try {
               acc.withdraw(2000);       // succeeds
               acc.withdraw(10000);      // throws InsufficientBalanceException
               acc.withdraw(-100);       // never reached
           }
           catch (InsufficientBalanceException e) {
               System.out.println("Business rule violated: " + e.getMessage());
           }
           catch (IllegalArgumentException e) {
               System.out.println("Invalid input: " + e.getMessage());
           }
           catch (Exception e) {
               System.out.println("Unexpected problem: " + e);
           }
           finally {
               sc.close();
               System.out.println("Transaction session closed");
           }

           System.out.println("Program continues normally");
       }
   }
   ```

   Output:
   ```
   Withdrawn Tk 2000.0. Balance: Tk 3000.0
   Business rule violated: Insufficient balance. Available: Tk 3000.0, requested: Tk 10000.0
   Transaction session closed
   Program continues normally
   ```

   Without exception handling the program would have terminated at the second withdrawal, and the Scanner would never have been closed.

   The modern try-with-resources form, which closes resources automatically:

   ```java
   import java.io.BufferedReader;
   import java.io.FileReader;
   import java.io.IOException;

   public class FileReadDemo {
       public static void main(String[] args) {
           try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
               String line;
               while ((line = br.readLine()) != null) {
                   System.out.println(line);
               }
           }
           catch (IOException e) {
               System.out.println("Could not read the file: " + e.getMessage());
           }
           // br is closed automatically, even if an exception was thrown
       }
   }
   ```

   Rules and good practice:
   - Catch the most specific exception first; putting catch (Exception e) before a more specific one is a compile error, because the later block would be unreachable.
   - Never leave a catch block empty; swallowing an exception silently hides the fault.
   - Use finally, or better try-with-resources, for anything that must be closed.
   - Throw a custom exception when a domain rule is broken, so that the log names the business problem rather than a generic condition.
   - Do not use exceptions for ordinary control flow, because throwing and catching is expensive.
   - A method that catches an exception it cannot handle should rethrow it, wrapping it if necessary, so that the original cause is preserved.

## C++ OOP Concepts & Friend Functions (2)

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1355 (ET: N/A)]*
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```


   Answer: A friend function is a function that is not a member of a class but is granted permission by that class to access its private and protected members. The permission is given by declaring the function inside the class with the keyword friend.

   Key properties:
   - It is declared inside the class but defined outside it, and the keyword friend is not repeated in the definition.
   - It is not a member function, so it is called like an ordinary function, without an object and without the dot operator.
   - It has no this pointer, so it must receive the object as a parameter.
   - Friendship is granted, not taken: a class chooses who may see its internals.
   - Friendship is not inherited, is not transitive (a friend of a friend is not a friend), and is not reciprocal.
   - It may be declared in the public, private or protected section; the placement makes no difference.

   Adding the required friend function to the given class:

   ```cpp
   #include <iostream>
   using namespace std;

   class myclass {
       int num;
   public:
       myclass(int i) { num = i; }

       // declaration of the friend function
       friend bool isneg(myclass obj);
   };

   // definition outside the class; the keyword friend is not repeated
   bool isneg(myclass obj) {
       return (obj.num < 0);      // direct access to the private member num
   }

   int main() {
       myclass a(10);
       myclass b(-25);
       myclass c(0);

       cout << boolalpha;                 // print true and false instead of 1 and 0
       cout << "a is negative? " << isneg(a) << endl;
       cout << "b is negative? " << isneg(b) << endl;
       cout << "c is negative? " << isneg(c) << endl;
       return 0;
   }
   ```

   Output:
   ```
   a is negative? false
   b is negative? true
   c is negative? false
   ```

   Explanation:
   - Without the friend declaration, the line return (obj.num < 0); would not compile, because num is private and isneg() is not a member of myclass.
   - The object is passed by value as a parameter, since a non-member function has no this pointer of its own. Passing by constant reference, as bool isneg(const myclass& obj), would be more efficient and is the preferred style.
   - The function is called as isneg(a), not a.isneg(), because it is not a member.

   A slightly better version, passing by constant reference:

   ```cpp
   class myclass {
       int num;
   public:
       myclass(int i) : num(i) {}
       friend bool isneg(const myclass& obj);
   };

   bool isneg(const myclass& obj) { return obj.num < 0; }
   ```

   When a friend function is genuinely useful:
   - Operator overloading where the left operand is not an object of the class, in particular the stream insertion and extraction operators, which must be written as friends: friend ostream& operator<<(ostream& out, const myclass& obj);
   - A function that must access the private members of two different classes, for example a function that adds a Complex and a Polar object.

   Caution: friendship weakens encapsulation, so it should be used only where a member function genuinely cannot do the job.
2. **(ক) Friend Function কী? উহার সুবিধা অসুবিধাগুলো লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


   Answer: ফ্রেন্ড ফাংশন (Friend Function) হলো এমন একটি ফাংশন, যা কোনো ক্লাসের সদস্য না হয়েও ওই ক্লাসের private ও protected সদস্যগুলোতে সরাসরি প্রবেশাধিকার পায়। ক্লাসের ভেতরে friend কীওয়ার্ড দিয়ে ঘোষণা করে এই অনুমতি দেওয়া হয়।

   বৈশিষ্ট্য:
   - ক্লাসের ভেতরে কেবল ঘোষণা দেওয়া হয়, সংজ্ঞা লেখা হয় ক্লাসের বাইরে এবং সেখানে friend কীওয়ার্ড আর লেখা হয় না।
   - এটি সদস্য ফাংশন নয়, তাই সাধারণ ফাংশনের মতো ডাকতে হয়; অবজেক্ট ও ডট অপারেটর লাগে না।
   - এর this পয়েন্টার নেই, তাই অবজেক্টকে প্যারামিটার হিসেবে পাঠাতে হয়।
   - বন্ধুত্ব দেওয়া হয়, নেওয়া যায় না; ক্লাস নিজেই ঠিক করে কাকে অনুমতি দেবে।
   - বন্ধুত্ব উত্তরাধিকারসূত্রে যায় না, সংক্রামক নয় (বন্ধুর বন্ধু বন্ধু নয়) এবং পারস্পরিকও নয়।
   - public, private বা protected — যেকোনো অংশে ঘোষণা করা যায়; অবস্থানভেদে কোনো পার্থক্য হয় না।
   - একটি সম্পূর্ণ ক্লাসকেও friend ঘোষণা করা যায়, তখন ওই ক্লাসের সব সদস্য ফাংশন প্রবেশাধিকার পায়।

   উদাহরণ:

   ```cpp
   #include <iostream>
   using namespace std;

   class Box {
       double width;              // private

   public:
       Box(double w) : width(w) {}

       friend void printWidth(Box b);          // ফ্রেন্ড ফাংশনের ঘোষণা
       friend class BoxInspector;              // ফ্রেন্ড ক্লাসের ঘোষণা
   };

   void printWidth(Box b) {
       cout << "Width = " << b.width << endl;  // private সদস্যে সরাসরি প্রবেশ
   }

   class BoxInspector {
   public:
       void check(Box b) {
           cout << (b.width > 10 ? "Large box" : "Small box") << endl;
       }
   };

   int main() {
       Box b(15.5);
       printWidth(b);        // Width = 15.5
       BoxInspector insp;
       insp.check(b);        // Large box
       return 0;
   }
   ```

   সুবিধাসমূহ:
   - দুই বা ততোধিক ভিন্ন ক্লাসের private সদস্য একসঙ্গে ব্যবহার করে কাজ করা যায়। যেমন একটি ফাংশন Complex ও Polar দুই ক্লাসের ব্যক্তিগত তথ্য নিয়ে হিসাব করতে পারে, যা কোনো একটি ক্লাসের সদস্য ফাংশন দিয়ে সম্ভব নয়।
   - অপারেটর ওভারলোডিংয়ে অপরিহার্য, বিশেষত যখন বাঁ দিকের অপারেন্ড ওই ক্লাসের অবজেক্ট নয়। যেমন cout << obj; লিখতে হলে operator<< কে friend হতেই হয়, কারণ বাঁ পাশে আছে ostream, আমাদের ক্লাস নয়।
   - কখনো কখনো কোড বেশি স্বাভাবিক ও পাঠযোগ্য হয়। ২ * obj লেখা obj.multiply(2) এর চেয়ে স্বাভাবিক।
   - কিছু ক্ষেত্রে কর্মদক্ষতা বাড়ে, কারণ গেটার-সেটারের অতিরিক্ত ফাংশন কল এড়ানো যায়।
   - দুটি সম্পর্কিত ক্লাসের মধ্যে ঘনিষ্ঠ সহযোগিতা প্রকাশ করা যায়, যেমন LinkedList ও Node।

   অসুবিধাসমূহ:
   - এনক্যাপসুলেশন দুর্বল হয়: ফ্রেন্ড ফাংশন ক্লাসের ব্যক্তিগত তথ্য দেখে ফেলে, যা তথ্য গোপনীয়তার মূল নীতির পরিপন্থী।
   - রক্ষণাবেক্ষণ কঠিন হয়: ক্লাসের অভ্যন্তরীণ গঠন বদলালে সব ফ্রেন্ড ফাংশনও বদলাতে হয়। ফলে ক্লাসটি আর স্বাধীনভাবে পরিবর্তনযোগ্য থাকে না।
   - অবজেক্ট ওরিয়েন্টেড নীতির সঙ্গে সাংঘর্ষিক: এটি কার্যত ফাংশন-কেন্দ্রিক পদ্ধতির দিকে ফিরে যাওয়া।
   - এটি উত্তরাধিকারসূত্রে যায় না, তাই ডেরাইভড ক্লাসের জন্য আলাদা করে ঘোষণা করতে হয়।
   - অতিরিক্ত ব্যবহারে ক্লাসগুলোর মধ্যে আঁটসাঁট সংযুক্তি (tight coupling) তৈরি হয়।
   - Java ও C# এ এই ধারণা নেই, তাই এমন কোড অন্য ভাষায় সরাসরি রূপান্তরযোগ্য নয়।

   ব্যবহারের নির্দেশনা: যেখানে সদস্য ফাংশন দিয়ে কাজটি করা যায়, সেখানে ফ্রেন্ড ফাংশন ব্যবহার করা উচিত নয়। কেবল অপারেটর ওভারলোডিং এবং দুই ক্লাসের যৌথ কাজে এটি ব্যবহার করা যুক্তিসঙ্গত।

## Interfaces & Abstract Classes (2)

1. **Class/Interface implementation of code?** *[BCIC Assistant Programmer 14.02.2025 compact it 1329 (ET: BUET)]*


   Answer: An interface declares what a class can do without saying how it does it. It contains method signatures with no bodies, and any class that implements the interface is obliged to supply the implementations. It is the strongest form of abstraction in Java, and it is how a common capability is given to unrelated classes.

   Interface compared with an abstract class:

   | Point | Interface | Abstract class |
   |---|---|---|
   | Methods | Abstract by default; default, static and private methods allowed since Java 8 and 9 | May have both abstract and concrete methods |
   | Variables | Implicitly public, static and final, that is constants only | May have instance variables of any access level |
   | Constructor | Not allowed | Allowed, and called by the subclass |
   | Multiple inheritance | A class may implement any number of interfaces | A class may extend only one abstract class |
   | Keyword to use it | implements | extends |
   | Access modifiers on methods | Implicitly public | Any |
   | Purpose | To define a capability or contract, a "can-do" relationship | To share common code in a family, an "is-a" relationship |
   | When to choose | When unrelated classes must share a capability | When related classes share both state and code |

   Complete example implementing an interface:

   ```java
   // the contract
   interface Payable {
       double TAX_RATE = 0.10;                 // public static final by default

       double calculateSalary();               // abstract by default
       String getRole();

       default void printPayslip() {           // default method, Java 8 onwards
           double gross = calculateSalary();
           double tax = gross * TAX_RATE;
           System.out.printf("%-12s Gross: Tk %-10.2f Tax: Tk %-9.2f Net: Tk %.2f%n",
                   getRole(), gross, tax, gross - tax);
       }

       static double annual(double monthly) {  // static method, Java 8 onwards
           return monthly * 12;
       }
   }

   // a second, independent capability
   interface Reportable {
       void generateReport();
   }

   // one class implementing two interfaces: multiple inheritance of type
   class Manager implements Payable, Reportable {
       private double basic;
       private double allowance;

       Manager(double basic, double allowance) {
           this.basic = basic;
           this.allowance = allowance;
       }

       @Override
       public double calculateSalary() {
           return basic + allowance;
       }

       @Override
       public String getRole() { return "Manager"; }

       @Override
       public void generateReport() {
           System.out.println("Manager's monthly report generated");
       }
   }

   class Consultant implements Payable {
       private int hours;
       private double rate;

       Consultant(int hours, double rate) {
           this.hours = hours;
           this.rate = rate;
       }

       @Override
       public double calculateSalary() { return hours * rate; }

       @Override
       public String getRole() { return "Consultant"; }
   }

   public class InterfaceDemo {
       public static void main(String[] args) {
           Payable[] staff = {
               new Manager(60000, 15000),
               new Consultant(120, 800)
           };

           for (Payable p : staff) {
               p.printPayslip();                 // the default method, one implementation
           }

           System.out.println("Annual salary of the first: Tk "
                   + Payable.annual(staff[0].calculateSalary()));

           // an interface reference can be narrowed when the capability is needed
           if (staff[0] instanceof Reportable) {
               ((Reportable) staff[0]).generateReport();
           }
       }
   }
   ```

   Output:
   ```
   Manager      Gross: Tk 75000.00   Tax: Tk 7500.00   Net: Tk 67500.00
   Consultant   Gross: Tk 96000.00   Tax: Tk 9600.00   Net: Tk 86400.00
   Annual salary of the first: Tk 900000.0
   Manager's monthly report generated
   ```

   Points demonstrated:
   - An interface as a contract: Payable guarantees that anything payable can report its salary and its role.
   - Multiple interface implementation, which is how Java obtains the benefits of multiple inheritance without the diamond problem.
   - Constants in an interface, which are automatically public, static and final.
   - Default methods, which allow shared behaviour to be added to an interface without breaking existing implementations.
   - Static methods in an interface, used as utilities.
   - Polymorphism through an interface reference: the array is of type Payable[], yet each element behaves according to its own class.
   - instanceof and casting, used when a second, optional capability is required.
2. **An Abstract class Player with two sub classes Bowler and Batsman, Abstract class has one abstract method average, also have constructor and a string function that display name bowler or batsman. Batsman class implement abstract function average and display result, Batsman class have run and number match data. Now write a Java Program and show Batsman average run.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*


   Answer: The program uses an abstract class Player with an abstract method average(), a constructor, and a concrete method that returns the type of player. Batsman implements average() using runs and matches.

   ```java
   // Abstract base class
   abstract class Player {
       protected String name;
       protected int matches;

       // constructor of an abstract class: called by the subclasses
       public Player(String name, int matches) {
           this.name = name;
           this.matches = matches;
       }

       // abstract method: every subclass must implement it
       public abstract double average();

       // concrete method returning a String
       public String playerType() {
           return "Player";
       }

       public void display() {
           System.out.println("Name    : " + name);
           System.out.println("Type    : " + playerType());
           System.out.println("Matches : " + matches);
           System.out.printf("Average : %.2f%n", average());
           System.out.println("--------------------------------");
       }
   }

   // Subclass 1
   class Batsman extends Player {
       private int totalRuns;

       public Batsman(String name, int matches, int totalRuns) {
           super(name, matches);           // call the base constructor
           this.totalRuns = totalRuns;
       }

       @Override
       public double average() {
           if (matches == 0) return 0;
           return (double) totalRuns / matches;    // runs per match
       }

       @Override
       public String playerType() {
           return "Batsman";
       }

       public int getTotalRuns() { return totalRuns; }
   }

   // Subclass 2
   class Bowler extends Player {
       private int runsConceded;
       private int wickets;

       public Bowler(String name, int matches, int runsConceded, int wickets) {
           super(name, matches);
           this.runsConceded = runsConceded;
           this.wickets = wickets;
       }

       @Override
       public double average() {
           if (wickets == 0) return 0;
           return (double) runsConceded / wickets;   // bowling average
       }

       @Override
       public String playerType() {
           return "Bowler";
       }
   }

   public class CricketDemo {
       public static void main(String[] args) {

           // Player p = new Player("X", 10);   // error: an abstract class cannot be instantiated

           Batsman b1 = new Batsman("Tamim Iqbal", 100, 3500);
           Batsman b2 = new Batsman("Mushfiqur Rahim", 120, 3600);
           Bowler  w1 = new Bowler("Shakib Al Hasan", 110, 4200, 150);

           System.out.println("========= PLAYER STATISTICS =========");
           b1.display();
           b2.display();
           w1.display();

           // the batting average asked for
           System.out.printf("%s scored %d runs in %d matches.%n",
                   "Tamim Iqbal", b1.getTotalRuns(), 100);
           System.out.printf("Batting average = %.2f runs per match%n", b1.average());

           // polymorphism through the abstract base type
           System.out.println("\n========= THROUGH THE BASE REFERENCE =========");
           Player[] squad = { b1, b2, w1 };
           for (Player p : squad) {
               System.out.printf("%-18s %-10s %.2f%n",
                       p.name, p.playerType(), p.average());
           }
       }
   }
   ```

   Output:
   ```
   ========= PLAYER STATISTICS =========
   Name    : Tamim Iqbal
   Type    : Batsman
   Matches : 100
   Average : 35.00
   --------------------------------
   Name    : Mushfiqur Rahim
   Type    : Batsman
   Matches : 120
   Average : 30.00
   --------------------------------
   Name    : Shakib Al Hasan
   Type    : Bowler
   Matches : 110
   Average : 28.00
   --------------------------------
   Tamim Iqbal scored 3500 runs in 100 matches.
   Batting average = 35.00 runs per match

   ========= THROUGH THE BASE REFERENCE =========
   Tamim Iqbal        Batsman    35.00
   Mushfiqur Rahim    Batsman    30.00
   Shakib Al Hasan    Bowler     28.00
   ```

   Points demonstrated:
   - An abstract class with an abstract method: Player declares average() without a body, so every concrete subclass is compelled to define it.
   - A constructor in an abstract class: it cannot be used to create a Player directly, but it is called through super() to initialise the inherited fields.
   - A concrete method in an abstract class: playerType() has a body and is overridden by each subclass.
   - The same abstract method carries a different meaning in each subclass: for a batsman it is runs per match, and for a bowler it is runs conceded per wicket. This is the essence of abstraction.
   - Run-time polymorphism through an array of the base type.
   - A guard against division by zero in both implementations.

   Note on the cricketing definition: the official batting average is total runs divided by the number of dismissals, not by the number of matches. The program above uses runs per match, as the question asks; if the number of not-outs were available, average() would be written as totalRuns / (innings - notOuts).
